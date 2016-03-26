
Spring Loaded with Spring Boot versions 1.3.{1,2,3}.RELEASE fails with:

    java.lang.IllegalAccessException: Class org.springsource.loaded.ReloadableType can not access a member of class org.springframework.context.annotation.ConfigurationClassEnhancer$BeanFactoryAwareGeneratorStrategy with modifiers "public"
        at sun.reflect.Reflection.ensureMemberAccess(Reflection.java:102)
        at java.lang.reflect.AccessibleObject.slowCheckMemberAccess(AccessibleObject.java:296)
        at java.lang.reflect.AccessibleObject.checkAccess(AccessibleObject.java:288)
        at java.lang.reflect.Method.invoke(Method.java:491)
        at org.springsource.loaded.ReloadableType.reloadProxiesIfNecessary(ReloadableType.java:568)
        at org.springsource.loaded.ReloadableType.loadNewVersion(ReloadableType.java:446)
        at org.springsource.loaded.TypeRegistry.loadNewVersion(TypeRegistry.java:1014)
        at org.springsource.loaded.agent.ReloadableFileChangeListener.fileChanged(ReloadableFileChangeListener.java:104)
        at org.springsource.loaded.agent.Watcher.determineChangesSince(FileSystemWatcher.java:251)
        at org.springsource.loaded.agent.Watcher.run(FileSystemWatcher.java:235)
        at java.lang.Thread.run(Thread.java:745)

The exception does not happen in Spring Boot version **1.3.0.RELEASE**.

### Reproduce ###
Set desired Spring Boot version in `pom.xml` in `project > parent > version`. Then run:

    mvn clean spring-boot:run 
    
To trigger hot swap run (in another console)

    mvn clean compile
