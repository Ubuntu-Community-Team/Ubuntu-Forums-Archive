---
title: "Problem with the classpath setting"
date: 2011-03-13
forum: New to Ubuntu
---

### Post by amityadav9314 on 2011-03-13
Hi
I recent-ally installed glassfish server.
As I need to run servlet on that, so i need to set the classpath of 
javax.servlet package.
So what i did, I made a folder and put all those files which are required to run/compile a servlet in lib folder of glassfish.
And then I set the classpath of the folder which contain javax.servlet package.
And here how i edited the .bashrc file....

export JAVA_HOME=/usr/lib/Java6u1
export PATH=$PATH:$JAVA_HOME/bin
export CLASSPATH=/home/amit/glassfish3/glassfish/lib/java

last line I have added myself..

Now here comes the problem...
Now when i compile any java program and try to run it, it throws the following exception....


amit@Ubuntu:~$ cd Desktop/
amit@Ubuntu:~/Desktop$ ls
Test.class  Test.java  Test.java~
amit@Ubuntu:~/Desktop$ javac Test.java
amit@Ubuntu:~/Desktop$ java Test
Exception in thread "main" java.lang.NoClassDefFoundError: Test
Caused by: java.lang.ClassNotFoundException: Test
	at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
Could not find the main class: Test. Program will exit.
amit@Ubuntu:~/Desktop$ java -cp . Test
amit
amit@Ubuntu:~/Desktop$ 


But when i run the java program by "java -cp . Test" command i get the program running. But the program should run by just this command only.."java Test"...

If I delete the last line of classapath that i added by myself in .bashrc file, i get the program running by just this command..."java Test"

Can any one tell me how to solve this problem?

---

