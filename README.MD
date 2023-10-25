# Blog Application

# To Deploy on AWS / ElasticBeanStalk

1. Change the port to 5000.
2. Change the "spring.profiles.active=dev" in application.properties to prod
3. In beanstalk connect to the same database.

Swagger Documentation: URL: http://localhost:9090/swagger-ui/index.html

![BlogApplication](https://github.com/omarbaig007212/SpringBoot-BlogApplication/assets/58821151/3fd2366e-7401-42b6-8a28-acf8bbc770ad)

This README provides an overview of a Blog Application built using Spring Boot that employs JSON Web Token (JWT) for authentication. The application allows users to create, manage, and interact with blog posts, comments, and categories. Below, you'll find details on the project structure, how to set up and run the application, and its API endpoints.

## Project Structure

The project structure is organized as follows:

- `src/main/java/com.blogApplication`: Contains the main Java application code.
- `src/main/resources`: Includes application properties, such as database configuration.
- `src/main/java/com.blogApplication.controllers`: Contains controllers to handle API endpoints.
- `src/main/java/com.blogApplication.entities`: Defines the entity classes.
- `src/main/java/com.blogApplication.repositories`: Manages the database operations using Spring Data JPA.
- `src/main/java/com.blogApplication.security`: Implements JWT-based security.
- `src/main/java/com.blogApplication.services`: Provides service classes and interfaces for business logic.
- `src/main/java/com.blogApplication.payloads`: Includes Data Transfer Objects (DTOs) for mapping request/response data.
- `src/main/java/com.blogApplication.exceptions`: Manages custom exceptions.

## Setup

### Prerequisites

Before running the Blog Application, make sure you have the following prerequisites:

- [Java 8](https://www.oracle.com/java/technologies/javase/javase-jdk8-downloads.html) or higher.
- [Maven](https://maven.apache.org/download.cgi) for dependency management.
- A database server (e.g., MySQL, PostgreSQL) and its configuration details (URL, username, password).

### Configuration

1. Clone this repository to your local machine.

2. Navigate to the `src/main/resources` directory and configure the database connection in the `application.properties` file. You should modify the following properties:

   ```properties
   spring.datasource.url=jdbc:your-database-url
   spring.datasource.username=your-username
   spring.datasource.password=your-password
   ```

   Additionally, you can customize other properties such as the server port or JWT secret in the same file.

3. Save your changes.


The application should now be running at `http://localhost:9090/api`.

## API Endpoints

The Blog Application provides the following API endpoints:

- **Authentication Endpoints:**

  - `POST /api/auth/login`: Authenticate a user and receive a JWT token.

- **Category Endpoints:**

  - `GET /api/categories`: Get a list of all categories.
  - `GET /api/categories/{category_id}`: Get a specific category by ID.

- **Post Endpoints:**

  - `GET /api/posts`: Get a list of all posts.
  - `GET /api/posts/{post_id}`: Get a specific post by ID.
  - `GET /api/categories/{category_id}/posts`: Get posts by a specific category.
  - `GET /api/users/{user_id}/posts`: Get posts by a specific user.
  - `POST /api/users/{user_id}/categories/{category_id}/posts`: Create a new post.
  - `PUT /api/posts/{post_id}`: Update a specific post.
  - `DELETE /api/posts/{post_id}`: Delete a specific post.

- **Comment Endpoints:**

  - `GET /api/posts/{post_id}/comments`: Get comments for a specific post.
  - `GET /api/comments/{comment_id}`: Get a specific comment by ID.
  - `POST /api/posts/{post_id}/comments`: Add a comment to a specific post (requires authentication).
  - `PUT /api/comments/{comment_id}`: Update a specific comment (requires authentication).
  - `DELETE /api/comments/{comment_id}`: Delete a specific comment (requires authentication).

## Entities

The Blog Application defines the following entities:

1. **Post**: Represents a blog post with fields for title, content, image, category, and user.
2. **User**: Represents a user with fields for name, password, about, email, and username.
3. **Comment**: Represents a comment with a content field, linked to a post and a user.
4. **Category**: Represents a blog category with a title.

These entities have relationships as follows:

- Each Category can have multiple Posts.
- Each User can have multiple Posts and Comments.
- Each Post can have multiple Comments.

## Authentication

Authentication in this application is based on JSON Web Tokens (JWT). When a user successfully logs in, a JWT token is provided, which must be included in the headers of protected endpoints. The application ensures that only authenticated users can create, update, or delete posts and comments.


## Images of swagger-ui
Token: Bearer <Token>

registerUser: 

![img23](https://github.com/omarbaig007212/SpringBoot-BlogApplication/assets/58821151/0df390f0-894b-4807-8540-8cd0df799907)
![img24](https://github.com/omarbaig007212/SpringBoot-BlogApplication/assets/58821151/b1de393c-f041-42d3-899b-3a79afe4b28f)

Login User: 

![img27](https://github.com/omarbaig007212/SpringBoot-BlogApplication/assets/58821151/5a202ee0-2d0d-4f7f-bb1f-d968dc1132a2)
![img28](https://github.com/omarbaig007212/SpringBoot-BlogApplication/assets/58821151/7ea7a45f-37d3-4e87-9a14-a2c118cd4d1f)
Register a token to authorize:

![img29](https://github.com/omarbaig007212/SpringBoot-BlogApplication/assets/58821151/2a546fef-f2ac-4c05-acd4-6b2ea7914af6)
Category (POST) (Create):

![img30](https://github.com/omarbaig007212/SpringBoot-BlogApplication/assets/58821151/7d6cf4c4-349e-43a9-b676-6f3075197a8a)
![img31](https://github.com/omarbaig007212/SpringBoot-BlogApplication/assets/58821151/937cc5f3-1b8c-4a46-a95e-8f4e20981e12)

Create a post using category_id and post_id :

![img32](https://github.com/omarbaig007212/SpringBoot-BlogApplication/assets/58821151/31a83a14-ec48-4596-95b5-e4a5b115834f)
![img33](https://github.com/omarbaig007212/SpringBoot-BlogApplication/assets/58821151/a2d548cc-1f9f-4d76-af1f-9ca4698a2e85)


Please ensure you include the JWT token in the `Authorization` header of your HTTP requests to access protected resources.

This README provides an overview of the Blog Application, including its setup, endpoints, entities, and authentication mechanism. You can now use this information to explore and interact with the application.
