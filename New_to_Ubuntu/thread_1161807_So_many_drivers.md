---
title: "So many drivers"
date: 2009-05-17
forum: New to Ubuntu
---

### Post by Duskao on 2009-05-17
Ok, I have been using Ubuntu for a little while now and I assumed I would catch on to all the different video drivers and how to use/install them. So could someone please enlighten me on the different video drivers in ubuntu. How to get them, and how to install them. What the default is with Ubuntu. I'm mostly talking about Ati, but you can throw in nvidia as well if you would like, just try to separate them. 
Here is what I know, or think I know, please correct me if I'm wrong. 

fglrx = Ati official closed source driver (this one I know)

Radeon/RadeonHD = community open soure driver

mesa = another open source driver????

Thank you so much guys.

---

### Post by diablo75 on 2009-05-17
Here's all I know:

The first place to check for drivers available is in System>Administration>Hardware Drivers.  If you see something in here that can be enabled, then hooray beer!  If not, then you'll likely not want to do anything unless you feel like going on a quest.

An older alternative that I'm pretty sure isn't recommended so much these days (at least not for Intrepid or Jaunty) is to use the 3rd party program Envy to install the best drivers for you.  But I have a feeling this is what Hardware Drivers actually does for you now.

I recently bought a laptop that has an ATI chipset in it which I kind of wish wasn't the case, but you lay in the bed you make.  Anyway, Compiz runs pretty smooth, but there are minor glitches.  There are no drivers available to me for enableing/disabling in Hardware Drivers and when I asked the forums if there were alternatives available, I was told to "continue using the open-source drivers you already have working".  I take that like the slogan for Guinness:  Good things come to those who wait.  At least that's what the situation is with ATI.  

As for nVidia, I've had GREAT luck in almost every nVidia card and the drivers made available via Hardware Drivers in the System menu.

---

### Post by Duskao on 2009-05-17
You seem to be in a similar situation as me, but I am using fglrx in 9.04 because I can. Your card probably is in the legacy list now. But my question still stands. I need clarification of the different drivers and how to get them and what the default is.

---

### Post by Peter09 on 2009-05-17
If you do 

```
lshw -C video
```
you can see the driver that is being used by your card, and also the cards name and type. Do a search on Google for your card and see what drivers are in use for Ubuntu

---

### Post by Duskao on 2009-05-17
Thanks again, I will have to remember that. But what is mesa? How do you install it? Do you install Radeon/RadeonHD driver through synaptic package manager?

---

### Post by Peter09 on 2009-05-17
Have you seen this thread?

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by Duskao on 2009-05-17
I have, but it seems quite dated, and alot of it is kinda mumbo-jumbo to a newbie like me. Plus the last ubuntu version it is talking about is 8.04. I'm not sure if it would have any bearing on 9.04, but like I said, I'm still quite new.

---

