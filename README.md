# Software Packaging in Popular Frameworks

## Project Overview

This project demonstrates the fundamental principles of software packaging across three popular application development ecosystems:

* Node.js
* Python/Django
* Java/Spring Boot

The project focuses on dependency management, semantic versioning, environment configuration, application building, packaging, security auditing and verification of packaged applications.

The objective is to demonstrate how application source code and dependencies can be packaged consistently so that applications can be built and executed across different environments.

---

## Project Objectives

The project demonstrates the following DevOps and software packaging practices:

* Application dependency management
* Dependency installation and version locking
* Semantic Versioning
* Environment-specific configuration
* Automated application builds
* Creation of distributable application artifacts
* Application verification
* Dependency security auditing
* Git version control
* GitHub source-code management
* Documentation of the packaging process

---

# Technology Stack

| Technology    | Tool        | Purpose                                         |
| ------------- | ----------- | ----------------------------------------------- |
| Node.js       | npm         | JavaScript dependency management                |
| Node.js       | Express     | Web application framework                       |
| Python        | pip         | Python dependency management                    |
| Python        | Django      | Web application framework                       |
| Java          | Maven       | Java dependency management and build automation |
| Java          | Spring Boot | Java web application framework                  |
| Git           | Git         | Source control                                  |
| GitHub        | GitHub      | Remote repository                               |
| Security      | npm audit   | Node.js dependency security                     |
| Security      | pip-audit   | Python dependency security                      |
| Configuration | `.env`      | Environment-specific settings                   |

---

# Project Structure

```text
software-packaging-frameworks/
│
├── node-app/
│   ├── index.js
│   ├── package.json
│   ├── package-lock.json
│   ├── .env.example
│   └── .gitignore
│
├── django-app/
│   ├── manage.py
│   ├── requirements.txt
│   ├── .env.example
│   ├── .gitignore
│   └── django_app/
│
├── spring-app/
│   ├── pom.xml
│   └── src/
│       └── main/
│           └── java/
│               └── com/
│                   └── example/
│                       └── demo/
│                           └── Application.java
│
├── screenshots/
│
└── README.md
```

---

# 1. Node.js Packaging

## 1.1 Create the Node.js Application

Navigate to the Node.js directory:

```bash
cd node-app
```

Initialise the Node.js project:

```bash
npm init -y
```

Install Express:

```bash
npm install express
```

This creates the following dependency files:

```text
package.json
package-lock.json
```

The `package.json` file defines the application metadata and dependencies.

The `package-lock.json` file records the resolved dependency versions to improve build consistency.

---

## 1.2 Node.js Application

The Node.js application is contained in:

```text
index.js
```

Example:

```javascript
const express = require("express");

const app = express();
const PORT = process.env.PORT || 3000;

app.get("/", (req, res) => {
    res.json({
        application: "Software Packaging Demo",
        framework: "Node.js",
        version: "1.0.0",
        environment: process.env.NODE_ENV || "development"
    });
});

app.listen(PORT, () => {
    console.log(`Node application running on port ${PORT}`);
});
```

---

## 1.3 Run the Node.js Application

Install dependencies:

```bash
npm install
```

Start the application:

```bash
npm start
```

The application runs on:

```text
http://localhost:3000
```

Expected response:

```json
{
  "application": "Software Packaging Demo",
  "framework": "Node.js",
  "version": "1.0.0",
  "environment": "development"
}
```

---

## 1.4 Node.js Security Audit

Run:

```bash
npm audit
```

To automatically apply compatible fixes:

```bash
npm audit fix
```

The audit identifies known vulnerabilities within installed Node.js dependencies.

---

# 2. Python/Django Packaging

## 2.1 Create the Python Virtual Environment

Navigate to the Django application:

```bash
cd ../django-app
```

Create a virtual environment:

```bash
python3 -m venv venv
```

Activate it on Linux/WSL:

```bash
source venv/bin/activate
```

On Windows PowerShell:

```powershell
.\venv\Scripts\Activate.ps1
```

---

## 2.2 Install Django

Upgrade pip:

```bash
python -m pip install --upgrade pip
```

Install Django:

```bash
pip install django
```

Check the Django version:

```bash
django-admin --version
```

---

## 2.3 Create the Django Application

Create the project:

