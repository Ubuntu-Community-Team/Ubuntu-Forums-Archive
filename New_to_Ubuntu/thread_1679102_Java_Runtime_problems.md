---
title: "Java Runtime problems"
date: 2011-01-31
forum: New to Ubuntu
---

### Post by kalebka55 on 2011-01-31
Hi,

I have a .jar file that I am trying to open.  I have had several similar .jar files that have been working fine.  This is the only one that is giving me problems.

Starting the .jar file normally (via selection of Java OpenJDK Java 6 RunTime) does absolutely nothing.  No response.

In terminal I get the message (after typing~ java -jar<filename>.jar)

[B]Exception in thread "main" java.lang.ArrayIndexOutOfBoundsException: 1
    at AppletMain.main(AppletMain.java:237)
[/B]
Can anyone advice me as to what I can do to get it running or as to what the problem is?

Thanks

---

### Post by mharrison on 2011-01-31
I won't pretend to be a programmer at all, but a quick google search of the error you posted leads me to believe there is an error with the code in your JAR file.

Someone else chime in if I am wrong...I'm just listening to the voices in my head ):P

---

### Post by lykeion on 2011-02-01
It may be that the application is supposed to be started with a parameter, like this: java -jar <filename>.jar <param>
It would be a lot easier to help if you could tell what application it is you are trying to launch...

---

### Post by SivaCoHan on 2011-02-01
Maybe it is coursed by OpenJDK ,
try SunJDK .

---

### Post by kalebka55 on 2011-02-01
> **SivaCoHan said:**
> Maybe it is coursed by OpenJDK ,
try SunJDK .


Same problem...  

The program is custom-made, it is an interactive quiz- no specific name/type.

I think mHarrison is right on this one... might just be a error within the code.  

Anyone else out there with suggestions?

---

### Post by moody_mark on 2011-02-01
> **kalebka55 said:**
> 
[B]Exception in thread "main" java.lang.ArrayIndexOutOfBoundsException: 1
    at AppletMain.main(AppletMain.java:237)
[/B]
Can anyone advice me as to what I can do to get it running or as to what the problem is?

Thanks

Yes, the program is expecting one or more additional arguments, without having the actual source code you wont know how many, normally its good programming practice if no arguments or the wrong number are specified then to prompt the user with some help text to show how to run.

Try running the program with a "-h" or "--help" they may have coded it to look for that input

For example

```
java -jar YourProgram.jar -h
```

---

### Post by kalebka55 on 2011-02-01
> **moody_mark said:**
> Yes, the program is expecting one or more additional arguments, without having the actual source code you wont know how many, normally its good programming practice if no arguments or the wrong number are specified then to prompt the user with some help text to show how to run.

Try running the program with a "-h" or "--help" they may have coded it to look for that input

For example

```
java -jar YourProgram.jar -h
```


Thanks moody_mark.  Unfortunately the response is the same..... :confused:

---

### Post by moody_mark on 2011-02-01
Try unjarring the file see whats inside, there may well be a readme inside

```

jar -xvf YourProgram.jar

```

---

### Post by VorpalBunny on 2011-02-01
mharrison is right, there is a coding error. Is the source code available somewhere? There's a good chance it's a really simple fix and as a CS student I'd enjoy having a go at it :)

---

### Post by kalebka55 on 2011-02-01
> **moody_mark said:**
> Try unjarring the file see whats inside, there may well be a readme inside

```

jar -xvf YourProgram.jar

```


This is what I get:

[B]java.io.FileNotFoundException: mw7q.jar (No such file or directory)
    at java.io.FileInputStream.open(Native Method)
    at java.io.FileInputStream.<init>(FileInputStream.java:106)
    at java.io.FileInputStream.<init>(FileInputStream.java:66)
    at sun.tools.jar.Main.run(Main.java:238)
    at sun.tools.jar.Main.main(Main.java:1149)

[/B]Ive also browsed the file contents but cannot find a readme.  How would one obtain the source code?

---

### Post by VorpalBunny on 2011-02-01
> **kalebka55 said:**
> How would one obtain the source code?

If you downloaded it from a website, you could poke around on that site for a link to sourceforge or some other site where people store source code to make it publicly available. Of course, it may not be open source so in that case you would have to just let the author know about the problem somehow and ask them to fix it.You mentioned it was custom made, so if you know the person that wrote it you could just ask them for the code, or ask them to fix the problem.

---

### Post by kalebka55 on 2011-02-01
You mentioned it was custom made, so if you know the person that wrote it you could just ask them for the code, or ask them to fix the problem.


It is an institution that has provided me with the program.  No-one else seems to be having this problem.  Perhaps something went wrong when my DVD was being created.  I'll try see if they can send me another copy...

Thanks everyone for your help.

Truly appreciated!

---

### Post by Andrew Jeyaraj on 2011-02-01
certainly has an error in the code.
i use netbeans ide and  get a lot of those lol:)
try running some other .jar file.

---

