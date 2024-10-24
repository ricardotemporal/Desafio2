# Desafio 2 - Dockerização e CI/CD com Deploy Automático no Vercel

## Visão Geral

Este projeto consiste na dockerização de uma aplicação e na configuração de um pipeline de CI/CD usando **GitHub Actions** para realizar o deploy automático no **Vercel**. O objetivo deste desafio é integrar todo o fluxo de desenvolvimento, desde o código-fonte até o deploy da aplicação em produção, de forma automatizada.

## Estrutura do Projeto

- **Aplicação Web**: A aplicação principal, que será dockerizada e configurada para deploy automático.
- **Docker**: Utilizado para criar um ambiente de desenvolvimento e produção consistente.
- **GitHub Actions**: Responsável por orquestrar o pipeline de CI/CD, incluindo a execução dos testes e o deploy no Vercel.
- **Vercel**: Plataforma de hospedagem na qual a aplicação será automaticamente implantada após cada push para o repositório.

## Requisitos

Antes de começar, certifique-se de que você tem o seguinte configurado:

- **Docker** e **Docker Compose** instalados no seu sistema.
- Uma conta no **GitHub**.
- Uma conta no **Vercel**, com o projeto configurado para receber deploys automáticos.

## Passos para rodar o projeto localmente

### 1. Clone o repositório

Execute o seguinte comando no terminal para clonar o repositório:

- git clone <URL_DO_REPOSITORIO>

### 2. Acesse o diretório do projeto

Navegue até o diretório do projeto:

- cd nome-do-diretorio-clonado

### 3. Inicie os containers com Docker Compose

Para iniciar os containers localmente, execute o seguinte comando:

- docker-compose up --build

Isso irá construir as imagens Docker e iniciar os containers da aplicação.

### 4. Acesse a aplicação

A aplicação estará disponível no navegador no seguinte endereço:
  
- http://localhost:4173

### 5. Parar os containers

Após terminar de usar a aplicação, você pode parar os containers com o comando:

- docker-compose down

## Configuração de CI/CD com GitHub Actions

Este projeto utiliza GitHub Actions para automatizar o processo de CI/CD e fazer deploy automático no Vercel. O workflow já está configurado no arquivo .github/workflows/deploy.yml.

### 1. Configuração do GitHub Secrets

Para que o GitHub Actions possa fazer o deploy no Vercel, você precisa configurar os seguintes secrets no seu repositório GitHub:

- VERCEL_TOKEN: O token de autenticação da sua conta Vercel.
- VERCEL_PROJECT_ID: O ID do projeto no Vercel.
- VERCEL_ORG_ID: O ID da sua organização no Vercel.

### 2. Como funciona o workflow de CI/CD

- Trigger: O pipeline é disparado automaticamente sempre que um commit é feito na branch main.
- Build: O GitHub Actions faz o build da aplicação para garantir que ela está funcionando corretamente.
- Testes: Caso existam testes, eles serão executados durante o pipeline.
- Deploy: Se o build e os testes passarem com sucesso, o deploy será feito automaticamente no Vercel.

## Deploy no Vercel

### 1. Vercel CLI

Se você precisar realizar o deploy manualmente, pode utilizar a Vercel CLI:

Instale a CLI:

- npm install -g vercel

Autentique-se:

- vercel login
  
Realize o deploy:

- vercel --prod
  
### 2. Acessando a aplicação no Vercel

Após o deploy automático ser realizado, a aplicação ficará disponível em um domínio gerado pelo Vercel. Verifique o painel do Vercel para o link final.

## Considerações finais

Certifique-se de que o arquivo .github/workflows/deploy.yml está corretamente configurado e que os secrets estão definidos no GitHub.
O deploy será automático após cada commit na branch main, garantindo que a aplicação esteja sempre atualizada no Vercel.
Verifique os logs do pipeline de CI/CD no GitHub Actions e no Vercel para diagnosticar possíveis erros.
