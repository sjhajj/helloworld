# Use an official Maven image to build the application
FROM maven:3.8.1-openjdk-11 AS build

# Set the working directory
WORKDIR /app

# Copy the pom.xml and source code into the container
COPY pom.xml .
COPY src ./src

# Build the application
RUN mvn clean package -DskipTests

# Use an OpenJDK image to run the application
FROM openjdk:11-jre-slim

# Set the working directory
WORKDIR /app

# Copy the JAR file from the build stage
COPY --from=build /app/target/helloworld-1.1.jar ./helloworld-1.1.jar

# Command to run the application
ENTRYPOINT ["java", "-cp", "helloworld-1.1.jar", "com.coveros.demo.helloworld.HelloWorld"]

