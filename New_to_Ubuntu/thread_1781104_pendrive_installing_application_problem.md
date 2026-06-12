---
title: "pendrive installing application problem"
date: 2011-06-13
forum: New to Ubuntu
---

### Post by BiosDaddy on 2011-06-13
Hi, I am new in the forum.
I have been working with Ubuntu Natty for a while, and I wanted to keep working with it in my job, so I made a USB flash memory stick with Ubuntu 11.04 and it works fine.
However I need an application called QtQr, that is working fine in my PC, but when I try to install it in the pendrive, it doesn't work because of a missing library or something like that.
This application works in python, I was trying to install all the dependencies but without success.
Is there anybody who can help me.

---

### Post by jake.anq on 2011-06-13
Hi
This should do it.
```
sudo apt-get install python-zbar qrencode
```
After running, re-try installing QtQr.

---

### Post by BiosDaddy on 2011-06-13
Hi jake, thanks for the reply.
I already tryed your suggestion, but a message appears telling me that Package pytho-zbar and qrencode is not available.
I've already added launchpad address to ubuntu's software center.
but it still not found the packages.

Is this problem could be a python's missing module??

---

### Post by jake.anq on 2011-06-13
Hi
I would suggest trying with synaptic manage manager.  If this still fails, double-check your Internet connection.

---

