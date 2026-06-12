---
title: "How to update Java"
date: 2011-06-08
forum: New to Ubuntu
---

### Post by new-2-linux on 2011-06-08
I have downloaded Java self-extracting file for Linux off [www.java.com](www.java.com) and it downloads as a BIN file. What do I do from there

---

### Post by Paqman on 2011-06-08
The best place to get your software on Ubuntu is the Ubuntu Software Centre. Open it up and search for "java".

---

### Post by new-2-linux on 2011-06-08
I have got Java off of there but then it isn't the most recent one because I still can't play any games and on the Java website i verify my Java and it says I'm Java 6 update 25 where the most recent is update 26

---

### Post by Paqman on 2011-06-08
The update should be rolled out to you as part of your normal system updates if it's important or security-related. What games are you having trouble with?

---

### Post by new-2-linux on 2011-06-08
I'm trying to have a go at the classic version of minecraft and also the racing games on MiniClip

---

### Post by new-2-linux on 2011-06-08
I just found out it is Update 20 that I have not 25

---

### Post by ajgreeny on 2011-06-08
I suspect you may be running the openjdk/openjre and not sun-java packages, which seem to be much less troublesome for some applications, and websites.

Those sun-java packages are all on the canonical.archive repos, so check your software-sources and make sure they are enabled and you should be able to search and find the sun-java versions.

PS:  What version of ubuntu are you running?

---

### Post by new-2-linux on 2011-06-08
> **ajgreeny said:**
> I suspect you may be running the openjdk/openjre and not sun-java packages, which seem to be much less troublesome for some applications, and websites.

Those sun-java packages are all on the canonical.archive repos, so check your software-sources and make sure they are enabled and you should be able to search and find the sun-java versions.

PS:  What version of ubuntu are you running?
Ubuntu 10.10

---

### Post by new-2-linux on 2011-06-08
> **ajgreeny said:**
> I suspect you may be running the openjdk/openjre and not sun-java packages, which seem to be much less troublesome for some applications, and websites.

Those sun-java packages are all on the canonical.archive repos, so check your software-sources and make sure they are enabled and you should be able to search and find the sun-java versions.

PS:  What version of ubuntu are you running?

Where do you go for the Software-sources

---

### Post by madmax75 on 2011-06-08
Hi,

this is the method I use. First you give some commands in the Terminal window (Applications -> Utilities -> Terminal), then switch to the Synaptic package manager (or Software Center). Then you can check the Java version you have again in the Terminal window.

**In the Terminal**

Add the Partner repository to the software sources list:
```

sudo add-apt-repository "deb http://archive.canonical.com/ maverick partner"
```

Then update the software sources list:

```
sudo apt-get update
```

**Synaptic/Software Center**

Remove entirely the *OpenJDK* and *IcedTea*-plugins.

Search for and install the *Sun Java* components (NOTE the sun-java-6-plugin, otherwise Java won't work in your internet browser):

sun-java6-jre
sun-java6-plugin 
sun-java6-fonts

**In the Terminal (optional)**

Check your Java version:

```
java -version
```

It should say something like Sun Java and so on, if it worked.

---

### Post by new-2-linux on 2011-06-08
Thank you. It's now working.

---

