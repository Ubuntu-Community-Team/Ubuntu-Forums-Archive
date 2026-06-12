---
title: "limewire and java"
date: 2009-03-27
forum: New to Ubuntu
---

### Post by lil_kid1333 on 2009-03-27
Well 1st of all I can't seem to install Limewire cause it says only one software management tool is allowed to run at once and I dont even got nothing running :S

I also want to install Java I downloaded a .bin file the latest and clicked it but nothing happens that no software is installed

Can someone help? :( thanks

p.s damn I got like 3 months with ubuntu and it's hard to get to know everything but it'll be worth it. I already know some things. I think about back then and realize how much I've learned and it makes me happy and most part cause of you guys. Thanks :)

---

### Post by |Mitch| on 2009-03-27
You can get Java through the ubuntu-restricted-extras, search in Synaptic 

or 

open the Terminal, and execute the following command:

         sudo apt-get install ubuntu-restricted-extras

---

### Post by lil_kid1333 on 2009-03-27
> **|Mitch| said:**
> You can get Java through the ubuntu-restricted-extras, search in Synaptic 

or 

open the Terminal, and execute the following command:

         sudo apt-get install ubuntu-restricted-extras

didnt work this came up

chick3n@chick3n-desktop:~$ sudo apt-get install ubuntu-restricted-extras
[sudo] password for chick3n: 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
chick3n@chick3n-desktop:~$

wtf I tried installing via the Add/Remove thing and it didn't let me this came up

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by |Mitch| on 2009-03-27
just run that command in the terminal,

sudo dpkg --configure -a

---

### Post by linux_tech on 2009-03-27
try typing ```
sudo dpkg --configure -a
```
in the terminal to fix that

---

### Post by lil_kid1333 on 2009-03-28
ok i think i got it :) thanks

well I got it but its not the latest which is update 13 :S I got update 10

edit: im following these instructions on java it says to type in su on the terminal and it ask 4 my password and I type it in and it says authentication failure O.o

---

### Post by |Mitch| on 2009-03-28
sudo apt-get update

---

### Post by lil_kid1333 on 2009-03-28
ok i got limewire and I didn't read nothing about java being updated but it's cool as long as I got limewire working is all cool

---

### Post by |Mitch| on 2009-03-28
why use limewire? I'd much rather use Frostwire [www.Frostwire.com](www.Frostwire.com)

---

### Post by presence1960 on 2009-03-28
> **lil_kid1333 said:**
> ok i think i got it :) thanks

well I got it but its not the latest which is update 13 :S I got update 10

edit: im following these instructions on java it says to type in su on the terminal and it ask 4 my password and I type it in and it says authentication failure O.o

Here is what I have :

> raz@raz-desktop ~ $ java -version
java version "1.6.0_14-ea"
Java(TM) SE Runtime Environment (build 1.6.0_14-ea-b01)
OpenJDK 64-Bit Server VM (build 14.0-b10, mixed mode)

Here is how I got it:

[http://ubuntuforums.org/showpost.php?p=6791349&postcount=59](http://ubuntuforums.org/showpost.php?p=6791349&postcount=59)

I have to give zika the credit for turning me on to this.

---

