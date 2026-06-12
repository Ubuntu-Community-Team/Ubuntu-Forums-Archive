---
title: "WLAN on Omnibook 510"
date: 2009-11-28
forum: New to Ubuntu
---

### Post by jalve on 2009-11-28
Could somebody be so kind and help me get WLAN working on HP Omnibook 510 with Ubuntu 9.10? It shows up as DISABLED with lshw even though the blue WLAN light is on.

I remember years ago (maybe with version 7.10?) I managed to get WLAN working after googling around for instructions. The solution was something close to the following:

#!/bin/sh

modprobe prism2_usb prism2_doreset=1
wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable
wlanctl-ng wlan0 lnxreq_autojoin ssid=<your-ssid> authtype=opensystem
/sbin/dhcpcd -t 10 -d wlan0

However, now I get the error message wlanctl-ng is not installed, and a suggestion to type

sudo apt-get install linux-wlan-ng

which will result in the following error message:

E: couldn't find package linux-wlan-ng

Now what should I do?

---

### Post by Tiberion on 2009-11-29
you probably have a broadcom chipset open source dirvers are somewhat unreliable.  install the proprietary drivers for broadcom.  Enable all archieve sources in software sources under system/admin.  Then run from terminal sudo apt-get install update.  Then go to system/admin/hardware drivers.  From here you should have a driver listed for broadcom.  enable it.  That should do it






 			 		
  		 	  	 	 		[RIGHT] 			21 Minutes Ago 
			by [TuxIsCute]("http://ubuntuforums.org/member.php?find=lastposter&t=1341223")  [[IMG]http://ubuntuforums.org/images/buttons/lastpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=8408677#post8408677") 		[/RIGHT]
  	 	  	 		[0]("http://ubuntuforums.org/misc.php?do=whoposted&t=1341223") 		1  		 			[Absolute Beginner Talk]("http://ubuntuforums.org/forumdisplay.php?f=326") 		 	  	     		 		[IMG]http://ubuntuforums.org/images/statusicon/thread_new.gif[/IMG] 	 	 		[IMG]http://ubuntuforums.org/images/icons/icon4.gif[/IMG] 	 	      		 		 			 				 					tags: monitor, monitor problems, problems with monitor 					 					 					 					 					 					 				 			 			[[IMG]http://ubuntuforums.org/images/buttons/firstnew.gif[/IMG]]("http://ubuntuforums.org/showthread.php?goto=newpost&t=1341214") 			 			 			                         [COLOR=#D15600]**[xubuntu]**[/COLOR] 			 			[Monitor turns off after 5 minutes]("http://ubuntuforums.org/showthread.php?t=1341214") 			 		
  		  		 			 			 				Spiffjiggins 			 		
  		 	  	 	 		[RIGHT] 			30 Minutes Ago 
			by [Spiffjiggins]("http://ubuntuforums.org/member.php?find=lastposter&t=1341214")  [[IMG]http://ubuntuforums.org/images/buttons/lastpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=8408641#post8408641") 		[/RIGHT]
  	 	  	 		[0]("http://ubuntuforums.org/misc.php?do=whoposted&t=1341214") 		1  		 			[Absolute Beginner Talk]("http://ubuntuforums.org/forumdisplay.php?f=326")hipset in your wireless card.

---

### Post by jalve on 2009-12-02
Thanks for trying to help me. Unfortunately after following your instructions, I again get the error message "E: Couldn't find package update."

I don't think I have a Broadcom chip. Last time it was following the Actiontec Prism instructions that worked (sort of - I vagely remember I had to do something else, too, like give the chip a reset or something).

---

### Post by jalve on 2009-12-02
Here's what lshw -C network returns:

lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82801CAM (ICH3) PRO/100 VM (KM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth0
       version: 42
       serial: 00:c0:9f:13:56:76
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI firmware=N/A ip=10.0.0.7 latency=66 maxlatency=56 mingnt=8 multicast=yes
       resources: irq:10 memory:e0200000-e0200fff ioport:2400(size=64)
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: wlan0
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

Is it normal that wlan0 has "ethernet physical" as its capabilities, just like the wired Ethernet?

---

### Post by jalve on 2009-12-03
lsusb confirms it's Actiontec:
lsusb
Bus 003 Device 002: ID 1668:0408 Actiontec Electronics, Inc. [hex] Prism2.5 802.11b Adapter
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

