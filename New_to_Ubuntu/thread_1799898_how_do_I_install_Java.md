---
title: "how do I install Java?"
date: 2011-07-08
forum: New to Ubuntu
---

### Post by Ditchdoc7893 on 2011-07-08
Hey guys, this may sound like a major beginner question, but how do I install Java?

---

### Post by howefield on 2011-07-08
This page should help you.

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

If you want Suns java (as opposed to opendjdk), enable the partner repository, reload your software sources and install sun-java6-jre sun-java6-fonts and sun-java6-plugin

---

### Post by mike555 on 2011-07-08
same way you should install anything in Ubuntu , in your package manager, type java in search box.......... Ubuntu comes with java installed unless you want a different version .

---

### Post by raja.genupula on 2011-07-08
just type java in terminal then it will give you some versions among those choose any jdk version ......

---

### Post by shibu_sawyer on 2011-07-08
> **Ditchdoc7893 said:**
> Hey guys, this may sound like a major beginner question, but how do I install Java?

synaptic manager->type jdk in quick search->select openjdk-6-jdk install thats all.

---

### Post by swaprava on 2011-07-08
enable partner sources in your sources.list, i.e. uncomment the two following lines in /etc/apt/sources.list

```
deb http://archive.canonical.com/ubuntu lucid partner
deb-src http://archive.canonical.com/ubuntu lucid partner

```


and then do 
```
sudo apt-cache search java
```

you'll find 

```
sun-java6-jdk
```

install that! make this the primary by putting priority over any other version you have already installed.

---

### Post by Ditchdoc7893 on 2011-07-08
Thanks guys for your responses.  As you all said, Java is available in the software center, and I have downloaded it.  I guess I should have specified as to what I'm after in the subject, but I'm wanting to install something that will allow me to play online backgammon (not for money, just free for fun), as in be able to play other people live (not the proverbial computer as is easily accomplished by downloading the backgammon app via the software center).  Anybody have any suggestions other than Pogo?  I tried it without success with multiple browsers (ie. Chrome, Firefox).  Any help appreciated!

---

