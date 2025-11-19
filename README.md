const fs = require('fs');

// Caminho do arquivo
const filePath = './exemplo.txt';

fs.writeFile(filePath, 'Conteúdo inicial do arquivo.', (err) => {
  if (err) {
    return console.error('Erro ao criar o arquivo:', err);
  }
  console.log('Arquivo criado e conteúdo escrito com sucesso!');

  fs.readFile(filePath, 'utf8', (err, data) => {
    if (err) {
      return console.error('Erro ao ler o arquivo:', err);
    }
    console.log('Conteúdo do arquivo:', data);

    fs.appendFile(filePath, '\nConteúdo adicional.', (err) => {
      if (err) {
        return console.error('Erro ao atualizar o arquivo:', err);
      }
      console.log('Conteúdo adicional escrito com sucesso!');

      fs.readFile(filePath, 'utf8', (err, data) => {
        if (err) {
          return console.error('Erro ao ler o arquivo atualizado:', err);
        }
        console.log('Conteúdo atualizado do arquivo:', data);

        fs.unlink(filePath, (err) => {
          if (err) {
            return console.error('Erro ao excluir o arquivo:', err);
          }
          console.log('Arquivo excluído com sucesso!');
        });
      });
    });
  });
});
