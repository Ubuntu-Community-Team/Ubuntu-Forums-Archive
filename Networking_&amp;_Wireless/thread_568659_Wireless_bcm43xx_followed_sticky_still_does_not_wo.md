---
title: "Wireless bcm43xx followed sticky still does not work"
date: 2007-10-06
forum: Networking &amp; Wireless
---

### Post by mrdaze0 on 2007-10-06
i have ndiswrapper installed using this to install bcm43xx drivers.  I have followed all of the advice i can find on the forums to get the card working.  i have a hp dv6500t laptop.

mrdaze0@mrdaze0-laptop:~$ ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4328) present
bcmwl6 : driver installed
        device (14E4:4328) present

ran ndiswrapper -m
and renamed wlan0 to eth1

iwconfig results with
mrdaze0@mrdaze0-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

any ideas on what i can do to get the card working

uname -r 2.6.22-12-generic
ubuntu 7.10

---

### Post by mrdaze0 on 2007-10-06
Some more info
lshw -C network command results with 

mrdaze0@mrdaze0-laptop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: nVidia Corporation
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 34:b7:aa:24:1b:00
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.60 duplex=full ip=192.168.0.103 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
  *-network UNCLAIMED
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0

---

### Post by kevdog on 2007-10-06
Ok within ndiswrapper you have the following drivers loaded

bcmwl5 and bcmwl6.  You can only use one or the other, not both.  Decide which one you want and then remove the other.  For example if you want bcmwl5, remove bcmwl6 with the following

sudo ndiswrapper -r bcmwl6

---

### Post by mrdaze0 on 2007-10-06
yeah i was thinking that last night.  i already removed the bcmwl5.  rebooted and tried to get the card running again still not working. any other suggestions?

---

### Post by kevdog on 2007-10-06
Do you have windows xp drivers for the card??  Inside these drivers do you know if they are bcmwl5 or bcmwl6??  Usually about 95% of the cases its bcmwl5 but Ive seen version 6 used.

Whenever you make a change, can you post
ndiswrapper -l

After making the chanage do you reload the kernel module
sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper

After this what is the following output:
lshw -C network 
In the above statement you need to look for a driver statement to tell you your device is associated with the ndiswrapper driver.

---

### Post by gimp0r on 2007-10-06
I have exactly the same laptop as this. same network card and same graphics card (seen your other post)

I used this to get ndiswrapper installed and working within minutes [http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

is yours the amd64 version? if so have you managed to get the speakers to mute when you plug in headphones?

Gimp0r

---

### Post by mrdaze0 on 2007-10-06
Looks like it is up and running now...i had originally downloaded the windows driver from HP.  that was the bcmwl6 well i removed that and the re did the installation from [http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990) light is now blue finishing updatign system and restarting. 
I do have amd64.  and No sound does not work at all yet.  I started installing 7.10 last night at midnight and gave up at 3:30.  who knows i might have gotten this on my own if it hadnt been for the late hours.

I am going to work on the sound next.  I will let you know what i get working on it.

Thanks for all your help.

---

### Post by mrdaze0 on 2007-10-08
On the sound issue.  got sound working then it was nto turnging off for headphones
turned out to be an easy fix
just added option "snd-hda-intel model=laptop postion_fix =1" to the bottom of /etc/modprobe.d/alsa-base

---

