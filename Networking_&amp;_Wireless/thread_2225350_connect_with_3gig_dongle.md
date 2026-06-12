---
title: "connect with 3gig dongle"
date: 2014-05-21
forum: Networking &amp; Wireless
---

### Post by Fred_Evans on 2014-05-21
Hello All
I have installed ubuntu 10. something ( the suggested system for linuxcnc)

Please tell me how i can connect to the internet using a vodacom 3 gig dongle. 
Vodacom says the version does not support linux

Alternately - Is it possible to connect to the internet and what do i need 

I am in south africa

best regards

fred evans

---

### Post by Lars Noodén on 2014-05-21
First, it would be best if you [use a version that is supported](https://wiki.ubuntu.com/Releases).  So unless your 10.x system is only a server, it is out of date and you should switch to 14.04.  If the UI is dislike there are options around that too.  

About the 3G dongle, I got mine working by adding the following to /etc/modules and rebooting:

```

option
usb_wwan
usbserial
usb_storage

```

But first bring the system up to date, if it is a desktop.

---

### Post by Fred_Evans on 2014-05-21
thank you Lars for your reply. I am not a computer geek- so sorry what is a "UI"
and where do I add this code to?
I am using a laptop with Ubuntu as an operating system because i am trying to
learn CNC machining with Linuxcnc. So because i will be working on the Linux computer 
it would be great to connect to the forums with the same machine.
My friends say that the latest versions of Ubuntu do not perform as well with linuxCNC
and i would be better off not to upgrade. please help
best regards

fred

---

### Post by Lars Noodén on 2014-05-21
UI is User Interface.  Some like Unity, the new default interface, others prefer the MATE or Xfce interfaces. 

You can edit with the [nano](http://manpages.ubuntu.com/manpages/trusty/en/man1/nano.1.html) text editor, it is functional yet very easy.  First, make a backup of the original file. 

```

sudo cp /etc/modules /etc/modules.orig
sudo nano /etc/modules

```

Then add those lines to the end of that file.

---

### Post by Fred_Evans on 2014-05-21
thanks-- my mind is blown-- i will try and get someone to show me how
Lars thank you very much- i really appreciate your help and will get a programmer 
to do the modification
Is this nano thing like gedit?
regards
fred

---

### Post by Lars Noodén on 2014-05-21
Yes, you could use gedit instead if you like that.

```

gksudo gedit /etc/modules

```

Normally you don't have to touch those kind of files though.

---

