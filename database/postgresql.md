## Instalando PostgreSQL

### Download Postgresql 

Os exemplos neste tutotial foram criados baseados em:

- Sistema operacional: MacOS Ventura   
- Gerenciado de pacotes: Homebrew 4.2.11   
- Banco de dados: PostgreSQL 15

Instale o postgresql pelo Homebrew
```sh
brew install postgresql@15
```


### Exportar o caminho para o PostgreSQL no PATH
```sh
echo 'export PATH="/usr/local/opt/postgresql@15/bin:$PATH"' >> ~/.zshrc
```
Esta opção adiciona o caminho para os binários do PostgreSQL (/usr/local/opt/postgresql@15/bin) ao seu PATH. Isso permite que você execute facilmente comandos do PostgreSQL de qualquer lugar no terminal, sem precisar especificar o caminho completo para o executável.

### Definir variáveis de ambiente LDFLAGS e CPPFLAGS para o PostgreSQL

```sh
export LDFLAGS="-L/usr/local/opt/postgresql@15/lib"
export CPPFLAGS="-I/usr/local/opt/postgresql@15/include"
```
Estas opções são úteis para o compilador encontrar as bibliotecas e cabeçalhos necessários do PostgreSQL durante a compilação de outros programas que dependem dele. Isso é necessário caso você compile manualmente programas que usem o PostgreSQL.

### Iniciar o serviço do PostgreSQL
```sh
brew services start postgresql@15
```
Esta opção inicia o serviço do PostgreSQL. Isso é útil se você deseja que o PostgreSQL seja executado como um serviço em segundo plano no seu sistema. Após executar este comando, o PostgreSQL será iniciado automaticamente sempre que você ligar o computador.

### Conectar-se ao PostgreSQL
Você pode se conectar ao PostgreSQL usando o utilitário psql, que é um cliente PostgreSQL interativo. Para se conectar ao PostgreSQL, execute o seguinte comando no terminal:
```sql
psql -U postgres
```

Isso conectará você ao servidor PostgreSQL usando o usuário padrão postgres. Se você criou outros usuários durante a instalação ou configuração, pode substituir postgres pelo nome do usuário que deseja usar.

### Testar a conexão
Depois de se conectar ao PostgreSQL, você pode testar se está tudo funcionando corretamente executando alguns comandos simples. Por exemplo, você pode verificar a versão do PostgreSQL com o seguinte comando:

```sql
select version();
```

### Alguns comandos básicos

#### Criar um novo banco de dados (opcional)
Se você quiser testar a criação de um novo banco de dados, pode fazer isso com o seguinte comando:

```sql
create database testdb;
```
Isso criará um novo banco de dados chamado `testdb`.   
Para checar se o database foi criado utilize o comando para listar os databases existentes:
```sql
\l
```
#### Sair do cliente psql:
Depois de concluir seus testes, você pode sair do cliente psql digitando:
```sql
\q
```

