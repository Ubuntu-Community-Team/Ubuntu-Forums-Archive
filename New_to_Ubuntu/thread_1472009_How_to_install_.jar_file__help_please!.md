---
title: "How to install .jar file  help please!"
date: 2010-05-04
forum: New to Ubuntu
---

### Post by appoloin on 2010-05-04
Hello
trying to install this to my computer " JBidwatcher-2.1pre6.jar" but i think im doing it all wrong SEE BELLOW"

ed@ed-desktop:~$ cd Desktop
ed@ed-desktop:~/Desktop$ ls
360Share+Pro.desktop            JBidwatcher-2.1pre6      Steam.desktop
360Share+Pro+Downloads.desktop  JBidwatcher-2.1pre6.jar  Xswim
Diablo+II.desktop               MagicISO.desktop
ed@ed-desktop:~/Desktop$ cd '/home/ed/Desktop/JBidwatcher-2.1pre6' cd
ed@ed-desktop:~/Desktop/JBidwatcher-2.1pre6$ \ cd
cd: command not found
ed@ed-desktop:~/Desktop/JBidwatcher-2.1pre6$ \cd
ed@ed-desktop:~$ cd '/home/ed/Desktop/JBidwatcher-2.1pre6' 
ed@ed-desktop:~/Desktop/JBidwatcher-2.1pre6$ ls
boot-manifest.mf  com  lib  main  META-INF
ed@ed-desktop:~/Desktop/JBidwatcher-2.1pre6$ ./install
bash: ./install: No such file or directory
ed@ed-desktop:~/Desktop/JBidwatcher-2.1pre6$ ls
boot-manifest.mf  com  lib  main  META-INF
ed@ed-desktop:~/Desktop/JBidwatcher-2.1pre6$ ./'/home/ed/Desktop/JBidwatcher-2.1pre6/boot-manifest.mf' 
bash: .//home/ed/Desktop/JBidwatcher-2.1pre6/boot-manifest.mf: No such file or directory
ed@ed-desktop:~/Desktop/JBidwatcher-2.1pre6$ ls
boot-manifest.mf  com  lib  main  META-INF
ed@ed-desktop:~/Desktop/JBidwatcher-2.1pre6$ 



cOULD SOMEONE PLEASE HELP ME AND GIVE ME STEP BY STEP COMMEND TOINSTALL THIS PLEASE????

---

### Post by appoloin on 2010-05-04
sorry to bother everyone out there but is there anyone can help me install this please???????

---

### Post by Bradtek on 2010-05-04
Don't install it, run it with Java

eg. Richt click on it and choose open with Sun Java 6 Runtime
(or whatever version of Java you have installed)

---

### Post by legatek on 2010-05-04
You don't install a .jar file, you run it using java. First, check if you have java installed:

```
java -version
```

If you don't, install java:

```
sudo apt-get install sun-java6-bin, sun-java6-jre
```

then run the .jar file as follows:

```
java -jar JBidwatcher-2.1pre6.jar
```

Maybe you need sudo before that last command, I don't know. Try it without first.

---

### Post by ankspo71 on 2010-05-04
Hi,
To me it looks like you extracted the jar file. Extracting shouldn't be necessary. 

First, if your jar file is located on the desktop, open a new terminal window and change directories to your desktop
```
cd Desktop
```

Next is the typical command to run or install "jar" applications/files.
```
java -jar JBidwatcher-2.1pre6.jar
```

If you need more help with Java, you can open a terminal and type:
**man java**
**java --help** (or **java -h** on my system with OpenJDK)
**info java**

---

### Post by appoloin on 2010-05-04
thank you guys

---

### Post by moparfreak426 on 2013-02-02
I've been trying to figure out how how to install casual to unlock my bootloader on verizon samsung galaxy note 2. I am still having trouble trying to install a .jar file

---

### Post by zealibib slaughter on 2013-02-02
you dont install jar files as stated above you type this into a terminal ```
java -jar *myjarfile*.jar
```
replace myjarfile with the name of the jar file you wish to run.

---

### Post by jerome1232 on 2013-02-02
snip--- necro thread how did I not notice that

---

### Post by lisati on 2013-02-02
Old thread closed.

---

