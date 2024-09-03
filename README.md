# User Management Service

## Descrição

O **User Management Service** é um serviço de gerenciamento de usuários que integra autenticação biométrica (FaceID) em dispositivos móveis com o AWS Cognito para autenticação segura e gerenciamento de usuários. O serviço suporta operações como registro, login, upload de avatares para o S3 e validação de tokens JWT.

# Funcionalidades

### 1. Autenticação Biométrica (FaceID)

- **Descrição:** Integração com o FaceID para autenticação segura no lado do cliente.
- **Benefícios:** Proporciona uma camada adicional de segurança e conveniência para os usuários ao realizar o login.

### 2. Gerenciamento de Usuários

- **Descrição:** Funcionalidade completa para cadastro, login e gerenciamento de informações dos usuários.
- **Inclui:**
  - Registro de novos usuários.
  - Login de usuários existentes.
  - Edição e gerenciamento dos dados do perfil do usuário.

### 3. Upload de Avatares

- **Descrição:** Permite o upload de fotos de perfil (avatares) para o Amazon S3.
- **Armazenamento:** As fotos são armazenadas de forma segura no S3, permitindo fácil acesso e recuperação.

### 4. Validação de Tokens JWT

- **Descrição:** Validação de tokens JWT gerados pelo AWS Cognito para acessar recursos protegidos.
- **Segurança:** Garante que apenas usuários autenticados possam acessar certas funcionalidades e dados.

### 5. Persistência de Dados

- **Descrição:** Utilização do Sequelize como ORM com PostgreSQL para gerenciamento de dados.
- **Benefícios:**
  - Mapeamento de dados entre objetos em TypeScript e tabelas do banco de dados.
  - Facilita a manipulação de dados de forma segura e eficiente.

# Tecnologias Utilizadas

### 1. Node.js

- **Descrição:** Plataforma de execução do JavaScript no lado do servidor.
- **Utilização:** Base para o desenvolvimento do servidor, permitindo a construção de APIs e serviços escaláveis.

### 2. Express

- **Descrição:** Framework web rápido e minimalista para Node.js.
- **Utilização:** Estrutura o servidor e gerencia rotas, middlewares e APIs RESTful.

### 3. TypeScript

- **Descrição:** Superconjunto do JavaScript que adiciona tipagem estática.
- **Utilização:** Proporciona maior segurança no desenvolvimento, facilitando a manutenção e escalabilidade do código.

### 4. AWS Cognito

- **Descrição:** Serviço de autenticação e gerenciamento de usuários.
- **Utilização:** Gerencia a autenticação dos usuários, incluindo a geração e validação de tokens JWT.

### 5. AWS S3

- **Descrição:** Serviço de armazenamento de objetos da AWS.
- **Utilização:** Armazena avatares de usuários com alta durabilidade e disponibilidade.

### 6. Sequelize

- **Descrição:** ORM (Object-Relational Mapper) para Node.js.
- **Utilização:** Facilita o mapeamento de objetos em TypeScript para tabelas do PostgreSQL, simplificando operações de banco de dados.

### 7. Multer

- **Descrição:** Middleware para gerenciamento de uploads de arquivos em Node.js.
- **Utilização:** Gerencia o processo de upload de arquivos, como avatares de usuários, garantindo segurança e eficiência.

### 8. Docker

- **Descrição:** Plataforma para criar, implantar e executar aplicativos em containers.
- **Utilização:** Permite a criação de ambientes consistentes para desenvolvimento, testes e produção.

### 9. Jest

- **Descrição:** Framework de testes para JavaScript e TypeScript.
- **Utilização:** Realiza testes unitários e de integração para garantir a qualidade e o funcionamento correto do código.

## Estrutura do Projeto

```plaintext
user-management-service/
├── src/
│   ├── application/
│   │   └── services/
│   │       └── UserService.ts              # Lógica de aplicação para gerenciamento de usuários
│   ├── domain/
│   │   ├── entities/
│   │   │   └── User.ts                     # Entidade de usuário com lógica básica
│   │   ├── errors/
│   │   │   └── DomainError.ts              # Classe de erro personalizada para domínio
│   │   ├── ports/
│   │   │   └── IUserRepository.ts          # Interface para repositório de usuários
│   │   └── validators/
│   │       └── UserValidator.ts            # Validador para a entidade User
│   ├── infrastructure/
│   │   ├── adapters/
│   │   │   ├── db/
│   │   │   │   ├── models/
│   │   │   │   │   └── UserModel.ts        # Modelo Sequelize para a entidade User
│   │   │   │   └── PostgresUserRepository.ts # Implementação do repositório usando Sequelize e PostgreSQL
│   │   │   └── cognito/
│   │   │       └── CognitoService.ts       # Serviço de integração com AWS Cognito para autenticação
│   │   ├── config/
│   │   │   ├── sequelize.ts                # Configuração do Sequelize
│   │   │   ├── s3.ts                       # Configuração do S3 para uploads de arquivos
│   │   │   └── multer.ts                   # Configuração do Multer para uploads de arquivos ao S3
│   ├── interfaces/
│   │   ├── controllers/
│   │   │   └── UserController.ts           # Controlador para lidar com requisições de usuário
│   │   ├── dtos/
│   │   │   ├── UserInputDTO.ts             # DTO para entrada de dados de usuário
│   │   │   └── UserOutputDTO.ts            # DTO para saída de dados de usuário
│   │   ├── routes/
│   │   │   ├── userRoutes.ts               # Definição das rotas de usuário
│   │   │   └── authRoutes.ts               # Rota para validação de tokens JWT
│   └── app.ts                              # Configuração principal do app Express
├── tests/
│   └── UserService.test.ts                 # Testes de unidade para o UserService
├── docker-compose.yml                      # Arquivo Docker Compose para rodar a aplicação e o banco de dados
├── Dockerfile                              # Dockerfile para construir a imagem da aplicação
├── jest.config.js                          # Configuração do Jest para testes
├── .env.example                            # Exemplo de variáveis de ambiente necessárias
├── .gitignore                              # Arquivos e pastas ignoradas pelo Git
├── package.json                            # Configurações do npm/yarn e dependências do projeto
├── tsconfig.json                           # Configuração do TypeScript
└── server.ts                               # Inicia o servidor Express
```
