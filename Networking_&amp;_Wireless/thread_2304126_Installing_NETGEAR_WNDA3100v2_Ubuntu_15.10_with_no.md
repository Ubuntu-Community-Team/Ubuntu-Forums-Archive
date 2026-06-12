---
title: "Installing NETGEAR WNDA3100v2 Ubuntu 15.10 with no internet connection"
date: 2015-11-24
forum: Networking &amp; Wireless
---

### Post by Will_Snikov on 2015-11-24
Hello all,

I'm really in a bit of a sticky situation here - I've just installed ubuntu 15.10 - it works perfectly.

However, it seems I should've done some research when purchasing my wireless adapter as I have picked up the infamously difficult Netgear WNDA3100v2.

To worsen conditions, the machine I am trying to set up has no ethernet connection and therefore no internet connection whatsoever.

If anybody is aware of any firmware or drivers for this distro of Ubuntu, please let me know as this is very rapidly becoming the bane of my life.

Having to switch between Operating Systems only exacerbates the situation. I hope someone can help.

I have time and determination to put up with the pain to get this fixed. Thank you very much.

---

### Post by Bucky Ball on 2015-11-24
Welcome. You are going to save yourself a lot of time by buying another that 'just works'. 

You are in a bad place as this stick is notoriously hard to get up, if you manage, *with* internet, let alone without it. One of the wireless gurus may figure out a genius plan, but you could be in for a long(er) ride.

---

### Post by chili555 on 2015-11-24
I assume you mean Ubuntu 15.10; confirm:```
lsb_release -a
```Assuming that is the case, on some other computer, go here: [http://packages.ubuntu.com/search?keywords=ndiswrapper&searchon=names&suite=wily&section=all](http://packages.ubuntu.com/search?keywords=ndiswrapper&searchon=names&suite=wily&section=all) and here: [http://packages.ubuntu.com/search?keywords=dkms&searchon=names&suite=wily&section=all](http://packages.ubuntu.com/search?keywords=dkms&searchon=names&suite=wily&section=all)

Select and download the packages ndiswrapper, ndiswrapper-dkms and dkms appropriate to your architecture; either 32- or 64-bit. Confirm:```
arch
```If you get x86_64, then you have a 64-bit system and need the packages referred to as amd64 or all.

When you have the three .deb files, transfer them on a USB drive or similar to the Ubuntu machine. Drag and drop them to the desktop. Install them with the terminal:```
cd ~/Desktop
sudo dpkg -i *.deb
```You may be missing a dependency or two. If so, go back and get them and add them to the desktop and try again.

Next, please confirm your exact device and I'll show you where to get the driver files:```
lsusb
```

---

### Post by chili555 on 2015-11-24
> **Bucky Ball said:**
> .... but you could be in for a long(er) ride.Indeed! LOL!

---

### Post by Bucky Ball on 2015-11-24
I'll leave you in chili555's capable hands and watch with anticipation. Hoping you can get it going. :)

[quote=chili555]Indeed! LOL! [/quote]

Just noticed this. ;)

---

### Post by Will_Snikov on 2015-11-24
Hi Bucky Ball,
Thank you very much for your welcome, however I'm afraid I'm not the type to throw my hands up and in extent, throw money at Wireless Adapters haha - if it is possible to get this to work I will do everything I can to make it functional!

---

### Post by Bucky Ball on 2015-11-24
Read from [chili's first post]("http://ubuntuforums.org/showthread.php?t=2304126&p=13396079&viewfull=1#post13396079") and follow the instructions. :D

---

### Post by Will_Snikov on 2015-11-24
Thank you chili555, here is my response after installing everything:

```

user@Computer:~/Desktop$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 15.10
Release:	15.10
Codename:	wily


user@Computer:~/Desktop$ arch
x86_64


user@Computer:~/Desktop$ lsusb
Bus 002 Device 005: ID 13fe:5500 Kingston Technology Company Inc. 
Bus 002 Device 004: ID 0a48:4001 I/O Interconnect 
Bus 002 Device 003: ID 0846:9011 NetGear, Inc. WNDA3100v2 802.11abgn [Broadcom BCM4323]
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0461:4d0f Primax Electronics, Ltd HP Optical Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

---

### Post by chili555 on 2015-11-24
Download this file and, again, transfer it on a USB or similar to the desktop: [http://media.cdn.ubuntu-de.org/forum/attachments/06/41/2612284-Broadcom_bcm43xx_USB_32_64bit_v2.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/06/41/2612284-Broadcom_bcm43xx_USB_32_64bit_v2.tar.gz)

On the desktop of the Ubuntu machine, right click and select 'Extract Here.' Now, back to the terminal:```
sudo ndiswrapper -i ~/Desktop/Broadcom_bcm43xx_USB_32_64bit_v2/bcmn43xx64.inf
sudo modprobe -v ndiswrapper
sudo ndiswrapper -ma
```Is a wireless interface created?```
iwconfig
```Can you connect?

---

### Post by Will_Snikov on 2015-11-24
I will try this now, Thank you.

---

### Post by Will_Snikov on 2015-11-24
I'm afraid not.

upon executing the ndiswrapper -i command to install the inf file, it said that the installation was missing a "SaveDiskSource" (I think) but it had proceeded and installed anyway.

```

snik0v@Redmoon27:~$ ndiswrapper -l
bcmn43xx64 : driver installed
snik0v@Redmoon27:~$ iwconfig
enxe2f847fa8a93  no wireless extensions.


enp0s25   no wireless extensions.


lo        no wireless extensions.


snik0v@Redmoon27:~$ 

```

---

### Post by chili555 on 2015-11-24
Let's see if there are any clues as to what went wrong:```
dmesg | grep ndis
```Is the device inserted?

---

