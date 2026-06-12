---
title: "Generic or Server Kernel?"
date: 2010-06-01
forum: New to Ubuntu
---

### Post by webwiller on 2010-06-01
Hi all,
reading about kernel I learned that a common generic kernel can read only up to 2gb of RAM and if you have more RAM on your system you would need to install the kernel Server version, which will allow your system to use more than 2gb of RAM.

I found these commands which worked for 9.04 karmic koala :

```
sudo apt-get install linux-server
```

```
sudo apt-get install linux-restricted-modules-server

```
```
sudo apt-get install linux-headers-server
```

This way I did have both generic and Server kernel on my system. Now I upgraded to lucid 10.04 and I tried the same way but also if I'm able to install two of the three packages( the middle one I'm not able to find it), I cant find them on the grub sceen as Server kernel, I keep having only the Generic one.

Any clue?

Thx in advance! ;)

---

### Post by sydbat on 2010-06-01
Some of what you are saying is incorrect. 32bit will only be able to utilize ~3.5GB of RAM. 64bit can utilize way more (at least 128GB if I remember correctly).

Using the server kernel will allow more RAM to be recognized via PAE for 32bit only.

Therefore, if you are running 64bit Ubuntu, you do not have to do anything. If you are running 32bit, then you can use the server kernel.

As for your question, have you updated grub? [https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

EDIT - Found [this in another thread]("http://ubuntuforums.org/showpost.php?p=9393649&postcount=5"). Might be helpful.

---

### Post by webwiller on 2010-06-01
I have a 32bit system in a machine with more than 4gb of RAM, that's why I need server kernel. But how do I update grub exactly? I keep not finding the server option at grub boot splash sceen.

---

### Post by da burger on 2010-06-01
To update grub log into ubuntu, open a terminal and run ```
sudo update-grub
```
Angus

---

### Post by migs73 on 2010-06-01
Try this link once your Grub is updated; [https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)

It worked for me, now seeing 3.8Gb of my 4Gb installed.
Check your processor can use PAE though. Most newer ones can.

---

