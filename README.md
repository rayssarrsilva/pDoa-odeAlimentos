# 🍲 Sistema de Conexão entre Doadores e Instituições

Este é um sistema web desenvolvido em PHP para conectar doadores de alimentos a instituições de caridade. Os doadores podem registrar doações, enquanto as instituições visualizam e acompanham as doações recebidas.

## 📌 Funcionalidades

- Cadastro de Doadores
- Cadastro de Instituições
- Registro de Doações
- Relacionamento entre doadores e instituições
- Organização do código seguindo o padrão MVC
- Conexão com banco de dados via Singleton (PDO)

## 🛠️ Tecnologias Utilizadas

- PHP 7+
- MySQL (via phpMyAdmin)
- XAMPP
- HTML5
- Padrão MVC com DAO, Service e Template

## 🧱 Estrutura do Projeto


- `controller/`: Lógica de controle de ações do usuário.
- `dao/`: Acesso ao banco de dados.
- `service/`: Regras de negócio.
- `template/`: Gerenciamento das views (interface).
- `generic/`: Conexão com o banco e classes auxiliares.
- `public/`: Formulários e páginas acessíveis.

## 🗃️ Estrutura do Banco de Dados

Execute o seguinte SQL no phpMyAdmin:

```sql
CREATE TABLE doadores ( 
    id INT AUTO_INCREMENT PRIMARY KEY, 
    nome VARCHAR(100) NOT NULL, 
    email VARCHAR(100) UNIQUE NOT NULL 
); 

CREATE TABLE instituicoes ( 
    id INT AUTO_INCREMENT PRIMARY KEY, 
    nome VARCHAR(150) NOT NULL, 
    endereco VARCHAR(255) NOT NULL 
); 

CREATE TABLE doacoes ( 
    id INT AUTO_INCREMENT PRIMARY KEY, 
    doador_id INT, 
    instituicao_id INT, 
    descricao TEXT NOT NULL, 
    data_doacao DATE NOT NULL, 
    FOREIGN KEY (doador_id) REFERENCES doadores(id), 
    FOREIGN KEY (instituicao_id) REFERENCES instituicoes(id) 
);
