---
title: "Connector/j issues"
date: 2010-12-09
forum: New to Ubuntu
---

### Post by sydnik on 2010-12-09
Hi. I am new to this forum. Can someone help me with the following Connector/j issue. I get the following error when running my program.

java.lang.ClassNotFoundException: com.mysql.jdbc.Driver
        at java.net.URLClassLoader$1.run(URLClassLoader.java:202)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:190)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:248)
        at java.lang.Class.forName0(Native Method)
        at java.lang.Class.forName(Class.java:169)
        at PersonConnector.writeToDatabase(PersonConnector.java:88)
        at PersonConnector.addNewPerson(PersonConnector.java:33)
        at PersonMain.main(PersonMain.java:12)
Java Result: 1


Below is the code that causes the error:

public void writeToDatabase() {
        Connection conn = null;
        Statement statement = null;

        try {
            Class.forName("com.mysql.jdbc.Driver");
            conn = DriverManager.getConnection("jdbc:mysql://localhost:3306/java_test", "root", "J7wiqe3o");
            statement = conn.createStatement();
            ResultSet result = statement.executeQuery(" SELECT * FROM PERSON ");

            while(result.next()) {
                String hold = result.getString(1) + "#" + result.getString(2) + "#"
                + result.getString(3) + "#" + result.getCharacterStream(4) + "#"
                + result.getInt(5);

                for_database.add(hold);
            }
        }
        catch(SQLException sqlException) {
            sqlException.printStackTrace();
            System.exit(1);
        }
        catch(ClassNotFoundException classNotFound) {
             classNotFound.printStackTrace();
             System.exit(1);
        }
        finally {
           try {
               statement.close();
               conn.close();
           }
           catch(Exception exception) {
               exception.printStackTrace();
               System.exit(1);
           }
        }
    }

Please help!!!

---

### Post by lykeion on 2010-12-09
First of all, please encode code output in CODE tags using # button for readability.

You need to install the MySQL JDBC driver:
```
sudo apt-get install libmysql-java
```
The mysql-connector-java.jar file is installed to /usr/share/java directory. 
You need to add this jar-file to CLASSPATH or if you use an IDE like Eclipse/NetBeans/IntelliJ add this jar-file.
See [this]("http://marksman.wordpress.com/2009/03/01/setting-up-mysqljdbc-driver-on-ubuntu/") page how that is done.

---

