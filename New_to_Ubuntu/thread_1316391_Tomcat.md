---
title: "Tomcat"
date: 2009-11-05
forum: New to Ubuntu
---

### Post by paul88 on 2009-11-05
Hi - I am completely new to linux and would like to install tomcat 5.5 how do i go about doing this?

I have tried using sudo apt-get install tomcat5

i have tried using tomcat6 but that doesn't contain the classes folder.

thanks

---

### Post by paul88 on 2009-11-05
Hi i am trying to install tomcat 5 how do i do this?

i installed 6 but that didn't have a classes folder and how do i install it to my home dir?


thanks

---

### Post by giants_fan on 2009-11-06
What I do is just to unzip it (it really doesn't need to be installed) into my home directory.

It'll create a directory called "apache-tomcat-6.0.20" or something.  Go into that directory's "bin" directory and do:

./catalina.sh run

And then go into your browser:

[http://localhost:8080](http://localhost:8080)

---

### Post by Mighty_Joe on 2009-11-06
Please don't post the [same question ]("http://ubuntuforums.org/showthread.php?t=1316391") more than once. It causes confusion and duplication of effort.

---

### Post by paul88 on 2009-11-06
Thank you.

How would I set it up so that I could just type 

```
tomcat start
```in order to start it

thanks again

---

### Post by paul88 on 2009-11-06
I have installed unzipped tomcat and am having trouble with it when starting tomcat

```
paul@paul-laptop:~/apache-tomcat-6.0.20/bin$ ./catalina.sh run
Using CATALINA_BASE:   /home/paul/apache-tomcat-6.0.20
Using CATALINA_HOME:   /home/paul/apache-tomcat-6.0.20
Using CATALINA_TMPDIR: /home/paul/apache-tomcat-6.0.20/temp
Using JRE_HOME:       /usr/lib/java/
exec: 375: /usr/lib/java//bin/java: not found
```can anyone help me 

thanks

---

### Post by overdrank on 2009-11-06
Hi and please do not create multiple threads on the same issue. Threads merged. :)

---

### Post by giants_fan on 2009-11-07
> **paul88 said:**
> I have installed unzipped tomcat and am having trouble with it when starting tomcat

```
paul@paul-laptop:~/apache-tomcat-6.0.20/bin$ ./catalina.sh run
Using CATALINA_BASE:   /home/paul/apache-tomcat-6.0.20
Using CATALINA_HOME:   /home/paul/apache-tomcat-6.0.20
Using CATALINA_TMPDIR: /home/paul/apache-tomcat-6.0.20/temp
Using JRE_HOME:       /usr/lib/java/
exec: 375: /usr/lib/java//bin/java: not found
```can anyone help me 

thanks


I think you haven't installed java yet.  Try:
```

sudo apt-get install sun-java6-jdk
```

---

