---
title: "Abit Airpace Card"
date: 2007-09-12
forum: Networking &amp; Wireless
---

### Post by sqrlking on 2007-09-12
i didn't see this on any of the list for compatible wireless, is there anywhere else i can check, or anything i can do to try and make it work??  I'm really new, just got ubuntu installed, so talk slow.  :)

---

### Post by TheShocker on 2007-12-08
I also have this card. Ubuntu does not automatically notice it. I want to enable it without losing my wired connection.

I found several threads about the card. A couple guys got it working but I'm a newb and can't figure out what they did.

Thanks

---

### Post by xiphosurus on 2008-01-06
Managed to get it working! w00t!

i did these first to install ndiswrapper 1.51. You might need the Ubuntu installation CD for these steps. extract ndiswrapper 1.51 into a folder. Then start terminal and go into the folder.

```
sudo apt-get update
sudo apt-get install build-essential
sudo apt-get install linux-headers-`uname -r`
sudo ln -s /usr/src/linux-`uname -r` /lib/modules/`uname -r`/build
make distclean
make
sudo make install
```

**note that the ` and ' are different characters!!

then I followed this guide from another forum
*****************************************
I managed to get the airpace working with ubuntu, but had to jump through
 several hoops.

 Here is what i did:

 1. you need to use the windows 32bit driver... you should have 3 files
 named net2425.inf, net2425.cat and aw5006.sys - make sure these are placed
 somewhere you can get to them from linux

 2. Make sure ndiswrapper is installed (I am using version 1.9)

 3. in a terminal, run: sudo depmod -a

 4. unload ndiswrapper (in case it's loaded) - in a terminal: sudo modprobe
 -r ndiswrapper

 5. You need to blacklist ath_pci...edit the  /etc/modprobe.d/blacklist
 file (you may need to alter file permissions to do that) - to the end, add
 this and save the file: blacklist ath_pci

 6. find ath_pci.ko in the file system, and rename it (to be sure... lol)
 -you may need to alter file permissions or use sudo to rename it

 7. make sure ndiswrapper has no wifi drivers... in a terminal, run:
 ndiswrapper -l to make sure. If it has drivers listed, then run: sudo
 ndiswrapper -r drivername

 8. lets install the driver: in a terminal change directory to where the
 windows drivers are located.  Next, run this command: sudo ndiswrapper -i
 net2425.inf

 9. now, load the ndiswrapper module. In a terminal:- modprobe ndiswrapper

 and thats it.... should all work.

 BTW: I am a linux (very) newbie and found most of this out via google and
 a lot of patience.  If anyone wants help they can add me to msn and I will
 try to help: aspwiz[^at^]hotmail[^dot^]com)

 Good luck :)
**************************************************
Note that the last step 9, instead of entering in the command

```
modprobe ndiswrapper
```

Use this instead

```
sudo modprobe ndiswrapper
```

Notes: I found the 3 driver files in step 1 by doing a search on my windows with the driver already installed.

Mine worked after that. I used ndiswrapper 1.51, ubuntu 7.10, 32 bit.

After all these, to make sure ndiswrapper loads each time you start, enter this in terminal...

```
echo "ndiswrapper" | sudo tee -a /etc/modules
```

---

### Post by xiphosurus on 2008-01-06
are we allowed to post those drivers from abit?

---

### Post by ubun_two on 2008-01-28
You can find the 32bit driver you need here:

[http://www.atheros.cz/download.php?atheros=AR5007EG&system=1](http://www.atheros.cz/download.php?atheros=AR5007EG&system=1)

I also tried 64bit version the same way (with 64bit driver), and unfortunately, the result was very spotty.  I got the connection correctly about 50% of the time...  I was always able to see available wireless network in the area, but when I attempt to connect, the result was hit and miss.  DHCP sometimes response, and sometimes not, for some reasons...

This forced me back to 32bit...:frown:

Anyone had any success with 64bit Ubuntu?

---

### Post by galileo99 on 2008-02-02
> **TheShocker said:**
> I also have this card. Ubuntu does not automatically notice it. I want to enable it without losing my wired connection.

I found several threads about the card. A couple guys got it working but I'm a newb and can't figure out what they did.

Thanks

"Without losing my wired connection". What do you mean?

I don't mind "loosing" my wired connection for my abit AirPace card.
xiphosurus's method is a bit complicated. Is there a more simple way?

---

### Post by ubun_two on 2008-02-05
> **galileo99 said:**
> 

xiphosurus's method is a bit complicated. Is there a more simple way?

I was able to get it to work without compiling ndiswrapper on my own.  I used one that I installed using Synoptic in Gutsy.

Other than that, I pretty much followed everything that was posted.  It's fairly standard procedure with ndiswrapper.

---

### Post by mala88 on 2008-03-23
Did anyone get this working with Ubuntu x64 ? I installed the Atheros  XP x64 drivers in ndiswrapper and the card is recognized. Network manager scans and displays the available wireless networks, but it does not connect to a WPA-AES network. It keeps getting stuck during the dhcp lease request.:confused:

 I also tried installing wicd and followed the troubleshooting instructions [here]("http://wicd.sourceforge.net/phpbb/viewtopic.php?f=3&t=158&sid=1a563935dbce4329e49eab9517ec57ee") but it cannot connect either. 

Any help is appreciated. Thanks.

---

### Post by VitalBodies on 2008-04-28
I would also like to get the 64-bit version going. Has anyone tried the madwifi driver? 
I downloaded the MadWifi but was not that sure how to install it. 

My current card is an Abit Airpace PCIe card. 

Without loading the Madwifi driver I have in **Hardware Drivers** there is an Atheros Hardware Abstraction Layer (HAL) IN USE and enabled since putting the mini PCI wifi in.  Plus "support for Atheros wireless lan" shows up IN USE and Enabled but no **Wireless Connection** in the **Network Settings**. 

I am using the 64-bit version of Hardy on an Intel Core 2 Quad Core Q6600 Dell 530 Inspiron.

The Wifi does show up if I do a lshw - C network.
network UNCLAIMED. What does that mean?
iwconfig says:
lo no wireless extensions.
eth0 no wireless extensions.
I would guess this means that Ubuntu sees the card but there is no driver loaded.
EDIT: From all I have read this is true.

So just by chance, both my D-link DWL-G132 USB wireless card and the abit use the Atheros chip. 
Might try this: [http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo)
Ubuntu: [http://madwifi.org/wiki/UserDocs/Distro/Ubuntu](http://madwifi.org/wiki/UserDocs/Distro/Ubuntu)

Trying this fail because the make command can not cd to a directory that is not there. 
 
Command line help: [https://help.ubuntu.com/7.10/basic-commands/C/](https://help.ubuntu.com/7.10/basic-commands/C/)

---

### Post by thekilobyte on 2008-04-28
Hey VitalBodies, let us know how the 64-bit driver installation goes. I have the same card and I plan to get 64-bit Hardy Heron installed sometime this week.

---

### Post by VitalBodies on 2008-04-29
> **thekilobyte said:**
> Hey VitalBodies, let us know how the 64-bit driver installation goes. I have the same card and I plan to get 64-bit Hardy Heron installed sometime this week.

I am going to try this: 
[http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html#more-484]("http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html#more-484")
If anyone gets this to work please report back.

---

### Post by VitalBodies on 2008-04-30
I got it going! I had a LOT of help. 
Here is what is needed: 
You need to get Ndiswrapper going. 
If you had a connection to the net this all would be easy. 
Just go to Synaptic Package Manager, that is in System > Administration and search the Synaptic Package Manager for **Ndis** and you will find three things to load:
ndisgtk
ndiswrapper-common
ndiswrapper-utils. 


But with no connection you will have to use another computer and connect and get these:
Mirrors for 64 ndisgtk:
[http://packages.ubuntu.com/hardy/amd64/ndisgtk/download](http://packages.ubuntu.com/hardy/amd64/ndisgtk/download)

Mirrors for [all architecture] ndiswrapper-common: 
[http://packages.ubuntu.com/hardy/all/ndiswrapper-common/download](http://packages.ubuntu.com/hardy/all/ndiswrapper-common/download)

Mirrors for 64 ndiswrapper-utils 1.9:
[http://packages.ubuntu.com/hardy/amd64/ndiswrapper-utils-1.9/download](http://packages.ubuntu.com/hardy/amd64/ndiswrapper-utils-1.9/download)

Download all 3 and install them in this order: commons, utils and then ndisgtk.
NOTE: They will answer with dependency error if one or the other has to go first. 

Once these are installed then use this driver: 
[http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz](http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz)

Once you have installed that driver setup your wireless in Network Settings. 
Note: Be sure to reboot if you have problems. 

I wrote his message using the 64-bit Ubuntu Hardy and my Atheros based Abit wireless card! 

Please add your helpful notes to those who follow our foot steps....
Did this post help?

---

### Post by c3apollyon on 2008-05-11
Worked great for me.  Thanks for the tip VitalBodies!

---

