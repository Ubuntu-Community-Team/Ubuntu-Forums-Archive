---
title: "working with JDBC in ubuntu"
date: 2011-02-22
forum: New to Ubuntu
---

### Post by manish411 on 2011-02-22
I have installed mysql query browser in my laptop.
When I compile the following program I get no compilation error
:import java.io.*;
import java.sql.*;

public class CreateDatabase{
  public static void main(String[] args) {
    System.out.println("Database creation example!");
    Connection con = null;
    try{
      Class.forName("com.mysql.jdbc.Driver");
      con = DriverManager.getConnection
("jdbc:mysql://localhost:3306/jdbctutorial","root","root");
      try{
        Statement st = con.createStatement();
        BufferedReader bf = new BufferedReader
(new InputStreamReader(System.in));
        System.out.println("Enter Database name:");
        String database = bf.readLine();
        st.executeUpdate("CREATE DATABASE "+database);
        System.out.println("1 row(s) affacted");
      }
      catch (SQLException s){
        System.out.println("SQL statement is not executed!");
      }
    }
    catch (Exception e){
      e.printStackTrace();
    }
  }
}
However when I try to run the program I get the following problem
java.lang.ClassNotFoundException: com.mysql.jdbc.Driver
    at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
    at java.lang.Class.forName0(Native Method)
    at java.lang.Class.forName(Class.java:186)
    at CreateDatabase.main(CreateDatabase.java:9

do we have install the driver separately??

---

### Post by freak42 on 2011-02-22
[https://help.ubuntu.com/community/JDBCAndMySQL](https://help.ubuntu.com/community/JDBCAndMySQL)

hth

---

### Post by lykeion on 2011-02-22
> **manish411 said:**
> do we have install the driver separately??
Yes you do, install like this:
```
sudo apt-get install libmysql-java
```
Then you'll also need to add it to classpath, like this:
```
CLASSPATH=$CLASSPATH:/usr/share/java/mysql.jar
export CLASSPATH
```

PS Please enclose code output in code tags using # button for readability.

---

### Post by theDaveTheRave on 2011-02-22
I would assume also that you are using an IDE (eclipse or similar). Somewhere in the options settings you can set the classpath also, so if you are on a system where you are testing using both the openJDK and Sun's JavaJDK you can easily switch between them.

I only mention this as I have always had issues attempting to set / amend the classpath on my systems. Although now I think about it maybe I should be performing this as 'root' and not as a standard user?

Good luck with the JDBC, I remember it not being extremly easy to get working (almost worrying so!). If you have any issues with your connection drop me a note and you can have a copy of my 'JavaMySQLTest' so as you can compare it to what you have.

David

---

