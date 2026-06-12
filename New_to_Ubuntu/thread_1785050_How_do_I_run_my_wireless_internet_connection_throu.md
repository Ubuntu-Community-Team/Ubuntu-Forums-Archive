---
title: "How do I run my wireless internet connection through Linux?"
date: 2011-06-17
forum: New to Ubuntu
---

### Post by TMundo on 2011-06-17
Sorry for the sheer basicness of my question.  I just installed Linux Ubuntu on my computer.  I am presently running it alongside Windows XP.  I have a Linksys E1000 wireless router, with a USB card.  It ran fine through Windows, but Linux doesn't have a driver for it.  I have heard that there are online drivers I could get (possibly) but I have not had any success in finding one.  I know a site where I can buy a new USB card, but before I spend the money, I want to make sure I am not overlooking something that can be solved easily.

     Also, a friend gave me a TRENDnet TEW-424UB USB Card, but its installation CD only supports Windows, as does the installation CD for the Linksys E1000.  Can anyone help me out?

---

### Post by wolfen69 on 2011-06-17
Open a terminal and do:
```
lsusb
```
Copy and paste the output here.
Also, check "additional drivers" section and see if there is a driver offered. But you will need to be online via a cable.

Oh, did you click the little network icon to see if there are any wireless access points?

---

### Post by TMundo on 2011-06-17
the output for the USB with my Linksys Card is as follows:

Bus 001 Device 002: ID 13b1:002f Linksys AE1000 v1 802.11n [Ralink RT2870]

I am online via a cable connection.  Do you mean additional drivers on this site?

Let me know if you need any other info.  Any help would be most appreciated

thanx

---

### Post by pqwoerituytrueiwoq on 2011-06-17
[http://ubuntuforums.org/showthread.php?t=1507793](http://ubuntuforums.org/showthread.php?t=1507793)
found this it is marked as solved so the answer should be in there

---

### Post by jtarin on 2011-06-17
There have been several threads on "Ralink" lately that have been solved. Might do a search in the forums.

---

### Post by Talon2 on 2011-06-17
> **TMundo said:**
> 

Bus 001 Device 002: ID 13b1:002f Linksys AE1000 v1 802.11n [Ralink RT2870]



I have a usb adapter based on that chipset.  Here is what I know:

1) With Ubuntu 11.04, it is plug and play.  If you aren't using 11.04, I recommend you do so.  If you don't like Unity, you can select Gnome 2.

2) With versions 9.04 until 10.10, that adapter is hell.  You need to blacklist some drivers...you don't want to go there.

Good luck.

---

### Post by TMundo on 2011-06-18
I downloaded and installed 11.04.  I believe that's what I've been using using.  Although I remember getting a message when I first fired it up, stating that I didn't have enough memory to run Unity, so it said it would run the standard version.

---

### Post by fractalman on 2011-06-18
[http://linuxwireless.org/en/users/Drivers](http://linuxwireless.org/en/users/Drivers)

for all linux wireless drivers

this thread deals with your wifi card

[http://www.qbik.ch/usb/devices/showdev.php?id=3285](http://www.qbik.ch/usb/devices/showdev.php?id=3285)

it looks like you need the zd1211 driver for your card,  you should be able to download it from the first link.

[http://www.qbik.ch/usb/devices/showdev.php?id=3285](http://www.qbik.ch/usb/devices/showdev.php?id=3285)

---

