# Para-Cuando?-API  
### **Para Cuando tendrá una api para interactuar con el front y servicios futuros. Esta api esatara contruida con Node usando Express, Sequelize (ORM) y  Passport JWT.**
-----
Objetivo del la API es que podamos autenticarnos para publicar ciertas encuestas y votarlas. Específicamente hablamos de publicar eventos, conciertos y torneos en una fecha determinada haciendo que la comunidad decida dar su apoyo o no para que se realice. Tenemos que idear la manera en que las personas puedan acceder a una aplicación para que puedan compartir estas publicaciones en donde puedan votar a favor de estas o en contra.   

## Steps

**Note**  
`Antes de iniciar recomendamos contar con algunas extenciones para su editor de codigo favorito en nuestro caso Visual Studio Code, instala Elist y Error Lens.`   

## PART I: Download & Build on local | From github

### Clone the repository, install node packages  and verify routes locally

# Pre-requisites
- Install [Node.js](https://nodejs.org/en/) version 18.13.0
- npm version 9.3.0

# Getting started
- Clone the repository
```
git clone  https://github.com/pakorro2/BK-para-cuando-G4
```
- Install dependencies
```
cd BK-para-cuando-G4
npm install
```
- Build and run the project
```
npm run dev
```
  Navigate to `http://localhost:9000`

- API Document endpoints

   swagger-ui  Endpoint : http://localhost:8001/docs 

Open your local browser and verify the BK-para-cuando-G4 API is working by accessing:     
`http://localhost:9000/ --> status	"Up"


## Project Structure
The folder structure of this app is explained below:

| Name | Description |
| ------------------------ | --------------------------------------------------------------------------------------------- |
| **controllers**          | Controllers define functions to serve various express routes. 
| **database**             | Contains configuration, migrations, models and seeders.  |
| **database**/config   | Models define schemas that will be used in storing and retrieving data from Application database  |
| **database**/migration  | Models define schemas that will be used in storing and retrieving data from Application database  |
| **database**/models    | Models define schemas that will be used in storing and retrieving data from Application database  |
| **database**/seeders      | Models define schemas that will be used in storing and retrieving data from Application database  |
| **libs**                 | Common libraries to be used across your app.                               |
| **middlewares**  | Express middlewares which process the incoming requests before handling them down to the routes                               |
| **node_modules**         | Contains all  npm dependencies                                                            |
| **routes**           | Contain all express routes, separated by module/area of application                       
| **services**           | Contain all express routes, separated by module/area of application                       
| **utils**      | Prometheus metrics |
| **configuration**        | Application configuration including environment-specific configs 
| **src/middlewares**      | Express middlewares which process the incoming requests before handling them down to the routes
| index.js         | Entry point to express app                                                               |
| .eslintrc.jsn              | Config settings for TSLint code style checking                                              |
| .gitignore              | Config settings for TSLint code style checking                                              |
| .sequelizerc             | Config settings for TSLint code style checking                                            |
| package.json             | Contains npm dependencies as well as [build scripts](#what-if-a-library-isnt-on-definitelytyped)   | tsconfig.json            | Config settings for compiling source code only written in TypeScript    
| .README.md              | Config settings for TSLint code style checking                                              |    


### Config .env

Open the .env.example (rename file to .env for production)file in your text editor and enter the following information from the Feature section you just configured.

```bash
# Port server
PORT:

# PostgreSQL credentials and information (you will come back and fill up this information after we set up our database)
A database URI is made up of these parts:
db:engine:[//[user[:password]@][host][:port]/][dbname]
------
example local db url: postgresql://postgres:root@localhost:5432/para_cuando
# Place in the variable according to the use case
DATABASE_URI_DEV:
DATABASE_URI_TEST:
DATABASE_URI_PROD:
```

### Config: Creating Database

If you already  have postgress installed in your local environment you can skip these steps, if not follow along to install pg and create a table in your database. 

- If you are using Windows, download a [Windows installer of PostgreSQL](https://www.postgresql.org/download/windows/) or you can use this [PostgreSQL Portable Copy](https://github.com/garethflowers/postgresql-portable)
- If you are using a Mac and you have Homebrew installed on your computer, open up the terminal and install postgresql with brew:

```bash
brew install postgresql
```

After the installation is complete, we’ll want to get postgresql up and running, which we can do with services start

```bash 
brew services start postgresql
```

With PostgreSQL now installed, we will connect to the default postgres database running 

```bash
psql postgres
```

We are now inside psql in the postgres database, you will see the prompt ends with an # to denote that we are logged in as the superuser, or root (postgres=#)

Commands within psql start with a backlash \. To test this, we can check what database, user and por we have connected to using the \conninfo command

```bash
postgres=# \conninfo
```
