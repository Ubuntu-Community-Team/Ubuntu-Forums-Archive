---
title: "Installing Java Runtime Environment"
date: 2010-04-14
forum: New to Ubuntu
---

### Post by Mykk on 2010-04-14
Could some one point me in the direction of some instructions to do this? I had a look on google and couldnt find anything that i thought was of relevance. 

I want to play runescape whilst at work (just kidding) :)

---

### Post by ConfusedUser on 2010-04-14
Same here, i looked up the Java.com page for Ubuntu and there are a whole load of terminal based instructions I have to type in, but it fails when I get to the bit where I am supposed to type in teh version.

All I wanted to dio was ensure that i had the latest version of Java on my machine - is there no easy straightforward way of installing without having to do about 15 different steps on the terminal?  Otherwise it all seems a bit 1980s to me.

---

### Post by philinux on 2010-04-14
> **Mykk said:**
> Could some one point me in the direction of some instructions to do this? I had a look on google and couldnt find anything that i thought was of relevance. 

I want to play runescape whilst at work (just kidding) :)

Seeing as your running lucid you need the openjdk apps from synaptic and the icedtea-plugin.

```
sudo apt-get install openjdk-6-jre openjdk-6-jre-lib icedtea-plugin
``` I'm on karmic right now so I cant double check this.

Background on this here. [http://ubuntuforums.org/showthread.php?t=1406969](http://ubuntuforums.org/showthread.php?t=1406969)

---

### Post by Mighty_Joe on 2010-04-14
> **philinux said:**
> Seeing as your running lucid you need the openjdk apps from synaptic and the icedtea-plugin.

If one is running Lucid, Sun Java is in the partner repository. See the [release notes]("http://www.ubuntu.com/getubuntu/releasenotes/1004#Sun%20Java%20moved%20to%20the%20Partner%20repository")
If one is running Karmic, Sun Java is in the main repository, but frozen at an older version.  [Here ]("http://sites.google.com/site/easylinuxtipsproject/java")are instructions for installing the latest version.

[QUOTE=ConfusedUser]
Otherwise it all seems a bit 1980s to me. 
[/QUOTE]

The console is extremely powerful tool in Unix. Much more so than in Windows. Ignore it and you are missing out.  
Not to mention it is much easier to copy and paste a couple of commands than wade through dozens of "click here, drag here, scroll down and look for the tab. . ." instructions.

---

### Post by Paqman on 2010-04-14
> **ConfusedUser said:**
> is there no easy straightforward way of installing without having to do about 15 different steps on the terminal?  Otherwise it all seems a bit 1980s to me.

There sure is. Go to System > Admin > Synaptic and install the package "icedtea-plugin" as mentioned above. There's no real need to be using the terminal for anything as routine as installing software. Unfortunately Linux's geeky roots and the millions of different distros in the wild mean that a lot of the instructions out there on the internet will give you terminal instructions, often not terribly good ones. Debate rages about whether this is the way it should be in 2010.

---

### Post by Mykk on 2010-04-15
Ok, so i tried installing the icedtea plugin as suggested but it flags up this error message and doesn't let me install it:


An Error Occurred

E: tzdata: subprocess installed  post installation script returned error exit status 1

What on earth is that trying to tell me? :|

---

### Post by Paqman on 2010-04-15
Urk, that doesn't look good. Try completely removing tzdata and reinstalling it. There seems to be a package called tzdata-java as well, you might want to install that (bit of a stab in the dark, i'm afraid...)

---

### Post by Mykk on 2010-04-15
Somehow, i dont know exactly how, i have managed to resolve this and install icedtea. Cheers for your help :)

---

