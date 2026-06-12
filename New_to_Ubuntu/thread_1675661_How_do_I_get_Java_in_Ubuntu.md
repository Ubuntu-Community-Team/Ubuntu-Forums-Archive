---
title: "How do I get Java in Ubuntu?"
date: 2011-01-25
forum: New to Ubuntu
---

### Post by Ranger_Joe on 2011-01-25
Hey Everyone,
A new semester just started for college students everywhere. As for me, I just started my first computer science class. I don't know much about development, as I only know web languages and my php is quite choppy. 

Anyway, my entire class is on Java. I will be doing quite a bit of coding from scratch in the text editor (gedit) and running the programs I write in the terminal.

The problem is this: The prof handed out a CD with the latest version of Java on it. The CD had everything we need... compiler, etc. However, this CD was of course for the Windows students. 

I am the only one in my class using Ubuntu or any Linux distro for that matter. Can someone tell me what all I need to write Java applications on my Maverick Meerkat laptop?

*If you could give me a terminal command for everything... that would be great! Thanks!

---

### Post by oldos2er on 2011-01-25
[http://java.dzone.com/articles/sun-java-6-ubuntu-1004-1010?utm_source=am6_feedtweet&utm_medium=twitter&utm_campaign=toya256ForRSS](http://java.dzone.com/articles/sun-java-6-ubuntu-1004-1010?utm_source=am6_feedtweet&utm_medium=twitter&utm_campaign=toya256ForRSS)

---

### Post by Ranger_Joe on 2011-01-25
Oldos,
You're awesome. This is what I did:

```
add-apt-repository ppa:sun-java-community-team/sun-java6
apt-get update
apt-get install sun-java6-jdk
update-java-alternatives -s java-6-sun
```

I should be good to go right?

---

### Post by deathbysushi on 2011-01-26
Yes, you should. If you want a nice IDE, I'd recommend Eclipse. Otherwise, learn to use emacs or vi, they will be useful when you have other programming classes! Good luck in school!

---

### Post by muteXe on 2011-01-26
Netbeans is also pretty good.

---

