---
title: "majoong tiles for linux"
date: 2011-02-28
forum: New to Ubuntu
---

### Post by ECET on 2011-02-28
hello all....I just found this program which I love to play called majoong tiles. I got the version downloaded for linux, but...being still a noob can't figure out how to install it. As all of you know, there is no "exe" file for me to execute,so....how to do it....I have included what "folders" are in the download. Please help me understand what I need to do...Thanks,.....

/home/michael/Desktop/ivory/Help
/home/michael/Desktop/ivory/Layouts
/home/michael/Desktop/ivory/TileSets
/home/michael/Desktop/ivory/BrowserLauncher2.jar
/home/michael/Desktop/ivory/formsrt.jar
/home/michael/Desktop/ivory/ivory
/home/michael/Desktop/ivory/j3dcore.jar
/home/michael/Desktop/ivory/j3dutils.jar
/home/michael/Desktop/ivory/j3d-vrml97.jar
/home/michael/Desktop/ivory/libj3dcore-ogl.so
/home/michael/Desktop/ivory/libj3dcore-ogl-cg.so
/home/michael/Desktop/ivory/license.txt
/home/michael/Desktop/ivory/log4j.jar
/home/michael/Desktop/ivory/mahjongg.jar
/home/michael/Desktop/ivory/readme.txt
/home/michael/Desktop/ivory/vecmath.jar

---

### Post by Witch Lady on 2011-02-28
No info on installation in readme.txt?

---

### Post by ECET on 2011-02-28
nope

---

### Post by Chronon on 2011-02-28
It's a java program, so presumably you just need to run the correct .jar with the java VM.  The readme doesn't provide any instruction?  How about the website?

If you can't find any info, then my first guess would be to try

```
java -jar /home/michael/Desktop/ivory/mahjongg.jar
```

---

### Post by ECET on 2011-02-28
I tried your code...thanks, but it didnt work either...Ill grab my ubuntu tricks and hacks book and see if it can help...if anyone else has any ideas, id appreciate em!!!....thanks Chronon and Witch Lady for your posts and possible help.....

---

### Post by SoFl W on 2011-02-28
How about playing the one found in the application/software center?  It will install itself.

Applications-> Software Center-> Games-> search for Mahjong

---

### Post by ECET on 2011-02-28
yea...its ok...but i want a more robust game...i have one for M$, but wine will not let it play....in fact I have 3 and none of them work.....so I just did a google search and found a couple free downloads for linux and wanted to try em out....I'm just not sure how to "execute" a program in linux....still learning, but enjoying!.....

---

### Post by Chronon on 2011-02-28
Hi.  

I just downloaded the tarball and the file named "ivory" is a script that checks to make sure Java is installed, adds the directory to the CLASSPATH and then launches the program.  Try running that instead.

---

### Post by oldos2er on 2011-03-01
> **ECET said:**
> I tried your code...thanks, but it didnt work 

Can you post the terminal output from the command Chronon gave you? Do you have Java installed? And can you post a URL to the game? Thanks.

---

### Post by Chronon on 2011-03-01
oldos2er, you can download it here:
[http://ivorymahjongg.com/#releases](http://ivorymahjongg.com/#releases)

---

### Post by oldos2er on 2011-03-01
From within the ivory folder, run ./ivory

---

