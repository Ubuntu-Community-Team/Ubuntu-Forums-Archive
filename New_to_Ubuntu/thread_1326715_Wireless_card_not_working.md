---
title: "Wireless card not working"
date: 2009-11-14
forum: New to Ubuntu
---

### Post by chriscross93 on 2009-11-14
Hello,
I just tried installing a Linksys WPC300N in my laptop (Karmic) using ndisgtk.  I pointed it at the driver (.inf) file and it seems to have worked (after reboot).  The lights on the card now light up.  Also, it now shows up when I run lspci in a terminal. ...But no wireless networks show up when I search (using Wicd).  I don't know where to go from here, I've been googling and on the wiki for a while now.  Thanks in advance.

---

### Post by Bunnybugs on 2009-11-14
> **chriscross93 said:**
> Hello,
I just tried installing a Linksys WPC300N in my laptop (Karmic) using ndisgtk.  I pointed it at the driver (.inf) file and it seems to have worked (after reboot).  The lights on the card now light up.  Also, it now shows up when I run lspci in a terminal. ...But no wireless networks show up when I search (using Wicd).  I don't know where to go from here, I've been googling and on the wiki for a while now.  Thanks in advance.

[http://linuxwireless.org/en/users/Download](http://linuxwireless.org/en/users/Download)

Here you will probably find your answer!

---

### Post by chriscross93 on 2009-11-14
The driver already seems to be in place, I just need to make it talk with Wicd (or another network manager, I'm open to change).  Is the package on linuxwireless a compilation of drivers?  I'm not really sure what it is, or what to do...

---

### Post by Bunnybugs on 2009-11-14
Well, What if you use the default network manager??

I didn't have any trouble with wireless untill I tried to change the software... changed back, and no trouble!

---

### Post by chriscross93 on 2009-11-14
Will do. Thanks for your time, will report back soon.

---

### Post by chriscross93 on 2009-11-14
ALMOST THERE!

I re-installed the default ubuntu network manager, now I can see wireless networks but cannot connect.  I put in the WPA key, the card ACT light blinks quickly for about 15 secs. and it does not connect.  Could it be an issue with WPA?  Is there something else I need?  Thanks again for your understanding, I'm new to the wireless side of ubuntu...

---

### Post by Bunnybugs on 2009-11-14
There are some codecs you'll need to install from Synaptic...

Search for WEP and WPA etc, etc, those are keysystems for WiFi

---

### Post by chriscross93 on 2009-11-14
Awesome.  Is there anything I need to do to use this Draft N card with a G network?

---

### Post by chriscross93 on 2009-11-14
Ok, WPA supplicant driver was already installed.  I disabled encryption on my network, now it works.  The problem is that I really need it to be secure...

EDIT
I installed the GUI for the WPA Supplicant Driver.  The Gui does not seem to see my card, how do make them talk?

---

### Post by 0nelove on 2010-05-18
#  Chipset: Broadcom Corporation BCM43XG
# pciid: 14E4:4329 

old thread, but after dancing around with this for a couple hours, I figured I'd share some notes relating to one possible solution in case somebody finds this thread searching for an answer.

Problem: linux fails to recognize Linksys WPC300N V1 PCMCIA card

Solved by:
> 
sudo apt-get install ndiswrapper


go here:
> [http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Linksys_WPC300N](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Linksys_WPC300N)

You'll need to extract that driver (a couple times) to get at the goodies inside.  dump the guts (you can skip the big cab files) into a folder & then:

> sudo ndiswrapper -i bcmwl5.inf

ndiswrapper -l  will show you the driver that is now associated with the card.  reboot & hopefully you'll be closer than before.

other misc useful commands:
lspci
lshw -C network
ndisgtk package was used during another unsuccessful attempt.  It's just a gtk frontend for ndiswrapper, I think.

cheers all & good luck!

---

