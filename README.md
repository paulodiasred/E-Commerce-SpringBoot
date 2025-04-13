## Projeto
Projeto base para estudo de Spring Boot, MVC e Hibernate.

## Implementações recentes
- Configuração do Hibernate adicionada (o banco de dados e as tabelas são criados automaticamente ao executar o projeto)
- Classes de serviço fornecem serviços reutilizáveis em todo o projeto.
- Classes DAO interagem com o banco de dados.
- Correções de bugs (imagem do produto, segurança, etc.).
- Suporte tanto no Eclipse quanto no IntelliJ IDE.
- Redesign geral de todo o código para melhorar a reutilização.
- Aviso: atualmente trabalhando neste branch, portanto, pode haver alguns bugs relacionados aos endpoints e lógica do carrinho.
  
## Inicio Rapido

1. Clone o repositorio
2. Abra o projeto na sua IDE: IntelliJ IDEA (recomendado) ou Eclipse.
    * Se estiver usando o IntelliJ IDEA, certifique-se de que a IDE abra o projeto como Maven e reconheça-o como um projeto Spring Boot. Além disso, você deve alterar o diretório de trabalho do projeto para que as visualizações (as páginas da web reais a serem exibidas) sejam encontradas pelo Spring Boot (consulte Web Directories no IntelliJ IDEA).
3. Certifique-se de estar no diretório `JtProject`.
4. Configure a conexão com o banco de dados no arquivo `application.properties` (verifique a seção Banco de Dados abaixo para mais informações).
5. Execute o projeto (executando o método `main` em `JtSpringProjectApplication.java`).
6. Abra http://localhost:8080/ no seu navegador!
   * Se você executou o script `basedata.sql` no banco de dados, pode fazer login com as seguintes credenciais como administrador; caso contrário, você terá que criar manualmente um usuário administrador no banco de dados:
     * Username: `admin`
     * Password: `123`
   * Faça login como um usuário normal:
     * Username: `paulo`
     * Password: `765`

### Banco de Dados

MySQL ou MariaDB podem ser usados como banco de dados para este projeto. A conexão com o banco de dados pode ser configurada no arquivo `src/main/resources/application.properties`, com os valores apropriados para as seguintes propriedades:

**(É melhor usar outro nome de usuário que não seja `root` e garantir que o usuário tenha as permissões correspondentes para o banco de dados.)**

```propriedades
    db.url=jdbc:mysql://[endereço IP do banco de dados]:[porta do banco de dados]/ecommjava?createDatabaseIfNotExist=true
    db.username=[username]
    db.password=[password, se tiver]
```

Se você encontrar o erro `java.lang.IllegalArgumentException: Could not resolve placeholder 'db.driver' in value "${db.driver}"`, talvez deva alterar sua versão do `mysql-connector-java` no arquivo `pom.xml` de acordo com a versão do seu MySQL. Não se esqueça de recarregar seu projeto Maven.

Depois disso, você deve criar alguns dados base no banco de dados. Você pode fazer isso executando o script `basedata.sql` no banco de dados. Consulte o Google para saber como fazer isso, pois depende da ferramenta que você está usando para acessar o referido banco de dados.

### Diretorios Web

As views estão localizadas em `src/main/webapp/views`, mas, por algum motivo, o Spring Boot não reconhece esse diretório. Para resolver isso, você deve alterar o diretório de trabalho do projeto na sua IDE. Se estiver usando o IntelliJ IDEA, siga estas etapas:

1. Clique no botão "Edit Configurations..." no canto superior direito da IDE.
2. Clique na configuração `JtSpringProjectApplication`.
3. Altere a opção "Working directory" (se não estiver presente, clique em "Modify Options" e selecione na lista) para o macro `$MODULE_WORKING_DIR$`.
4. Clique em "Apply" e "OK".


Quando você executar o projeto, as visualizações devem ser encontradas pelo Spring Boot e você deverá ver uma página de login em http://localhost:8080/ (se não estiver logado anteriormente)!

# Fluxo de Trabalho
- ![image](https://github.com/paulodiasred/E-Commerce-SpringBoot/blob/main/JtProject/src/main/resources/assets/image1.png)
### Controller
- Controla o endpoint e também envia dados para a visualização (usamos o método ModelAndView).
```
public String adminlogin() {
		
		return "adminlogin";
}
```
- Sempre que a URL `/login` é acessada, o arquivo `adminlogin.jsp` em `src->main->webapp` é executado.
### Models
- Representam dados como entidades e o relacionamento entre eles.

### View
- Recebe dados do controlador e exibe com o frontend.

## Endpoints
- http://localhost:8080/
- http://localhost:8080/register
- http://localhost:8080/admin/products
- http://localhost:8080/admin/customers
- http://localhost:8080/admin/categories
- http://localhost:8080/admin/Dashboard


## Spring Boot

Para qualquer informação sobre o Spring Boot, aqui estão alguns links úteis!

### Documentação de Referência
Para mais informações, considere as seguintes seções:

* [Documentação oficial do Apache Maven](https://maven.apache.org/guides/index.html)
* [Guia de Referência do Plugin Maven do Spring Boot](https://docs.spring.io/spring-boot/docs/2.6.4/maven-plugin/reference/html/)
* [Criar uma imagem OCI](https://docs.spring.io/spring-boot/docs/2.6.4/maven-plugin/reference/html/#build-image)
* [Spring Web](https://docs.spring.io/spring-boot/docs/2.6.4/reference/htmlsingle/#boot-features-developing-web-applications)


## Visualização

![image](https://github.com/paulodiasred/E-Commerce-SpringBoot/blob/main/JtProject/src/main/resources/assets/image2.jpg)
![image](https://github.com/paulodiasred/E-Commerce-SpringBoot/blob/main/JtProject/src/main/resources/assets/image3.jpg)
![image](https://github.com/paulodiasred/E-Commerce-SpringBoot/blob/main/JtProject/src/main/resources/assets/image4.jpg)

