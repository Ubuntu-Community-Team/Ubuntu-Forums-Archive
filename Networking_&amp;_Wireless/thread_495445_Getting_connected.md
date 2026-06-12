---
title: "Getting connected"
date: 2007-07-08
forum: Networking &amp; Wireless
---

### Post by samuraix on 2007-07-08
Hello everyone,
I just got Ubuntu a few days ago and finally got my bcm4318 install with this HOWTO [http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990).

Now i am having problems connection to my network.
I have research the internet and i found i could detect my network with "iwlist scanning"
but i get no results. I have a BUFFALO WHR-G54S on my house and its protected. 
I don't know what information you guys need from me, but please tell me and I'll do my best on giving you the info. to fix the problem.
How i said before i just got Ubuntu no more then a week ago, so please help me out or redirect me to another part of the forum so i can get this fixed.
thank you for your tie guys

---

### Post by Fitzy_oz on 2007-07-08
> **samuraix said:**
> Hello everyone,
I just got Ubuntu a few days ago and finally got my bcm4318 install with this HOWTO [http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990).

Now i am having problems connection to my network.
I have research the internet and i found i could detect my network with "iwlist scanning"
but i get no results. I have a BUFFALO WHR-G54S on my house and its protected. 
I don't know what information you guys need from me, but please tell me and I'll do my best on giving you the info. to fix the problem.
How i said before i just got Ubuntu no more then a week ago, so please help me out or redirect me to another part of the forum so i can get this fixed.
thank you for your tie guys

Broadcom cards are a huge huge pain in the **** so it might take a few goes at it.  I would advise switching to the NDISWrapper and using you're windows drivers for the card as the native ones are just to flakey.

to do this first thing you'll need to do it install the NDISWRAPPER package and the graphical utility for it to make it easy to configure.

The packages are ndiswrapper-common
                                  ndiswrapper-utils-1.9
                                  ndisgtk.

So drop to a terminal and type sudo apt-get install ndiswrapper-common ndiswrapper-utils* ndisgtk.

Once this is installed, disable the broadcom driver by typing gksudo gedit /etc/modprobe.d/blacklist

you'll need to add the line:
**blacklist bcm43xx**

Save the file and then open the System menu, goto administration and then windows wireless drivers.  make sure you have you're wireless driver disk in the drive (or download them from the web). click install driver and navigate to where the inf file for the driver is usually under the folder win98 or winxp2000 on the disk.  It will install the driver for you.  Reboot the sytem and you should be good to go.

---

### Post by samuraix on 2007-07-08
Thanks a lot it works like a charm. The only problem i had was getting connected with ndisgtk but i used System>Administration>Network and i got it running in 2 minutes.

---

