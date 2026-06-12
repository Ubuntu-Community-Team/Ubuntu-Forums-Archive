---
title: "Always get the error &quot;No such file or directory&quot;"
date: 2010-11-19
forum: New to Ubuntu
---

### Post by DarrenMR415 on 2010-11-19
No matter what I do my terminal always say No such file or directory.  Ive check my spelling, Ive check case.  What do I do????

---

### Post by oldsoundguy on 2010-11-19
> **DarrenMR415 said:**
> No matter what I do my terminal always say No such file or directory.  Ive check my spelling, Ive check case.  What do I do????

did you cd to the folder that contains the file?

---

### Post by Quackers on 2010-11-19
It depends on what you were trying to do, and how. Can you give an example please?

---

### Post by DarrenMR415 on 2010-11-19
I am attempting to learn java programing.  [[HTML]http://download.oracle.com/javase/tutorial/getStarted/cupojava/unix.html[/HTML]]("http://download.oracle.com/javase/tutorial/getStarted/cupojava/unix.html")  

```
Bring up another shell window. To compile your source file, change your current directory
 to the directory where your file is located. For example, if your source directory is
 /home/jdoe/java, type the following command at the prompt and press Return: 
cd /home/jdoe/java

If you enter pwd at the prompt, you should see the current directory, which in this
 example has  been changed to /home/jdoe/java.
```

```
darren@darren-laptop:~/java$
```

```
darren@darren-laptop:~/java$ /home/darren/java/HelloWorldApp.java
bash: /home/darren/java/HelloWorldApp.java: No such file or directory

```

---

### Post by DarrenMR415 on 2010-11-19
I got it.  Ive still had trouble trying to get files that I know exist in other places though.  But Ive finished writting my first java app ever!

---

### Post by The Cog on 2010-11-19
Your problem is that /home/darren/java/HelloWorldApp.java doesn't exist. I guess you downloaded it to somewhere else.

Your second problem is that just naming the file will try to execute it, which will get a permission denied message because the file is not executable. You probably want to edit the file **gedit HelloWorldApp.java** or compile it **javac HelloWorldApp.java**

---

