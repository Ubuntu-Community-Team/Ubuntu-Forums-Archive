---
title: "Wubi Ubuntu &amp; Windows"
date: 2009-12-27
forum: New to Ubuntu
---

### Post by asnbd on 2009-12-27
hi,
 
i installed a 32bit ubuntu using wubi. so is ubuntu now run in windows? or it's still running on it's own(like a dual boot)
 
thanks.

---

### Post by Kevbert on 2009-12-27
Wubi Ubuntu is like an application that runs through Windows. If you decide that you no longer want Windows you would have to re-install Ubuntu from a CD. See [[COLOR="Red"]this[/COLOR]]("http://wubi-installer.org/faq.php#internals") for more information.

---

### Post by mlentink on 2009-12-27
Actually it is much more like dual-booting. You cannot ***run*** Ubuntu as an application within Windows (if you want to, you need something like VirtualBox), however you can ***install*** Ubuntu through an application within windows (Wubi).
The difference with a "real" dual boot situation is that Wubi creates a windows file which contains a virtual partition in which Ubuntu is installed. This makes it possible to remove Ubuntu from your disk simply by deleting the windows-file(s)

---

### Post by SecretCode on 2009-12-27
It's like dual booting in the sense that you can't run windows at the same time as wubi-ubuntu - when you boot to ubuntu there are no parts of windows running. 

But you still require the windows bootloader to get to it and the windows filesystem to hold  it.

---

### Post by asnbd on 2009-12-27
> **SecretCode said:**
> It's like dual booting in the sense that you can't run windows at the same time as wubi-ubuntu - when you boot to ubuntu there are no parts of windows running. 

But you still require the windows bootloader to get to it and the windows filesystem to hold  it.

hi,

so are you saying that windows and ubuntu can only one be running? if using wubi, which ubuntu is installed in windows, can i run windows and run ubuntu like an application?

btw, how do i start the installed ubuntu to run in windows?

thanks.

---

### Post by presence1960 on 2009-12-27
> **asnbd said:**
> hi,

so are you saying that windows and ubuntu can only one be running? if using wubi, which ubuntu is installed in windows, can i run windows and run ubuntu like an application?

**_btw, how do i start the installed ubuntu to run in windows?_**

thanks.

see #10 & #11 [here]("https://help.ubuntu.com/community/Wubi")

---

### Post by asnbd on 2009-12-27
hi,

i'm trying to make my imac triple boot(mac, linux, windows).

so which is the better way to install ubuntu? using wubi or install from a .iso dvd

thanks.

---

### Post by mlentink on 2009-12-27
You cannot run Ubuntu from inside Windows except as a virtual machine, using something like VMWare, VirtualBox, or for that matter, Parallels from within OSX.
Otherwise, you cannot have two OS's open at the same time.

It is entirely possible to triple-boot Windows, OSX and Ubuntu (or other GNU/Linux distro's)

---

### Post by SecretCode on 2009-12-27
> **asnbd said:**
> so are you saying that windows and ubuntu can only one be running? 
**YES**

> **asnbd said:**
> if using wubi, which ubuntu is installed in windows, can i run windows and run ubuntu like an application?
**NO**, I thought I said that very clearly
(eta: as did mlentink - crosspost!)

> **asnbd said:**
> btw, how do i start the installed ubuntu to run in windows?
YOU CAN'T. The only way to get this working would be to use a virtualisation program like VirtualBox or VMware.


> **asnbd said:**
> i'm trying to make my imac triple boot(mac, linux, windows).

so which is the better way to install ubuntu? using wubi or install from a .iso dvdWUBI is designed for quick testing of Ubuntu. You should plan to install Ubuntu to a partition.

But you should do a lot of reading first - there are plenty of articles on the web about triple-booting - as you don't seem to be understanding the basics very well yet. (For example - a WUBI install is *also* done from a .iso CD/DVD the same as a full install. It's whether you install into onto its own partition that makes the difference.)

Make sure you read about Grub2, and make sure you back up your entire system (e.g. using Clonezilla), because there's a high chance of messing something up.

Actually I recommend you try out virtualbox - it's a great way to experiment with all these concepts without trashing your main machine.

---

### Post by mlentink on 2009-12-27
> **SecretCode said:**
> 
Actually I recommend you try out virtualbox - it's a great way to experiment with all these concepts without trashing your main machine.

+1!

I use VB to try out new versions of Ubuntu, other distro's and OS's.

---

### Post by asnbd on 2009-12-28
thanks. appreciated.
 
ed

---

