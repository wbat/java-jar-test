# THe Amazing Maven Example Project!

This project demonstrates how to publish a Java JAR to GitHub Packages using GitHub Actions and how to use the published JAR in other projects.

## Publishing the JAR

The JAR is automatically published to GitHub Packages when:
- A push is made to the `main` branch
- A new release is created

The publishing process is handled by the GitHub Actions workflow defined in `.github/workflows/publish-jar.yml`.

## Using the Published JAR

To use the published JAR in another project, add the following to your `pom.xml`:

```xml
<repositories>
    <repository>
        <id>github</id>
        <url>https://maven.pkg.github.com/YOUR_GITHUB_USERNAME/maven</url>
    </repository>
</repositories>

<dependencies>
    <dependency>
        <groupId>com.example</groupId>
        <artifactId>maven-example</artifactId>
        <version>1.0-SNAPSHOT</version>
    </dependency>
</dependencies>
```

Replace `YOUR_GITHUB_USERNAME` with your actual GitHub username.

## Local Development

To use GitHub Packages in your local development environment:

1. Create or edit the file `~/.m2/settings.xml`
2. Add the following content:

```xml
<settings>
    <servers>
        <server>
            <id>github</id>
            <username>YOUR_GITHUB_USERNAME</username>
            <password>YOUR_PERSONAL_ACCESS_TOKEN</password>
        </server>
    </servers>
</settings>
```

Replace `YOUR_GITHUB_USERNAME` with your GitHub username and `YOUR_PERSONAL_ACCESS_TOKEN` with a GitHub Personal Access Token that has the `read:packages` scope.

## Building the Project

To build the project locally, run:

```
mvn clean package
```

This will compile the code and create a JAR file in the `target` directory.
