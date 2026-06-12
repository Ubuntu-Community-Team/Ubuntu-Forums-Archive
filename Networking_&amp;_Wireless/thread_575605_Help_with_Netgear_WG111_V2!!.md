---
title: "Help with Netgear WG111 V2!!"
date: 2007-10-14
forum: Networking &amp; Wireless
---

### Post by Lucaio on 2007-10-14
Right, well I am new, which you can probably see as this is my first post.

I have just installed Linux Ubuntu today and I can't get to seem to get my wireless adaptor working (Netgear WG111 v2).

I tried looking round but I get confused by all the jargon that is getting used.

Could someone please provide a simple way to get my adaptor working so I can browse the net??

:)

---

### Post by Jose Catre-Vandis on 2007-10-14
This probably the best thread on the forum about this adapter
[http://ubuntuforums.org/showthread.php?t=329299](http://ubuntuforums.org/showthread.php?t=329299)
In simple terms you have to use your windows drivers (on the CD or download) and "wrap" them up in "ndiswrapper" to make them work for Linux. Alternatively, you can use the built in driver in the linux kernel if on Feisty (7.04) but this doesn't work for everyone. Probably ndiswapper is more successful.

Come back if/when(!) you get stuck

---

### Post by Lucaio on 2007-10-14
Right well I have downloaded NDIDSWRAPPER but I don't have a clue what to do with it.

Where do I type in all this code that I keep reading about??

---

### Post by Jose Catre-Vandis on 2007-10-14
Open a terminal! (like command prompt in windows)

Main Menu > Accessories > Terminal

Remember to use "sudo" to carry out commands that require root (admin) access

---

### Post by Lucaio on 2007-10-14
Ah thanks!

Sorry, if I'm asking silly questions! But it's nice to join a friendly and helpful community. :)

---

### Post by Jose Catre-Vandis on 2007-10-15
No worries, keep asking :)

One day, the "Terminal" will become your best friend ;)

---

### Post by Lucaio on 2007-10-26
How do I login to the root user area?

I need to log in to change the permissions on my main drive.

---

### Post by Jose Catre-Vandis on 2007-11-06
You have probably figured this by now, but with Ubuntu you can use the sudo command to temporarily give you root priveliges. For example
```
fdisk -l
```
gives you nothing but if you
```
sudo fdisk -l
```
and type in your password, you will get lots of info about your system, because you are running as root/administrator

---