```bash
django-admin startproject django_app .
```

The main project files include:

```text
manage.py
django_app/
├── __init__.py
├── settings.py
├── urls.py
├── asgi.py
└── wsgi.py
```

---

## 2.4 Generate the Dependency File

Generate `requirements.txt`:

```bash
pip freeze > requirements.txt
```

This records the installed Python packages and their versions.

Another environment can install the same dependencies using:

```bash
pip install -r requirements.txt
```

---

## 2.5 Run Django

Start the development server:

```bash
python manage.py runserver
```

The application is available at:

```text
http://127.0.0.1:8000
```

---

## 2.6 Python Dependency Security Audit

Install `pip-audit`:

```bash
pip install pip-audit
```

Run the audit:

```bash
pip-audit
```

This checks installed Python dependencies against known vulnerability information.

---

# 3. Java/Spring Boot Packaging

## 3.1 Java and Maven

Check Java:

```bash
java -version
```

Check the Java compiler:

```bash
javac -version
```

Check Maven:

```bash
mvn -version
```

The project is configured to use Java 17.

---

# 3.2 Spring Boot Project Structure

The Spring Boot application uses the following structure:

```text
spring-app/
│
├── pom.xml
│
└── src/
    └── main/
        └── java/
            └── com/
                └── example/
                    └── demo/
                        └── Application.java
```

The Java package is:

```java
package com.example.demo;
```

---

# 3.3 Maven Dependency Management

The project uses Maven through:

```text
pom.xml
```

The POM defines:

* Project name
* Project version
* Java version
* Spring Boot version
* Spring Web dependency
* Spring Boot Maven Plugin
* Test dependencies

Example project version:

```text
1.0.0
```

---

# 3.4 Spring Boot Application

The main application is:

```text
src/main/java/com/example/demo/Application.java
```

Example:

```java
package com.example.demo;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RestController;

@SpringBootApplication
@RestController
public class Application {

    public static void main(String[] args) {
        SpringApplication.run(Application.class, args);
    }

    @GetMapping("/")
    public String home() {
        return """
        {
          "application": "Software Packaging Demo",
          "framework": "Spring Boot",
          "version": "1.0.0",
          "status": "running"
        }
        """;
    }
}
```

The `main()` method is the entry point for the Spring Boot application.

---

# 3.5 Build the Spring Boot Application

Navigate to the Spring Boot project:

```bash
cd ../spring-app
```

Clean previous build files:

```bash
mvn clean
```

Build and package the application:

```bash
mvn clean package
```

Maven performs several stages:

```text
Source Code
     ↓
Dependency Resolution
     ↓
Compilation
     ↓
Testing
     ↓
Packaging
     ↓
JAR Artifact
```

A successful build should display:

```text
BUILD SUCCESS
```

---

# 3.6 Spring Boot JAR Artifact

After a successful Maven build, the packaged application is created inside:

```text
target/
```

Example:

```text
target/spring-packaging-demo-1.0.0.jar
```

This JAR file is the distributable application artifact.

---

# 3.7 Run the Packaged JAR

Run:

```bash
java -jar target/spring-packaging-demo-1.0.0.jar
```

The application starts on port `8080`.

Open:

```text
http://localhost:8080
```

Expected response:

```json
{
  "application": "Software Packaging Demo",
  "framework": "Spring Boot",
  "version": "1.0.0",
  "status": "running"
}
```

This verifies that the packaged artifact can be executed independently.

---

# 4. Semantic Versioning

Semantic Versioning is represented as:

```text
MAJOR.MINOR.PATCH
```

The project uses:

```text
1.0.0
```

### MAJOR

Incremented when incompatible or breaking changes are introduced.

Example:

```text
1.0.0 → 2.0.0
```

### MINOR

Incremented when backwards-compatible functionality is added.

Example:

```text
1.0.0 → 1.1.0
```

### PATCH

Incremented for backwards-compatible bug fixes.

Example:

```text
1.0.0 → 1.0.1
```

Semantic versioning is demonstrated through the application metadata and Maven project version.

---

# 5. Environment Configuration

Environment-specific configuration should be kept separate from application source code.

Example:

```text
.env.example
```

Node.js example:

```env
NODE_ENV=development
PORT=3000
```

Django example:

