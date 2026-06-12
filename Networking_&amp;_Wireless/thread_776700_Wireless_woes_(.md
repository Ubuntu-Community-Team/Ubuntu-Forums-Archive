---
title: "Wireless woes :("
date: 2008-04-30
forum: Networking &amp; Wireless
---

### Post by Yewni on 2008-04-30
Just switched over from Freespire to the latest version of Ubuntu, and am enjoying it other than the fact that I can't get my wireless working.  Hopefully you guys can walk me through it.

I ran the command:

> "sudo lshw -C network"

and this is what I got:

>   *-network:0             
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 03
       serial: 00:12:3f:f5:41:52
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=full firmware=N/A ip=192.168.1.102 latency=64 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:14:a5:35:c7:e1
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g



It would appear that my wireless is disabled.  There is no switch on my laptop to do this, and it worked fine under Freespire...

Hopefully you guys can get me up and running here.

Thanks!

---

### Post by agim on 2008-04-30
It worked under freespire because linspire, freespire's big brother OS, is something that the company charges for. Part of the money paid for linspire goes to the company to buy all of the nonfree drivers and codecs that make linspire work out of the box.

To get that card working in Ubuntu, you are going to have to download the cards driver and use ndiswrapper to install it.

Although i have heard that in 8.04 there is some broadcom support, so check
System-Administration-Hardware drivers.


Edit:
Wrong place to look. Try this:
System->administration->Network from your main menu

ReEdit:
look under hardware-drivers, then network. Sorry, don't often use this method, so I had to triple check.

---

### Post by Yewni on 2008-05-01
Alrighty...

I checked the drivers section, and found my wireless driver.  When I tried to enable it, it said I'd need the firmware to do so.

Would somebody be kind enough to walk me through this? 

Thanks!

---

### Post by agim on 2008-05-01
try following this post:
[http://ubuntuforums.org/showthread.php?t=769603&highlight=BCM4318](http://ubuntuforums.org/showthread.php?t=769603&highlight=BCM4318)


Edit:
I see on that post that this doesn't always work. If not, use ndiswrapper, which is what I use.

here is a link for that one.

[http://ubuntuforums.org/showthread.php?t=766560&highlight=ndiswrapper+hardy](http://ubuntuforums.org/showthread.php?t=766560&highlight=ndiswrapper+hardy)

---

### Post by Yewni on 2008-05-01
> **agim said:**
> try following this post:
[http://ubuntuforums.org/showthread.php?t=769603&highlight=BCM4318](http://ubuntuforums.org/showthread.php?t=769603&highlight=BCM4318)


Edit:
I see on that post that this doesn't always work. If not, use ndiswrapper, which is what I use.

here is a link for that one.

[http://ubuntuforums.org/showthread.php?t=766560&highlight=ndiswrapper+hardy](http://ubuntuforums.org/showthread.php?t=766560&highlight=ndiswrapper+hardy)

I was able to get it working via the ndiswrapper one.  However, it says in the tutorial that it won't last through a reboot, and the command he gives gave me an error in the terminal.  Anybody know how to make this permanent?

Thanks again!!!


EDIT:  The one that didn't work was this:

> echo -e '\n#hardy ssb bug-fix\nrmmod b43\nrmmod b44\nrmmod b43legacy\nrmmod ssb\nrmmod ndiswrapper\nmodprobe ndiswrapper\nmodprobe ssb' | sudo tee -a /etc/init.d/rc.local


taken from [here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851")

---

### Post by agim on 2008-05-01
it should work after reboot. It was permanent for me. In fact, it tells you to reboot.

What command gave you an error?

---

### Post by Yewni on 2008-05-01
Seemed to work through the reboot, however I did notice some errors during the load up.  Is there a way to log the load-up text so I can post it here to see what it all means?

Thanks.

---

### Post by agim on 2008-05-01
Its funny, I just asked the same on another thread, for a different problem.

[http://ubuntuforums.org/showthread.php?t=776692](http://ubuntuforums.org/showthread.php?t=776692)

So far, no one has answered me either.

Send me the link to show me the steps you followed. There are so many different ways that people post, and sometimes people leave things out.

---

### Post by agim on 2008-05-01
okay, I didn't see your edit until just now.

echo -e '\n#hardy ssb bug-fix\nrmmod b43\nrmmod b44\nrmmod b43legacy\nrmmod ssb\nrmmod ndiswrapper\nmodprobe ndiswrapper\nmodprobe ssb' | sudo tee -a /etc/init.d/rc.local

This is the problem script, and here is a longer, although more thorough way to do the same thing. 

 step 6
 sudo gedit /etc/init.d/wirelessfix.sh
 
 Paste the followings in the opened file(wirelessfix.sh)and make sure you save it before continuing Step 7
 
 #!/bin/bash
 modprobe -r b44
 modprobe -r b43
 modprobe -r b43legacy
 modprobe -r ssb
 modprobe -r ndiswrapper
 modprobe ndiswrapper
 modprobe b44
 
 Step 7 (run in terminal)
 
 Run this :
 
 cd /etc/init.d/ && sudo chmod 755 wirelessfix.sh
 
 Step 8 (run in terminal)
 
 finally run this:
 
 sudo update-rc.d wirelessfix.sh defaults


This is a copy and paste from here.

[http://ubuntuforums.org/showthread.php?t=776812](http://ubuntuforums.org/showthread.php?t=776812)

---

### Post by agim on 2008-05-01
If that did it, marked this thread as solved. That way other people can use the advice.
This question comes up a lot :). This could help limit the number of threads devoted to it.
Welcome to Ubuntu!

---

### Post by Yewni on 2008-05-01
> **agim said:**
> If that did it, marked this thread as solved. That way other people can use the advice.
This question comes up a lot :). This could help limit the number of threads devoted to it.
Welcome to Ubuntu!

My wireless is up and running now, no problems.  You can mark this as solved...

Although I do get some errors when booting down my machine now.  I'll leave that to another thread in a different forum however.

Thanks to everybody who helped me!!!!

---

