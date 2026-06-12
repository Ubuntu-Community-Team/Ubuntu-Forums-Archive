---
title: "Wireless card not being seen?"
date: 2008-02-21
forum: Networking &amp; Wireless
---

### Post by burns863 on 2008-02-21
Hi Guys,

Tearing my hair out here.  My Edimax EW-7728In doesn't appear to be being seeing (unless my beginner skills have limited me into seeing it myself :lolflag: ).  

Was going to use ndiswrapper to install the car, however I have found some native Linux drivers through the help of another post for the chipset of my card.  However, the results of the following command dont seem to be showing my wireless card at all?

Hope somebody can help!

```
lshw -C network
```

Results:
```
sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 9
       bus info: pci@0000:00:09.0
       logical name: eth0
       version: 02
       serial: 00:06:4f:03:77:bc
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=full ip=192.168.2.3 latency=32 link=yes maxlatency=11 mingnt=52 module=sis900 multicast=yes port=MII speed=100MB/s
daniel@Project-Host:~$ 
```

---

### Post by Hightide on 2008-02-21
Hi

please post output from

```
iwconfig
```

regards

:)

---

### Post by steeleyuk on 2008-02-21
You might also want to post the output of **lspci**.

---

### Post by burns863 on 2008-02-21
Thanks guys. Here is the output to both those commands.  Hope it helps with my problem :)

```
daniel@Project-Host:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

daniel@Project-Host:~$ lspci
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:04.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:04.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:04.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:04.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
00:09.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV5 [RIVA TNT2 Ultra] (rev 11)
daniel@Project-Host:~$ 
```

Also, not sure if this makes any difference but it is quite an older spec machine.  It is just being used as a host for media, in a Myth TV setup so I have just chosen to use this old P3 machine I had lying about!

---

### Post by burns863 on 2008-02-22
Bumpety Bump :D

---

### Post by burns863 on 2008-02-26
Can anyone shed any light on my terminal posts?

I have now moved on to trying to compile and install the Linux Source Code for my WLAN adapters chipset.  I have been following this guide [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

However, I am at the "sudo apt-file update" command, and terminal is reporting "command not found".  Slightly confused now!

Help! :D

Dan

---

### Post by rustybronco on 2008-02-26
> **burns863 said:**
> 

However, I am at the "sudo apt-file update" command, and terminal is reporting "**command not found**".  Slightly confused now!

Help! :D

Dansudo apt-get install apt-file ( command not found, so you will need to get and install apt-file)

[http://wiki.linuxquestions.org/wiki/Apt-file](http://wiki.linuxquestions.org/wiki/Apt-file)

then do the sudo apt-file update

---

### Post by burns863 on 2008-02-28
Sorry guys... me being stupid has meant my post was wrong.  I ws posting feedback on my  problems from memory.


I have the apt-file package installed.  When trying to upfdate, I am not getting "command not found", I am getting the following...

```
daniel@Project-Host:/usr/local/src/2008_0108_RT2860_Linux_STA_v1.5.0.0$ apt-file update
E: Can't write in /var/cache/apt/apt-file
daniel@Project-Host:/usr/local/src/2008_0108_RT2860_Linux_STA_v1.5.0.0$ sudo chown daniel /var/cache/apt/apt-file
[sudo] password for daniel:
daniel@Project-Host:/usr/local/src/2008_0108_RT2860_Linux_STA_v1.5.0.0$ apt-file update
Put CDROM labeled [Ubuntu_7.10__Gutsy_Gibbon__-_Release_i386_(20071016)] in the cdrom device
read: 1: arg count
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: /dev/scd0 already mounted or /media/cdrom0 busy
mount: according to mtab, /dev/scd0 is already mounted on /media/cdrom0
cp: cannot stat `/cdrom/dists/gutsy/Contents-i386.gz': No such file or directory
daniel@Project-Host:/usr/local/src/2008_0108_RT2860_Linux_STA_v1.5.0.0$  

```

It asks me fr the Ubuntu disc, but feeds back "no such file or directory".  

Hope somebody can help, I dont understand the problem with this one!  Obviously its a problem with the disc but al lI have done is burn the disc image I had!

EDIT....

Ok, I didnt realise that if I just gave it time, it woulf use another source.  The update command seems to have worked now, but I have ran into another problem.

In the directory I creted from unpacking the tarball, there sems to be no configure file what so ever.  so by running ./configure I get no such file or directory.  HELP :)

---

### Post by burns863 on 2008-02-28
OK guys.  I have been working in a bit of a muddled up order.  I ignored the fact that my WLAN card was not being showing with various terminal commands and continued to compile and install the source code for the card.  Reason for this is that I am just clutching at straws.  After installing, the card was STILL not being seen.

As posted earlier, the output from "lshw -C network" and "lspci" dont show the card anywhere.  All they show is my ethernet card.

I am now on a completely fresh install as I felt I had messed around with too many things over the past few weeks and hadn't got anywhere.  God knows the amount of things I have tried, so I decided to reinstall Ubuntu and start again from scratch.  This also meant that the card was present during the installation of Ubuntu, where as last time it wasn't.  I thought that this may help but it doesn't seem to have. All I know is that the green light is on the card, although I guess this doesn't really mean much?

Im completely frozen in time here.  Cant progress until this is sorted and I am waaayyyy behind with my project now.  I would really really appreciate some more help from anyone that might be able to shed some light on my the card doesn't appear to be being seen?  I dont want to progress with making and installing the source code until its at least recognised!

Thank you in advance

Dan

---

