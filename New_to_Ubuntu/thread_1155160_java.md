---
title: "java"
date: 2009-05-10
forum: New to Ubuntu
---

### Post by lanceps on 2009-05-10
how do u install and compile java programs in ubuntu/linux

i used to use blue j in windows can anyone suggest a good ide in linux

---

### Post by SunnyRabbiera on 2009-05-10
well there is the java development kit...

---

### Post by lanceps on 2009-05-10
how do u use that in linux, sorry i know only how to compile java programs in blue j

---

### Post by lanceps on 2009-05-10
is eclipse a good ide

---

### Post by MontelEdwards on 2009-05-10
```
sudo aptitude install ubuntu-restricted-extras 
```

---

### Post by The Cog on 2009-05-10
First, install Suns java JDK. You can do this with the command **sudo aptitude install sun-java6-jdk**.

Second, Bluej has a .jar installer that runs on Linux.
[http://www.bluej.org/download/files/bluej-251.jar](http://www.bluej.org/download/files/bluej-251.jar) 
Just download the file and run the command **java -jar bluej-251.jar** 

However, although I really like the object bench and connectivity diagrams, I find the editor intolerable because of hte poor fonts. I recommend you install geany and use that as your editor. It has a compile button.

You really should find out how to compile without relying on an IDE though.

---

