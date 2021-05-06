# Curso TDD con RSpec
## Antes de empezar
Requerimos tener en nuestro enviroment instalado lo siguiente
* Docker
* Docker compose
## Clonar repositorio
El proyecto se compone de dos repositorios, el repositorio principal donde tenemos nuestro archivo docker compose y configuramos nuestras variables de ambiernte. El segundo repositorio es el proyecto de rails con nuestro código.

`git clone  --recurse-submodules  https://github.com/vurokrazia/curso_tdd_con_rspec`

## Iniciando el setup
Copiar nuestros archivos de la carpeta enviroments removiendo la palabra example y escribiendo el valor de nuestras credenciales o dejar las credenciales de ejemplo.
```
  cd enviroments/
  cp .example.env.postgresql .env.postgresql 
  cp .example.env.store_api .env.store_api
```
Creamos nuestra imagen del proyecto store api
```
  docker-compose build
```
Iniciamos nuestros servicios
```
  docker-compose up -d
```
Creamos la base de datos del proyecto
```
  docker-compose  exec store_api rails db:create
```
Ejecutamos las migraciones del proyecto
```
  docker-compose  exec store_api rails db:migrate
```
## Services
* Store api
  * Nombre del servicio: store_api
  * Port: 3000
  * Dependencias: db_store
* Postgres
  * Nombre del servicio: db_store 
  * Port: 5432