---
title: "Acer wireless question"
date: 2007-09-04
forum: Networking &amp; Wireless
---

### Post by laihafloyd on 2007-09-04
I've tried everything I could try given my limited linux skills, but I can't seem to get my wireless button on my Acer to light up when I start ubuntu.  But, strangely, when the computer hibernates and re-awakens, my wireless button lights up and I can get online!

My linux skills are amateurish at best, so i have no idea what happens when the computer hibernates to cause my wireless to suddenly work.  Does anyone have any suggestions on how i can take whatever is working when it hibernates and make it happen when ubuntu originally fires up?  Thanks for any help or information...


Marc

---

### Post by noob12 on 2007-09-04
I don't understand that, but the typical solution to enabling the wireless involves loading the acerhk module with the correct options and then toggling either the switch or the control file under  /proc. 


Feisty has the acerhk module built-in, but it doesn't load by default.  You need to load it with appropriate options for your device and laptop.
See [http://rfswitch.sourceforge.net/?page=laptop_matrix](http://rfswitch.sourceforge.net/?page=laptop_matrix)

I can probably help you further if you post more about your system:

What Acer model do you have?
The output of
```

lspci -nn

sudo lshw -C network

```

---

### Post by laihafloyd on 2007-09-04
The laptop is an Acer 3000, i'm using feisty.  on a side note, i can't even use pc wireless cards either.  When I upgraded from edgy to feisty, i lost functionality of the wireless button.  again, thanks for any help...

marc@marc-laptop:/$ sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@00:04.0
       logical name: eth0
       version: 91
       serial: 00:16:36:08:96:1e
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=half latency=173 link=no maxlatency=11 mingnt=52 multicast=yes port=MII speed=10MB/s
       resources: ioport:1800-18ff iomemory:e2005000-e2005fff irq:16
  *-network:1 DISABLED
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: b
       bus info: pci@00:0b.0
       logical name: eth1
       version: 02
       serial: 00:14:a4:73:1d:dd
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-16-386 latency=64 link=no multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:e2000000-e2001fff irq:22

---

### Post by noob12 on 2007-09-05
OK.  I don't have have any direct experience with that model.  The switch on that model is supposed to be pure hardware (according to the rfswitch page referenced earlier it requires no driver/software assistance to toggle the radio).  I would suggest that you check your BIOS settings for something that controls it on startup and try pressing the indicator switch on the front of the laptop.

Can you post the output of:
```

cat /sys/class/net/*/device/rf_kill

```
If this puts out a number at all, we want to see it be 0 or 1, something other than 2.


I also notice you are running the bcm43xx driver.  Does that work fine for you once you manage to enable the radio?  If not you might try this thread:  [http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

---

### Post by laihafloyd on 2007-09-05
The output of cat /sys/class/net/*/device/rf_kill returned file not found.

To answer your question, yes, the wireless works fine when i do get the light to come on.  I went ahead and checked out the link [http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990) anyway and downloaded the new driver and, lo and behold, it worked!  The button acts a little different though.  the light blinks whenever there are packets being sent or received.  It used to stay solid the entire time I was connected to an access point.

Anyway, thanks so much for your help!

---

### Post by noob12 on 2007-09-06
Great to hear.

---

