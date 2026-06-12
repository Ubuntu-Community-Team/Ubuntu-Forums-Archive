---
title: "Problem with BCM4318 Wireless!"
date: 2007-08-16
forum: Networking &amp; Wireless
---

### Post by Newuser1111 on 2007-08-16
It won't connect to my wireless network! I'm not installing ubuntu until I see it working on the internet. It says that I have BCM4318. The wireless came with my ACER Aspire 3000 laptop.

---

### Post by maldojr88 on 2007-08-16
you computer might not have the drivers availiable for the wireless card
 
you need to get a program called **Ndiswrapper** which will allow you to get the drivers

and then you need another program called **fwcutter** which will provide with the firmware of the drivers...

obviously you need to download them through the     
$ apt-get Ndiswrapper
$apt-get fwcutter

this will install the two programs.... you acutally need to download fwcutter first because its gonna be used by ndiswrapper...

and u need to be conected directly first through ethernent to download the programs...

this is assuming you have a wireless card which is not being recognized by the kernel

---

### Post by maldojr88 on 2007-08-16
google this:
Ndiswrapper [name of wireless(including brand and model)]


you will find out the commands to run in the terminal that will install the drivers

for instance i would google"

Ndiswrapper Dell Truemobile 1350

let me know how it goes

---

### Post by Newuser1111 on 2007-08-16
What do I do with Ndiswrapper?
How do I install it?

---

### Post by maldojr88 on 2007-08-20
can you tell me the model and brand name of ur wireless card

---

### Post by lavinog on 2007-08-21
First off don't bother with googling for the answer...the results you find will just cause more problems.

The card you have has some issues with fwcutter that still need to be resolved
[http://bcm43xx.berlios.de/?go=devices]("http://bcm43xx.berlios.de/?go=devices")

Don't worry though, your card does work with Ubuntu, and the answer is on this forum.

many solutions will tell you to use fw-cutter first then try ndiswrapper if it fails
I would recommend skipping directly to using ndiswrapper

I also recommend finding out what revision bcm-4318 you have.
I have a bcm-4318 rev 02 which doesn't work with the solutions for the rev 01 version.
you can find this out by doing a lspci in the terminal
```
lspci |grep -i'broadcom'
```
if you get something that says:
Network Controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
then you are in luck because I too am looking for the solution...I know it is here because I did it before, but I reinstalled Ubuntu recently so I have to do it again.

here is the link I think I followed...I'll let you know if it did work for me.
[http://ubuntuforums.org/showthread.php?t=197102&highlight=4318]("http://ubuntuforums.org/showthread.php?t=197102&highlight=4318")

UPDATE: it worked

**Quick Summary**

download this file to your desktop:
[http://ubuntuforums.org/attachment.php?attachmentid=37116&d=1183395075]("http://ubuntuforums.org/attachment.php?attachmentid=37116&d=1183395075")

Either put the Ubuntu install cd in the drive, or connect your laptop to the internet via ethernet cable (i did the internet, so I can't guarantee the CD method)
right click on the downloaded file (bcm4318.all.tar.gz) and click extract here. It should make a script file and a folder
close all other programs (in case you have apt, aptitude, or synaptic running)
open a terminal:
```
cd Desktop
sudo ./ndiswrapper_setup 
```
quick note: in the terminal you can take advantage of the tab key to auto complete what you need to type ex: sudo ./ndis[tab]

it should take a couple of seconds
when it is done you should have a light or you may have to press your wireless button.

**Quick tests**
in the terminal
```
iwconfig
```
you should get some things like lo, eth0, eth1 where eth1 has information associated with it (ESSID...etc)
if you did...then good

lets test the scanning ability
```
sudo iwlist eth1 scanning
```
you should see your access point

lets connect to your access point
make sure you know the ssid (case is important)
if you are using encryption try and use wep...wpa is more difficult

lets assume your ssid is linksys
and your wep key is 1234abcdef (this is in hex...not paraphrase)
```
sudo iwconfig eth1 essid linksys enc 1234abcdef
sudo dhclient eth1
```
if it finishes by saying bound to some ip address then it worked

at this point you may want to install wifi-radar
```
sudo apt-get install wifi-radar
```
I currently don't use it anymore because I find doing it the manual way is quicker, but it will save you some trouble if you roam alot.

---

### Post by Don9307 on 2007-11-01
Go to [http://fedoranews.org/mediawiki/index.php/How_To_Install_Your_Broadcom_BCM4318_Using_Ndiswrapper](http://fedoranews.org/mediawiki/index.php/How_To_Install_Your_Broadcom_BCM4318_Using_Ndiswrapper)

---

