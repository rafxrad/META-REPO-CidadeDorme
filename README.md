# Deploy do Jogo Cidade Dorme

## Sobre o Jogo

Cidade Dorme é um jogo baseado no clássico jogo de tabuleiro "Máfia" ou "Cidade Dorme", no qual os jogadores assumem papéis específicos e precisam interagir estrategicamente para alcançar seus objetivos. O jogo envolve fases de noite e dia, onde durante a noite certos jogadores realizam ações secretas, e durante o dia todos discutem e votam em suspeitos.

## Pré-requisitos

Antes de iniciar o deploy, é necessário garantir que os seguintes requisitos estejam atendidos:

- **Docker** instalado na máquina
- **Docker Compose** instalado
- Acesso à internet para clonar e construir os contêineres
- **Docker daemon** em execução
- 
## Estrutura do Docker Compose

O arquivo `docker-compose.yml` define dois serviços principais:

### 1. Frontend
- O código-fonte do frontend está no repositório [`cidade_dorme_front`](https://github.com/rafxrad/cidade_dorme_front.git).
- Usa a porta `5073` mapeada para a porta `80` do contêiner.
- Depende do serviço backend.
- Está conectado à rede `cidade_dorme_network`.

### 2. Backend
- O código-fonte do backend está no repositório [`cidade_dorme_back`](https://github.com/rafxrad/cidade_dorme_back.git).
- Define a variável de ambiente `ASPNETCORE_URLS=http://+:8080`.
- Usa a porta `8080` exposta para o host.
- Está conectado à rede `cidade_dorme_network`.

## Passos para Deploy

### 1. Clonar o repositório
Clone o repositório:
```sh
git clone https://github.com/rafxrad/META-REPO-CidadeDorme/
```
Mude para onde se encontra o arquivo docker compose do jogo:
```sh
cd META-REPO-CidadeDorme
```

### 2. Executar o Docker Compose
No diretório onde o arquivo `docker-compose.yml` está salvo, execute:
```sh
docker-compose up --build
```
Isso iniciará os serviços frontend e backend em contêineres.

### 3. Acessar a Aplicação
Após o deploy, acesse o frontend no navegador:
```
http://localhost:5073
```
O backend estará disponível na porta 8080:
```
http://localhost:8080
```
Você pode acessar o swagger da documentação da api:
```
http://localhost:8080/swagger/index.html
```

## Parar e Remover os Contêineres
Para parar e remover os contêineres criados:
```sh
docker-compose down
```

## Conclusão
Com esses passos, o jogo "Cidade Dorme" estará rodando localmente em contêineres Docker. Agora é possível interagir com a aplicação, testar funcionalidades e expandir o projeto conforme necessário.

