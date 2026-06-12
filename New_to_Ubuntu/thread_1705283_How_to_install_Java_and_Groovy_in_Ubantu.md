---
title: "How to install Java and Groovy in Ubantu?"
date: 2011-03-12
forum: New to Ubuntu
---

### Post by antoaravinth on 2011-03-12
Hi all, i'm a new user to ubantu! so i need your help, how to install java and groovy in ubantu?? 
Please say by step by step:):popcorn:

---

### Post by milindo on 2011-03-12
Ubuntu, not ubantu :P

press alt+f2 and type gnome_terminal and press enter. 
A purple thing should appear. 

Enter in the purple thing: 
```
sudo apt-get install sun-java6-jre
``` and press enter. Enter your password. Java is installed.  Check by typing "java"(without "") to see if it works

---

### Post by a2warik on 2011-03-12
You can install groovy from the synaptic package manager(System>Administration>) directly which will take care of all the dependencies as well.

After you install java as shown by [milindo]("http://ubuntuforums.org/member.php?u=1256715") simply type in the  
```

java -jar /file/path/of/the/program/that/one/has/to/install 

```
I hope this helps. guess what even i am new to ubuntuforums
:popcorn:

---

### Post by lykeion on 2011-03-12
I'm not sure whether two above posters really know anything about groovy, so I'm gonna give you a step by step that works.

1. Install groovy with a package manager
In GUI package managers like Ubuntu Software Center and Synaptic you can search for "groovy" (without quotes) and simply install it. However I would recommend that you do this from a terminal. So launch a terminal (Applications > Accessories > Terminal) and use *apt-get* to install groovy by entering this command:
```
sudo apt-get install groovy
```
2. After installation you can try to launch the groovy shell. I suggest you do this in a terminal. Enter this command:
```
groovysh
```
However if you don't have a Java JDK installed you'll get an error message, something like this:
```
JAVA_HOME not set and cannot find javac to deduce location, please set JAVA_HOME.
```
To install a JDK please follow step 3.

3. Install OpenJDK JDK
From a terminal use apt-get to install it like this:
```
sudo apt-get install openjdk-6-jdk
```

Now you have successfully setup the groovy and Java environment, so you could proceed to use the groovy shell to test groovy commands and write groovy code and compile it with groovyc.

To get started with groovy I would recommend the excellent guides and tutorials on the groovy homepage:
[http://groovy.codehaus.org/Documentation](http://groovy.codehaus.org/Documentation)

Hope this helps :)

---

### Post by milindo on 2011-03-12
> **lykeion said:**
> I'm not sure whether two above posters really know anything about groovy, so I'm gonna give you a step by step that works.

1. Install groovy with a package manager
In GUI package managers like Ubuntu Software Center and Synaptic you can search for "groovy" (without quotes) and simply install it. However I would recommend that you do this from a terminal. So launch a terminal (Applications > Accessories > Terminal) and use *apt-get* to install groovy by entering this command:
```
sudo apt-get install groovy
```
2. After installation you can try to launch the groovy shell. I suggest you do this in a terminal. Enter this command:
```
groovysh
```
However if you don't have a Java JDK installed you'll get an error message, something like this:
```
JAVA_HOME not set and cannot find javac to deduce location, please set JAVA_HOME.
```
To install a JDK please follow step 3.

3. Install OpenJDK JDK
From a terminal use apt-get to install it like this:
```
sudo apt-get install openjdk-6-jdk
```

Now you have successfully setup the groovy and Java environment, so you could proceed to use the groovy shell to test groovy commands and write groovy code and compile it with groovyc.

To get started with groovy I would recommend the excellent guides and tutorials on the groovy homepage:
[http://groovy.codehaus.org/Documentation](http://groovy.codehaus.org/Documentation)

Hope this helps :)
I don't know about groovy alright but about java i know :P

---

