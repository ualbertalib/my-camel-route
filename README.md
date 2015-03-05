Camel Router WAR Project
========================
[![Build Status](https://travis-ci.org/ualbertalib/my-camel-route.svg?branch=master)](https://travis-ci.org/ualbertalib/my-camel-route)

This project includes a sample route as as a WAR.
You can build the WAR by running
```bash
    mvn install
```
You can then run the project by dropping the WAR into your 
favorite web container or just run
```bash
    mvn jetty:run
```
to start up and deploy to Jetty.

If you have JBoss AS running you can deploy using
```bash
   mvn jboss-as:deploy
```
Or to redeploy
```bash
    mvn jboss-as:redeploy
```
For more help see the Apache Camel documentation

    [http://camel.apache.org/](http://camel.apache.org/)

This project has been built using maven.
```bash
mvn archetype:generate \
  -DarchetypeGroupId=org.apache.camel.archetypes \
  -DarchetypeArtifactId=camel-archetype-web \
  -DarchetypeVersion=2.14.0 \
  -DgroupId=org.example.camel \
  -DartifactId=my-camel-route \
  -Dversion=1.0.0-SNAPSHOT \
  -Dpackage=org.example.camel
```

Camel Router in [Spring DSL](http://camel.apache.org/spring.html), [applicationContext.xml](https://github.com/ualbertalib/my-camel-route/src/main/webapp/WEB-INF/applicationContext.xml)
```xml
    <camelContext xmlns="http://camel.apache.org/schema/spring">
        <route id="timer-to-console">
            <from uri="timer://foo?fixedRate=true&amp;period=10s"/>
            <transform>
               <simple>Hello Web Application, how are you?</simple>
            </transform>
            <to uri="stream:out"/>
        </route>
    </camelContext>
```
