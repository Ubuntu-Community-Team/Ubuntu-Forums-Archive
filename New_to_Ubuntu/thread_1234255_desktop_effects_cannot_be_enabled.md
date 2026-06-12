---
title: "desktop effects cannot be enabled"
date: 2009-08-07
forum: New to Ubuntu
---

### Post by ekansh on 2009-08-07
hello people.. I am a total newbie to ubuntu world ..and forum.. If i have placed my thread/reply, shift to where it belong
(i checked for this thread before  .. but  i was unable to post my querry there)

I have an AMD 2800 + machine with K8S MX mother board of asus and Ubuntu 8.04
Problem : I can not enable graphics effect
on terminal when I typed
lspci | grep VGA
the out put i got is this
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

Cant I enable graphic effects.. Please I really want to enable them.. I dont want compiz fuzion  but at least some graphic effects

---

### Post by overdrank on 2009-08-07
Hi and welcome, the [SiS] 661/741/760  graphics do not work well with the desktop effects. You may look [here]("http://ubuntuforums.org/showthread.php?t=958967&highlight=SiS+graphics") for some help.

---

### Post by rcayea on 2009-08-07
Sounds to me that the card just won't let you. When I had a not-so-good graphics card and when I tried to do effects, I couldn't. It is almost like the OS recognizes that your graphics card can't handle it.

---

### Post by Liolikas on 2009-08-07
Get read 3D card (nvidia or ati one). At least used and cheap from ebay.

---

### Post by Buuntu on 2009-08-07
System > Administration > Hardware Drivers.
Activate the latest driver and see if that fixes it.  You might have to restart.

---

### Post by ekansh on 2009-08-08
> **Buuntu said:**
> System > Administration > Hardware Drivers.
Activate the latest driver and see if that fixes it.  You might have to restart.

As u said i opened the hardware driver window..
but the box is empty. i mean i was expecting some list of drivers there.. but nothing is there totally empty.. and the box also doesnt give much facility to add some thing(driver) in it

---

### Post by Buuntu on 2009-08-08
What is the actuall error message you get when trying to enable effects?  I'm guessing your going to System > Preferences > Appearance and then the Visual Effects tab right?

---

### Post by 3rdalbum on 2009-08-08
> **Buuntu said:**
> What is the actuall error message you get when trying to enable effects?  I'm guessing your going to System > Preferences > Appearance and then the Visual Effects tab right?

The error message is "Desktop effects cannot be enabled".

The SiS graphics is most likely to be the problem. Not only are they weak, but there is poor support for them on Linux. The vendor needs to release some specifications in order for us to work on writing drivers.

---

### Post by ekansh on 2009-08-08
> **Buuntu said:**
> What is the actuall error message you get when trying to enable effects?  I'm guessing your going to System > Preferences > Appearance and then the Visual Effects tab right?


I did-> right clicked on desktop back -> change desktop back ground and then visual effects .. the same as u said ..
if in case u want to see my XORG.conf file.. i am posting it with this reply...
the file is very strange and has minimum configuration setting

and i edit it to obtain the resolution of 1024 X 768
thanks for all the help

---