```env
DEBUG=True
SECRET_KEY=change-me
ALLOWED_HOSTS=127.0.0.1,localhost
```

Actual `.env` files should not be committed to Git when they contain secrets or environment-specific credentials.

The `.gitignore` files therefore exclude:

```text
.env
```

---

# 6. Dependency Locking

Different ecosystems use different dependency management mechanisms.

### Node.js

```text
package.json
package-lock.json
```

### Python

```text
requirements.txt
```

### Java

```text
pom.xml
```

These files allow dependencies to be documented and installed consistently.

---

# 7. Security Auditing

Dependency security checks were performed using:

### Node.js

```bash
npm audit
```

### Python

```bash
pip-audit
```

These tools identify known security vulnerabilities affecting dependencies.

Security findings should be reviewed before deployment and dependencies should be updated where appropriate.

---

# 8. Application Verification

Each application was tested after dependency installation and packaging.

| Application | Port | Verification            |
| ----------- | ---: | ----------------------- |
| Node.js     | 3000 | Browser/API response    |
| Django      | 8000 | Django development page |
| Spring Boot | 8080 | Browser/API response    |

The Spring Boot application was additionally verified by executing the generated JAR:

```bash
java -jar target/spring-packaging-demo-1.0.0.jar
```

---

# 9. Git Version Control

Initialise the repository:

```bash
git init
```

Check the repository:

```bash
git status
```

Stage files:

```bash
git add .
```

Create a commit:

```bash
git commit -m "Add software packaging examples"
```

View commits:

```bash
git log --oneline
```

---

# 10. GitHub

The project can be uploaded to GitHub using:

```bash
git branch -M main
```

Add the remote repository:

```bash
git remote add origin https://github.com/YOUR_USERNAME/software-packaging-frameworks.git
```

Push the project:

```bash
git push -u origin main
```

Replace:

```text
YOUR_USERNAME
```

with the GitHub username.

---

# 11. Screenshot Evidence

The following screenshots were captured as evidence of the implementation:

```text
screenshots/
│
├── 01-project.png
├── 02-git.png
├── 03-node-install.png
├── 04-node-running.png
├── 05-node-audit.png
├── 06-python-venv.png
├── 07-requirements.png
├── 08-django-running.png
├── 09-pip-audit.png
├── 10-java-maven.png
├── 11-maven-package.png
├── 12-spring-jar.png
├── 13-git-commit.png
└── 14-github.png
```

Each screenshot provides evidence of a specific stage of the packaging process.

---

# 12. Troubleshooting

## Maven: Non-readable POM

If Maven reports:

```text
Non-readable POM
input contained no data
```

check that `pom.xml` is not empty:

```bash
cat pom.xml
```

---

## Maven: Unable to find main class

If Maven reports:

```text
Unable to find main class
```

verify that the application exists at:

```text
src/main/java/com/example/demo/Application.java
```

Check the Java package:

```java
package com.example.demo;
```

Check that the application contains:

```java
public static void main(String[] args) {
    SpringApplication.run(Application.class, args);
}
```

Then clean and rebuild:

```bash
mvn clean package
```

---

# 13. Project Learning Outcomes

This project demonstrates practical knowledge of software packaging across multiple ecosystems.

The implementation covers:

* Dependency management
* Dependency locking
* Semantic versioning
* Environment separation
* Build automation
* Application packaging
* JAR artifact generation
* Dependency security auditing
* Application verification
* Git version control
* GitHub repository management

---

# 14. Conclusion

This project demonstrates how different application ecosystems package software for consistent deployment.

Node.js uses npm and `package.json`, Python/Django uses pip and `requirements.txt`, while Java/Spring Boot uses Maven and `pom.xml`.

The applications were configured with version information, dependencies were installed and audited, and the Spring Boot application was packaged into a distributable JAR artifact.

The project demonstrates the relationship between software development, dependency management, security, build automation and deployment within a DevOps workflow.

---

## Final Packaging Workflow

```text
Application Source Code
          ↓
Dependency Definition
          ↓
Dependency Installation
          ↓
Semantic Versioning
          ↓
Environment Configuration
          ↓
Security Audit
          ↓
Build Automation
          ↓
Application Packaging
          ↓
Distributable Artifact
          ↓
Application Verification
          ↓
Git Commit
          ↓
GitHub Repository
```
