---
title: "Unable to install Micronet SP907GK Wireless LAN USB Adapter"
date: 2008-10-13
forum: Networking &amp; Wireless
---

### Post by pluggster on 2008-10-13
Hello,

Just installed Hardy on a PC I built from bits I had laying around. Not used Linux since Uni when I had a taste of RedHat ... and let me tell you I wish I had carried on using it ... it's great to be back!

Anyways, my problem which I would like some help with, please. I have searched all over but cant seem to find any specific information anywhere.

This PC I have built, originally had Win XP on it, but I wanted to use LAMP to develop a website project I have been toying with for a year or two, so decided to come back to Linux. The install seemed to go OK, and I didn't realise I had a PCI Lan card installed until 5 minutes ago. I've jacked a CAT5 in and hey presto, I am writing this from within Hardy .. .great.

However, until 5 minutes ago, I have been trying to get a Micronet SP907GK Wireless LAN USB Adapter installed without success.

Firstly I had to install ndiswrapper, which I think went smoothly ... I say smoothly, I followed some instructions I found somewhere which suggested downloading 3 files and installing ndiswrapper using the following command:

```
sudo dpkg -i *.deb
```

The three files I had to install where:

```
ndiswrapper-common_1.43-1ubuntu2_all.deb
ndisgtk_0.7.2-1ubuntu1_i386.deb
ndiswrapper-utils-1.9_1.43-1ubuntu2_i386.deb

```

However, I have since read that the three files need to installed in a specific order!?! (This I read in these forum pages somewhere, I think)

Right, so I installed ndiswrapper, then I try 'Install New Driver' by pressing the button. I then navigate to the CDROM which contains all the drivers and locate the .inf file (there's one for Win98 all the way up to Win Vista ... no linux tho). But when I've clicked complete I don't get anything showing in the 'Currently Installed Windows Drivers' panel. I tried this process of trying to install the driver a couple of times, so I guess there may be something corrupt now!!

If I plug the Wireless USB stick into the machine I don't get any clue as to it working. When I've tried rebooting the machine with the Wireless USB stick plugged in, the machine crashes.

When I run the 

```
lshw -C network
```

command, I get the following output:

michael@spogo:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: DP83815 (MacPhyter) Ethernet Controller
       vendor: National Semiconductor Corporation
       physical id: f
       bus info: pci@0000:00:0f.0
       logical name: eth0
       version: 00
       serial: 00:40:f4:1a:68:06
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=natsemi driverversion=2.1 ip=192.168.1.68 latency=64 maxlatency=52 mingnt=11 module=natsemi multicast=yes
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:11:3b:13:71:a8
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g


When I run this command:

```
lsmod|grep ndiswrapper
```

I don't get anything returned. And when I run this command:

```
ndiswrapper -l
```

again, nothing is returned. I have then run this command:

```
sudo modprobe -r ndiswrapper
```

and that didn't return anything. So I ran this command:

```
sudo modprobe ndiswrapper
```

And that didn't return anything. Finally, I ran this command:

```
dmesg|grep ndiswrapper
```

which, finally (phew!) output this:

michael@spogo:~$ dmesg|grep ndiswrapper
[ 4595.368534] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[ 4595.433567] usbcore: registered new interface driver ndiswrapper

Now, this is strange. I've just thought to go into Network settings and see whats happening in there. It looks like the Wireless connection is working. I'm going to play around with it and see if it is and get back to y'all.

Cheers,

Michael

---

### Post by alan34 on 2008-10-14
Try copying the .inf and .sys files to a new folder on your desktop from the cdrom.
I believe that you cannot install the files direct from a cd. (What I have always done).

If you have installed ndisgtk you should have Windows Wireless Drivers as a menu item
under System - Administration.

If you want to use the terminal ........

    1  cd towhereyourfilesare
    2  sudo ndiswrapper -i yourfile.inf 
    3  sudo ndiswrapper -l
    4  sudo depmod -a
    5  sudo modprobe ndiswrapper
    6  sudo ndiswrapper -m
    7  gksudo gedit /etc/modules 
    8  gksudo gedit /etc/modprobe.d/blacklist

3 - should give you something like this

alan@alan-desktop:~$ sudo ndiswrapper -l
[sudo] password for alan: 
net8185 : driver installed
	device (10EC:8185) present
alan@alan-desktop:~$ 

7 is add **ndiswrapper** on a line on its own at the bottom of the file

and 8 is blacklisting the kernal module - whatever yours is.

good luck

---

### Post by atomicdonald on 2009-11-23
I got this working out of the box with Karmic and also previously with Hardy. Seems to be recognised as Ath0.

It even worked on a fresh install NBR 9.10 working on an old PIII 450Hz desktop PC. I don't recommend running OOO on something that old but Firefox was acceptable though slow. 

see here : [http://donaldindeed.blogspot.com/2009/11/my-linux-marathon-9-nov-2009.html](http://donaldindeed.blogspot.com/2009/11/my-linux-marathon-9-nov-2009.html)

Hope this helps.

D.

---

