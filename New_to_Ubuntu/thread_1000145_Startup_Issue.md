---
title: "Startup Issue"
date: 2008-12-02
forum: New to Ubuntu
---

### Post by J8218 on 2008-12-02
I downloaded the version 8.10 .iso file and created an install dvd.  Installed Ubuntu on a Windows XP machine in dual boot mode.  Windows still boots properly.  When I boot to Ubuntu I am placed in a "dos" screen which displays:
Loading, please wait...
Linix ubuntu 2.6.27-7-generic #1 SMP Friday Oct 24 06:42:44 UTC 2008 i686

various copyright and documentation messages.

And then left at this prompt:

ubuntu@unbuntu:~$

Now what?

Dell Prescision T3400 2GB digital monitor

Thanks, Jon

---

### Post by adult swim on 2008-12-02
did you install ubuntu server edition?

---

### Post by J8218 on 2008-12-02
I did  not think so, is there a way to tell looking at the dvd?

---

### Post by adult swim on 2008-12-02
what does it say when  you type in ```
startx
``` and press enter?

---

### Post by J8218 on 2008-12-02
It is the desktop version "ubuntu-8.10-desktop-i386.iso" 715,592 KB.

I ran the CD test and had no issues.

The install had no issues.

I think I will try the 8.04 version.

---

### Post by J8218 on 2008-12-02
Primary device is not PCI
(EE) No devices detected.

Fatal server error:
no screens found
giving up

---

### Post by adult swim on 2008-12-02
what kind of video card do  you have?

---

### Post by slinkey1981 on 2008-12-02
My fresh install of 8.04 does this too. I have to enter

```
sudo gdm start
```

for it to load the desktop....


EDIT: Wow, I forgot to press send, and by the time I figured it out, you'd gone past the point I was trying to help. Sorry.

---

### Post by J8218 on 2008-12-02
I have two Dual nVidia,NVS 290, 256MB dual DVI, Graphics Cards.  Using the "Primary device is not PCI" I found:

Now I need to find out how to update the xorg.conf 


QUOTE=iSTRONG;6087050]i fixed my problem by adding
BusID "XX:YY:Z"
to the device section of my xorg.conf
XX:YY:Z can be obtained through the command lspci (find primary video device PCI address)

Basically, the problem is that when you have 2 video cards, xserver doesn't make an assumption about which one is the primary one. So you have to specify it in xorg. conf.

Hope that helps someone.[/QUOTE]

---

### Post by Nosss on 2008-12-02
> **adult swim said:**
> what does it say when  you type in ```
startx
``` and press enter?

Ok, I really am sorry I feel so stupid on Ubuntu cos i dnt kno how to do *anything*. Above you said to type in startx..where do u type that in? Because literally i have problem after problem wen i try and install Ubuntu. This is on Vista, on an Asus, basically first off it came up with the "/bin/sh cant access tty"..i got around that though then it came up with "cant read sid from /proc/1/stat" but it carries on attempting to start ubuntu so i didnt bother looking into it, then finally something stops me "fatal error no screens found" now i have, *NO* idea how to fix this. Please tlk to me like im a kid step by step because that is really what i am on Ubuntu but i really want to learn so try to give me a chance.

Nos

---

### Post by J8218 on 2008-12-03
I was not able to edit (gedit xorg.conf) the xorg.conf file because the screen issue prevented gedit from working.  By removeing the 2nd adapter in windows (this is a dual boot XP install), powering off the box and removing the second adapter, Ubuntu is continuing the installation process.  After the installtion is complete I will try re-installing the card.

Thanks for the help.

---

### Post by oldos2er on 2008-12-03
> **J8218 said:**
> I was not able to edit (gedit xorg.conf) the xorg.conf file because the screen issue prevented gedit from working.

 You need to use a CLI editor like nano.

---

