1️⃣ Spring Boot Core & Fundamentals — ANSWERS
What is Spring Boot?
Spring Boot is an opinionated framework built on top of Spring that simplifies application setup by providing auto-configuration, embedded servers, and starter dependencies so developers can focus on business logic instead of boilerplate.

Difference between Spring and Spring Boot?
Spring is a framework that requires manual configuration.
Spring Boot reduces configuration by:
Auto-configuring beans
Providing embedded Tomcat
Using starter dependencies
Eliminating XML configs

What are starter dependencies?
Starters are curated dependency bundles like spring-boot-starter-web that pull in all required libraries with compatible versions.

What is auto-configuration?
Auto-configuration automatically configures beans based on:
Classpath dependencies
Application properties
Existing beans
Example: If spring-webmvc is on the classpath, Spring auto-configures DispatcherServlet.

What does @SpringBootApplication do?
It combines:
@Configuration
@EnableAutoConfiguration
@ComponentScan

Difference between @Component, @Service, @Repository?
They’re functionally the same but semantically different:
@Component: generic bean
@Service: business logic
@Repository: data access + exception translation

Controller vs RestController?
@Controller → returns views
@RestController → returns JSON (adds @ResponseBody)

What is Dependency Injection?
DI allows objects to receive dependencies externally rather than creating them internally. It improves testability, decoupling, and maintainability.
Constructor injection is preferred because:
Makes dependencies explicit
Easier testing
Immutable fields

2️⃣ REST APIs & Controllers — ANSWERS
Difference between GET, POST, PUT, PATCH?
GET → fetch data
POST → create resource
PUT → replace entire resource (idempotent)
PATCH → partial update

Path variable vs query param?
Path variable → identifies resource (/users/{id})
Query param → filtering/sorting (/users?page=1)

What is ResponseEntity?
ResponseEntity allows full control over:
HTTP status
Headers
Response body

What is idempotency?
An operation is idempotent if repeating it produces the same result.
PUT and DELETE are idempotent
POST is not

How do you version APIs?
URL versioning: /api/v1/users
Header versioning
Media type versioning
URL versioning is simplest and most common.

What happens when an exception occurs?
Without handling → 500 error
With global handling → controlled error response via @ControllerAdvice

3️⃣ Spring Data JPA — ANSWERS
What is JPA?
JPA is a Java specification for ORM that maps Java objects to database tables.

What is Hibernate?
Hibernate is the most popular JPA implementation.

CrudRepository vs JpaRepository?
CrudRepository → basic CRUD
JpaRepository → CRUD + pagination + sorting + batch ops

What does @Entity do?
Marks a class as a persistent JPA entity mapped to a table.

Lazy vs Eager loading?
Lazy → fetch when accessed (default for collections)
Eager → fetch immediately
Lazy is preferred to avoid performance issues.

What is the N+1 problem?
Occurs when fetching a collection lazily causes one query per child entity.
Solved using:
Fetch joins
Entity graphs
Batch fetching

What does @Transactional do?
Ensures a method runs within a database transaction.
Commits on success
Rolls back on runtime exceptions

Why not put @Transactional on controllers?
Controllers should handle HTTP, not business logic.
Transactions belong in the service layer.

4️⃣ Exception Handling & Validation — ANSWERS
How do you handle exceptions globally?
Using @ControllerAdvice with @ExceptionHandler.

What is @ControllerAdvice?

A centralized exception handling mechanism across all controllers.
What is @Valid?
Triggers bean validation on request bodies using annotations like:
@NotNull
@Size
@Email

What happens if validation fails?
Spring throws MethodArgumentNotValidException, which should be handled globally.

5️⃣ Configuration & Profiles — ANSWERS
application.yml vs properties?
YAML is hierarchical and more readable.
Functionally identical.

What are Spring Profiles?
Profiles allow environment-specific configuration (dev, test, prod).

How do you manage secrets?
Environment variables
Vault / Secrets Manager
Never commit secrets to Git

@Value vs @ConfigurationProperties?
@Value → single value
@ConfigurationProperties → group related configs (preferred)

6️⃣ Spring Security — ANSWERS (VERY IMPORTANT)
Authentication vs Authorization?
Authentication → who you are
Authorization → what you can do

How does JWT work?
User logs in
Server issues signed JWT
Client sends JWT in Authorization header
Server validates token per request

What is OncePerRequestFilter?
A filter that runs once per request, typically used for JWT validation.

How do you store passwords?
Using BCrypt hashing. Never store plaintext passwords.

What is CSRF?

Cross-Site Request Forgery.
Disabled for stateless APIs using JWT.

How do you implement role-based access?
Using:
@PreAuthorize("hasRole('ADMIN')")

7️⃣ Performance & Scalability — ANSWERS
Is Spring Boot single-threaded?
No. It uses a thread pool (Tomcat/Netty) to handle concurrent requests.

How does Spring Boot scale?
Stateless services
Horizontal scaling
Load balancers

How do you improve performance?
Pagination
Caching
Connection pooling (HikariCP)
Avoid N+1 queries

8️⃣ Testing — ANSWERS
Unit vs Integration tests?
Unit → isolated, fast
Integration → full context, slower

What is @SpringBootTest?

Loads the full application context for integration testing.

What is @WebMvcTest?
Loads only controller layer for fast API testing.

How do you mock dependencies?
Using Mockito:
@MockBean

9️⃣ Deployment & Production — ANSWERS
How is Spring Boot packaged?
As a fat JAR with embedded Tomcat.

What are Actuators?
Production monitoring endpoints like:
/health
/metrics

How do you log?
Using SLF4J with Logback.
Log at appropriate levels (INFO, WARN, ERROR).

🔥 10️⃣ JPMC HYBRID QUESTIONS — ANSWERS
“Describe a Spring Boot service you built”
Explain:
API design
Database model
Security
Error handling
Transactions

“What if two requests update same record?”
Use:
Database locking
Optimistic locking (@Version)
Proper isolation levels

“How do you ensure consistency?”
Transactions
Rollbacks
Idempotent APIs

🧠 FINAL INTERVIEW TIP (IMPORTANT)
JPMC doesn’t want encyclopedias.
They want calm, structured thinking.
If you can:
Explain why
Tie answers to your project
Mention tradeoffs

👉 You’re already ahead of 80% of candidates.

If you want next:
🎯 Mock JPMC Spring Boot interview
🛠️ Exact Spring Boot project template to memorize
🔍 Tricky follow-ups interviewers use to trap candidates

1. java interview questions
2. DesignPair Round (45 minutes): This will involve one system design/whiteboarding question.
Behavioral Round (45 minutes): We will assess soft skills, career aspirations, and teamwork/leadership qualities.
