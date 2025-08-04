# 🚀 Challenge Forum Hub

O Challenge Forum Hub é uma **API REST** desenvolvida como parte de um desafio do programa **ONE da Oracle**. Ele simula um fórum online, permitindo que usuários gerenciem **tópicos de discussão** de forma segura e eficiente.

---

## 🏆 Conclusão do Desafio

Badge recebida pela conclusão do desafio.

<div align="center">
    <img width="200" height="200" alt="Badge-Spring" src="https://github.com/user-attachments/assets/0583127d-c4e6-4f6b-8ddd-088e1738ed5a"]/>
</div>

---

## 🎯 Objetivo do Projeto

O principal objetivo do Challenge Forum Hub é prover uma API para o gerenciamento de tópicos de fórum, contendo funcionalidades essenciais de um CRUD (Create, Read, Update, Delete) e um sistema de autenticação e autorização.

---

## ✨ Funcionalidades

A API oferece os seguintes recursos para o gerenciamento de tópicos:

* **Cadastro de Tópicos:** Permite a criação de novos tópicos de discussão com campos como **título**, **mensagem**, **autor** e **curso**. (Requer autenticação)
* **Listagem de Tópicos:** Consulta e exibe todos os tópicos existentes no fórum. (Acesso **liberado**, sem necessidade de autenticação)
* **Detalhes do Tópico:** Permite buscar um tópico específico por ID. (Acesso **liberado**, sem necessidade de autenticação)
* **Atualização de Tópicos:** Permite a modificação de tópicos existentes. (Requer autenticação)
* **Exclusão de Tópicos:** Permite a remoção de tópicos do fórum. (Requer autenticação)

### Autenticação e Autorização

A segurança da API é garantida através de:

* **Autenticação JWT (JSON Web Token):** Os usuários devem enviar credenciais válidas para o endpoint `/login`.
* **Login de Usuário:** Ao enviar um JSON com informações de login válidas, a API retorna um token JWT.
* **Autorização por Token:** Para operações de cadastro, atualização e exclusão, o token JWT deve ser enviado no cabeçalho das requisições, garantindo que apenas usuários autenticados e autorizados possam realizar essas ações. As requisições de listagem (GET) são abertas ao público.

---

## 💻 Tecnologias Utilizadas

* **Linguagem de Programação:** Java 21
* **Framework:** Spring Boot 3.5.3
* **Gerenciador de Dependências:** Gradle
* **Banco de Dados:** MySQL
* **Gerenciamento de Migrações de Banco de Dados:** Flyway
* **Segurança:** Spring Security e JWT (JSON Web Tokens)
* **Desenvolvimento de API:** Spring Web
* **Validação de Dados:** Bean Validation (para garantir a integridade e conformidade dos dados de entrada)

---

## 🚀 Como Executar o Projeto Localmente

Para rodar o Challenge Forum Hub em sua máquina, siga os passos abaixo:

### Pré-requisitos

Certifique-se de ter as seguintes ferramentas instaladas e configuradas em seu ambiente:

* **Java Development Kit (JDK) 21**
* **Gradle** (versão compatível com Spring Boot 3.x)
* **Servidor MySQL** (local ou acessível pela rede)
* **Cliente MySQL** (opcional, mas recomendado para gerenciamento do banco de dados, ex: MySQL Workbench, DBeaver)

### 1. Configuração do Banco de Dados

1.  Crie um novo banco de dados no seu servidor MySQL para o projeto (ex: `forum_hub_db`).
2.  Certifique-se de que o usuário do MySQL que você irá usar tenha as permissões necessárias para criar e manipular tabelas neste banco.

### 2. Configuração das Variáveis de Ambiente

As credenciais do banco de dados e a chave secreta do JWT são carregadas via variáveis de ambiente para maior segurança. Você deve configurá-las no seu sistema operacional antes de iniciar a aplicação.

* **Para Linux/macOS (Terminal):**
    Abra seu terminal e execute os seguintes comandos, substituindo os valores entre `[]` pelos seus dados reais:

    ```bash
    export DB_HOST=[SEU_HOST_MYSQL]  # Ex: localhost
    export DB_NAME=[SEU_NOME_DO_BANCO] # Ex: forum_hub_db
    export DB_USER=[SEU_USUARIO_MYSQL]
    export DB_PASSWORD=[SUA_SENHA_MYSQL]
    export JWT_SECRET=[SUA_SENHA_SECRETA_JWT] # Uma string complexa e segura para o JWT
    ```
    *Para tornar essas variáveis persistentes, adicione-as ao seu `.bashrc`, `.zshrc` ou arquivo de perfil correspondente.*

* **Para Windows (Prompt de Comando ou PowerShell):**
    Abra o Prompt de Comando ou PowerShell e execute:

    ```cmd
    set DB_HOST=[SEU_HOST_MYSQL]
    set DB_NAME=[SEU_NOME_DO_BANCO]
    set DB_USER=[SEU_USUARIO_MYSQL]
    set DB_PASSWORD=[SUA_SENHA_MYSQL]
    set JWT_SECRET=[SUA_SENHA_SECRETA_JWT]
    ```
    *Para configurar permanentemente no Windows, use as "Variáveis de ambiente do sistema".*

### 3. Build e Execução da Aplicação

1.  **Clone o Repositório:**
    ```bash
    git clone git@github.com:roberto-rodriguess/ChallengeForumHub.git
    cd ChallengeForumHub
    ```
2.  **Compile o Projeto:**
    Abra o terminal na raiz do projeto (onde o arquivo `build.gradle` está localizado) e execute:
    ```bash
    ./gradlew clean build
    ```
    *Este comando irá baixar as dependências, compilar o código e rodar os testes.*

3.  **Execute a Aplicação:**
    Após o build ser concluído com sucesso, execute a aplicação com o Gradle:
    ```bash
    ./gradlew bootRun
    ```
    *A API será iniciada e estará acessível em `http://localhost:8080` (porta padrão do Spring Boot), a menos que configurado de outra forma.*

### 4. Migrações do Banco de Dados (Flyway)

Ao iniciar a aplicação pela primeira vez, o **Flyway** (integrado ao Spring Boot) irá automaticamente executar as migrações SQL presentes na pasta `src/main/resources/db/migration` para criar o esquema inicial do banco de dados (tabelas de usuários, tópicos, etc.).

---

## 🛣️ Endpoints

| Método HTTP | Endpoint       | Descrição                        | Autenticação |
| :---------- | :------------- | :------------------------------- | :----------- |
| `POST`      | `/login`       | Autentica o usuário e retorna JWT | Pública      |
| `POST`      | `/topicos`     | Cadastra um novo tópico          | JWT Exigido  |
| `GET`       | `/topicos`     | Lista todos os tópicos           | Pública      |
| `GET`       | `/topicos/{id}`| Detalha um tópico por ID         | Pública      |
| `PUT`       | `/topicos/{id}`| Atualiza um tópico existente     | JWT Exigido  |
| `DELETE`    | `/topicos/{id}`| Exclui um tópico por ID          | JWT Exigido  |

---

## 📈 Próximos Passos e Melhorias (Planejado)

* **Documentação com Swagger:** Implementar o Swagger para gerar documentação interativa da API.
* **Testes Automatizados:** Desenvolver testes de unidade para garantir o funcionamento correto da aplicação.

---

## 🤝 Contribuição

Contribuições são bem-vindas! Se você tiver sugestões ou encontrar problemas, sinta-se à vontade para abrir uma issue ou enviar um pull request.
