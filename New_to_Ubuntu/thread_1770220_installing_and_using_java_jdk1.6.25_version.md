---
title: "installing and using java jdk1.6.25 version"
date: 2011-05-28
forum: New to Ubuntu
---

### Post by amitpokhrel on 2011-05-28
hi i would like to install and use java on my ubuntu system. I have been using it in windows but i would like to use it in ubuntu. can anyone tell me how to install java and what are the basic commands to run it!!!

---

### Post by webofunni on 2011-05-28
I am not sure about the version. But 

```

apt-get install sun-java6-jdk

```

should install jdk 

Below are the other packages available. 

> sun-java6-fonts - Lucida TrueType fonts (from the Sun JRE)
sun-java6-jre - Sun Java(TM) Runtime Environment (JRE) 6 (architecture independent files)
sun-java6-demo - Sun Java(TM) Development Kit (JDK) 6 demos and examples
sun-java6-plugin - The Java(TM) Plug-in, Java SE 6
sun-java6-javadb - Java(TM) DB, Sun Microsystems' distribution of Apache Derby
sun-java6-jdk - Sun Java(TM) Development Kit (JDK) 6
sun-java6-bin - Sun Java(TM) Runtime Environment (JRE) 6 (architecture dependent files)
sun-java6-source - Sun Java(TM) Development Kit (JDK) 6 source files


---

### Post by wog on 2011-05-29
The latest Java in the repositories is 1.6.24

alien lists jre-6u25-linux-i586-rpm.bin as an unknown file type.
running the non-rpm bin only produces a directory with the files, but no way of knowing where to put them.

---

### Post by webofunni on 2011-05-29
wog, is that a solution or question ? 

jre-6u25-linux-i586-rpm.bin is a binary file not rpm.

---

### Post by wog on 2011-05-30
That was more of a clarifying question rather than a solution. 

I had hoped to help someone else not go down the same blind alley I had, especially in hopes of finding a better answer.

If I am in error in providing this information, then I apologize, and will go off and start my own question thread.

Please let me know.

---

### Post by webofunni on 2011-05-30
I understood now. But it was confusing :-). Yes, new java is not there in repo. I guess extracting rpm from that binary and converting that to deb package is seems to be a good idea.

---

### Post by amitpokhrel on 2011-05-30
> **webofunni said:**
> I understood now. But it was confusing :-). Yes, new java is not there in repo. I guess extracting rpm from that binary and converting that to deb package is seems to be a good idea.
I don't how i can make it work.. can u please tell me the commands of process to achieve this... thanks

---

### Post by jtarin on 2011-05-30
The version in Synaptic is fine.I have several mainline Java apps that work without problems. Your only going to do needless work trying to install the newest.
If you have to......[http://www.youtube.com/watch?v=fknHQlrNN7g](http://www.youtube.com/watch?v=fknHQlrNN7g)

---

