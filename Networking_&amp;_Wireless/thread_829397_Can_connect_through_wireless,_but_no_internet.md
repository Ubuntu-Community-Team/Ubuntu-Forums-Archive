---
title: "Can connect through wireless, but no internet"
date: 2008-06-14
forum: Networking &amp; Wireless
---

### Post by CC_Joe on 2008-06-14
Hi everyone! I just installed 8.04 on my laptop. I am a complete newbie, so I'm having a little bit of trouble. I'm using a hp pavillion dv9000, and I used Ndiswrapper to get the correct drivers for my broadcom card. I think I did that correctly: when I first installed 8.04 I couldn't find any wireless networks (or even a wireless card) and now I can see my network! I can even connect to it, but when I use a browser I can't surf the web. Anyone know what's going on?

I lurked on the forums a bit, so I think you might need this:

joe@Snow-Crash:~$ sudo lshw -C network
[sudo] password for joe: 
  *-network               
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 02
       serial: 00:1a:73:76:f9:e7
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=0 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g


and this:

joe@Snow-Crash:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1b:24:6c:e8:1e  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5743 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5456 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5966602 (5.6 MB)  TX bytes:781840 (763.5 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:171 errors:0 dropped:0 overruns:0 frame:0
          TX packets:171 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8825 (8.6 KB)  TX bytes:8825 (8.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1a:73:76:f9:e7  
          inet6 addr: fe80::21a:73ff:fe76:f9e7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:99 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:18086 (17.6 KB)
          Interrupt:20 Memory:b6000000-b6004000 

If anyone can point me in the right direction, it'd be much appreciated!

-Joe

---

### Post by CC_Joe on 2008-06-14
Ok, so I think I might have broke it further. I was thinking maybe I was getting interference between ndiswapper and ssb because:

ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4311) present (alternate driver: ssb)

So I did the following steps from [http://ubuntuforums.org/showthread.php?t=827799]("http://ubuntuforums.org/showthread.php?t=827799"):

> 3)Setup ndiswrapper to load driver (and itself) at startup

* Edit the following file:
Code:

sudo gedit /etc/modules

* Add a line which says:
Code:

ndiswrapper

* Restart


)

3)After you are done, run
#sudo gedit /etc/init.d/ndiswrapperfix.sh
and paste the following

#!/bin/bash

modprobe -r b44
modprobe -r b43
modprobe -r b43legacy
modprobe -r ssb
modprobe -r ndiswrapper
modprobe ndiswrapper
modprobe b44

into the file. Save and close (It will stop causing ssb and ndiswrapper interference)

4)Then run
#cd /etc/init.d/ && sudo chmod 755 ndiswrapperfix.sh

5)Lastly run
#sudo update-rc.d wirelessfix.sh defaults


Restart and enjoy your wireless.I am enjoying hope u ll too.

Now, I don't think this fixed the ssb interference, because ndiswrapper -l still mentions ssb. And I have a new problem: I can't connect to my wireless router anymore. Before, my problem was that I could connect but couldn't surf. Now when I try to connect the network manager just continuously says "waiting for network key."

Blargh! Anyone with ideas?

---

### Post by CC_Joe on 2008-06-15
Hah, caught the problem. Turns out my router was using 64-bit encryption, and I was telling ubuntu it was 128-bit encryption. Changing that solved my problem.

Lol.

---

