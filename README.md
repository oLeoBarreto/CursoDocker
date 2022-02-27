# Curso de Docker 

- o docker fui criado para facilitar o processo de desenvolvimento, para deixar os ambientes de producao e homologacao mais padroxinados utilizando containers.
- um arquivo docker tem que ser criado da seguinte forma `Dockerfile`, sem extencao e com a primera letra maiusculo e file em minuscula.

## Principais comandos docker

- Para rodar um container basta `docker container run container-name`.
- Para parar a execucao de um container `docker container stop container-name ou container-id`.
- `docker container run ex-build-arg bash -c "echo $S3_BUCKET"` onde o `-c` serve para passar um comando que no caso `"echo $S3_BUCKET"` e um echo da variavel de ambiente.
- `docker image inspect --format="{{index .Config.Labels \"maintainer\"}}" ex-build-arg` voce pode inpecionar algo especifico da imagem ou ela por inteira, nesse caso iremos inspecionar apenas o `maintainer` do container.

## Principais flags

- Serve para listar as imagens, containers ou volumes `ls`
- Definir a porta que o container ira rodar `-p 8080:80`
- Startar o container de forma interativa `-it`
- Para mapear o volume `-v`
- Na execusao de um container voce pode especificar o nome dele usando `--name` assim quando o container rodar nao tera um nome aleatorio
- `rm` serve para remover um container, imagem ou volume
- `-d` do `docker cotainer run` indica que o container sera executado em modo background/deamon    
- `--rm` diz que apos executar o container ja sera altomaticamente removido.
- Para passar um comando utiliza `-c`
- `--net` serve para configurar o tipo de rede, podendo ser: none, bridge ou host

## Comandos de build

- Para buildar uma imagem simples `docker image build -t ex-simple-build .` onde o `-t` serve para dar o nome a imagem.
- Buildar uma imagem com argumentos `docker image build --build-arg S3_BUCKET=myapp -t ex-build-arg .`, o `--build-arg` serve para definir um valor para a variavel de ambiente.

## Rede 

- Para listar as redes docker basta o comando `docker network ls`
- Com o comando `docker network create --driver DriverName NomeRede` cria uma nova rede, e o comando `--drive` serve para especificar o drive usando nessa rede
- `docker network connect bridge containerName` faz com que o container se connect a rede bridge, se conectando a mais de uma rede, sendo assim possivel se conectar com outros containers
- Assim como o `docker network disconnect containerName` disvincula aquela o container daquela rede 

## Docker Compose

Apos criar um arquivo de compose com seus devidos services e imagens:
- `docker-compose up -d` cria nosso compose e executa ele em modo deamon
- `docker-compose ps` lista os composes 
- `docker-compose down` faz com que o compose que esta rodando pare de rodar 
- usando a flag `--scale` podemos escalar mais de container para uma determidada instancia, EX: `docker-compose up -d --scale worker=3`, onde escala 3 workers

## Override Compose

Podemos criar um arquivo de compose `docker-compose.override.yml` que sobrescreve variaves do arquivo de compose original.

# Comandos de cmd Windowns

- `%cd%` serve para dizer a pasta raiz/pasta atual
- `cls` limpa o cdm do windows
- `mkdir` cria um novo diretorio/nova pasta
- `dir` lista os diretorios/pastas
- `cd` entrar ou sair de um diretorio