---
title: "HOWTO: Setup WPC54GX Ver.2 Card."
date: 2007-06-25
forum: Networking &amp; Wireless
---

### Post by nup on 2007-06-25
Hey guys, 

A little background about what I been going through I have been trying to get this card to work for little over a week in Fedora and just couldn't get it to connect to AP. After following the instructions below I was able to install this card no problem.

Drivers for NDISWRAPPER can be found here:
[http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1166859955278&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=5527837314B252&displaypage=download#versiondetail](http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1166859955278&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=5527837314B252&displaypage=download#versiondetail)




Code:
sudo aptitude install ndiswrapper-common ndiswrapper-utils-1.9

Grab the drivers if you don't have them. Then install:
Code:
sudo ndiswrapper -i NETANI.INF

Check to see if it installed:
Code:
ndiswrapper -l

You should see something like:
Code:
netani : driver installed
        device (17CB:0001) present

Load up the module:
Code:
sudo depmod -a

NOW: To get modprobe to work, need to use module-assistant:
Code:

sudo module-assistant prepare
sudo module-assistant auto-install ndiswrapper
sudo modprobe ndiswrapper

Make sure you have ndiswrapper in  /etc/modules
if not
sudo vi  /etc/modules and add ndiswrapper

Reboot and enjoy your wireless.

---

### Post by kevdog on 2007-06-25
Just a critique on your tutorial.  Part of it Ive never done:

> 
NOW: To get modprobe to work, need to use module-assistant:
Code:

sudo module-assistant prepare
sudo module-assistant auto-install ndiswrapper
sudo modprobe ndiswrapper


Do you really need to do this??  After the depmod -a step, I just typed:

> 
sudo modprobe ndiswrapper

and everthing proceeded.

---

### Post by Herrero on 2007-12-03
Hello,

I have problem with installing drivers for this card. I did these steps:

> **nup said:**
> 
Code:
sudo aptitude install ndiswrapper-common ndiswrapper-utils-1.9

Grab the drivers if you don't have them. Then install:
Code:
sudo ndiswrapper -i NETANI.INF

Check to see if it installed:
Code:
ndiswrapper -l

You should see something like:
Code:
netani : driver installed
        device (17CB:0001) present

Load up the module:
Code:
sudo depmod -a

sudo module-assistant prepare
sudo module-assistant auto-install ndiswrapper
sudo modprobe ndiswrapper

When I typed "sudo module-assistant auto-install ndiswrapper" I recived information that this is incorrect command :/ What I did wrong? Can You help me with this card? 
Thanks,
Michael

P.S. After typing "ndiswrapper -l" I've received information: netani : driver installed device (17CB:0001) present, but in "iwconfing" there is any wirelles interfaces :/

---

### Post by drudogg on 2008-01-13
maybe somebody can help me. when you download the driver and extract it where do you save the netani.inf file to, and why won't it let me drag and drop it into the /etc/ndiswrapper/netani folder


it says that i don't have sufficient priveledges to do so?


it also tells me that the driver is already installed but when i check it it says invalid driver. because it is not there.

by the way 7.10 32 bit and dell laptop that all seems to work except this card that i am adding. i have dlink dwl-650 but the linksys is better and would like to have one card to do both windows and ubuntu. the linksys is mimo srx200 and the dlink is B and weak.

---

### Post by drudogg on 2008-01-13
okay i figured out why it told me that is was installed and i removed the folder for the netani in the /etc/ndiswrapper folder but can not get it to install still. where do i put the netani file so that it will pick it up and install???????????


this is drving me absolutely crazy

---

### Post by pjvandehaar on 2008-07-16
im a bit late, but i just put it on the desktop. no clue what im going to do with it. then i went to system->administration->windows wireless drivers and installed it. I think i got that program through apt and it was called ndisgtk

---

