---
title: "wired connection suddenly stopped working"
date: 2008-08-06
forum: Networking &amp; Wireless
---

### Post by Pacopag on 2008-08-06
Hi.
My wired connection was working fine.  Now suddenly it isn't working.  It says that it is connected to the wired network, but when I look at connection information, everything is 0.0.0.0  (ip address etc). But the wireless works fine.

Any help?

---

### Post by pytheas22 on 2008-08-06
You could try getting an IP manually.  What does:
```

sudo dhclient -r eth0
sudo dhclient eth0
```

say?

If that doesn't get you an IP, please provide the output of:
```

ifconfig
lspci -nn
lshw -C Network
```

so that we can investigate more.

---

### Post by Pacopag on 2008-08-06
sudo dhclient -r eth0

gives the output

Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:1c:23:54:d7:f3
Sending on   LPF/eth0/00:1c:23:54:d7:f3
Sending on   Socket/fallback

sudo dhclient eth0

gives the output

There is already a pid file /var/run/dhclient.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:1c:23:54:d7:f3
Sending on   LPF/eth0/00:1c:23:54:d7:f3
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

ifconfig

gives output

eth0      Link encap:Ethernet  HWaddr 00:1c:23:54:d7:f3  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:949187772195 overruns:0 frame:0
          TX packets:0 errors:0 dropped:184 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:251 

eth1      Link encap:Ethernet  HWaddr 00:1f:e1:3c:ca:4a  
          inet addr:192.168.0.104  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:e1ff:fe3c:ca4a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:898 errors:0 dropped:0 overruns:0 frame:29646
          TX packets:541 errors:11 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:774341 (756.1 KB)  TX bytes:91328 (89.1 KB)
          Interrupt:19 

eth0:avahi Link encap:Ethernet  HWaddr 00:1c:23:54:d7:f3  
          inet addr:169.254.9.122  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:251 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1519 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1519 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:77481 (75.6 KB)  TX bytes:77481 (75.6 KB)

lspci -nn

gives

00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a02] (rev 0c)
00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a03] (rev 0c)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 03)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 [8086:2845] (rev 03)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 [8086:2847] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 03)
06:00.0 Network controller [0280]: Broadcom Corporation BCM4310 USB Controller [14e4:4315] (rev 01)
07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev ff)
08:05.0 FireWire (IEEE 1394) [0c00]: O2 Micro, Inc. Firewire (IEEE 1394) [1217:00f7] (rev 02)
08:05.2 SD Host controller [0805]: O2 Micro, Inc. Integrated MMC/SD Controller [1217:7120] (rev 02)
08:05.3 Mass storage controller [0180]: O2 Micro, Inc. Integrated MS/xD Controller [1217:7130] (rev 01)

lshw -C Network

gives

  *-network               
       description: Wireless interface
       product: BCM4310 USB Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth1
       version: 01
       serial: 00:1f:e1:3c:ca:4a
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl ip=192.168.0.104 latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
  *-generic
       description: Ethernet interface
       product: Illegal Vendor ID
       vendor: Illegal Vendor ID
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: ff
       serial: 00:1c:23:54:d7:f3
       size: 1GB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master vga_palette cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full latency=255 link=yes maxlatency=255 mingnt=255 module=r8169 multicast=yes port=twisted pair speed=1GB/s

---

### Post by pytheas22 on 2008-08-06
If you run these commands:
```

sudo ifconfig eth0 down
sudo ifconfig eth0 up
```

does the ethernet work?  If not, please try:
```

sudo rmmod r8169
sudo modprobe r8169
sudo ifconfig eth0 up
```

If neither of those things helps, there's still other stuff to try, but hopefully the above will do it.

---

### Post by Pacopag on 2008-08-06
Yep.  The first thing worked.  Thank you very much.

---

### Post by pytheas22 on 2008-08-06
Glad to hear it--actually I should have told you to try that first; this ended up being a lot simpler than I thought.

If your ethernet is broken again the next time you reboot your computer and you need to run those commands again to fix it, let me know and we can fix it permanently.

---

### Post by Pacopag on 2008-08-06
You guessed it.  Upon rebooting I get the same problem.  How can I fix this once and for all?

---

### Post by pytheas22 on 2008-08-06
Not too difficult to fix permanently.  Write a script to run those commands at boot.

1. open up the file:
```

sudo gedit /etc/init.d/ethernet-fix.sh
```

A file will open.  Add to it these lines:
```

#!/bin/bash
#this file fixes ethernet

ifconfig eth0 down
ifconfig eth0 up
```

Then save and close the file.

2. make the file get run at boot:
```

sudo -s
cd /etc/init.d
chmod +x ethernet-fix.sh
update-rc.d ethernet-fix.sh defaults
```

That should do it.  Let me know if it doesn't.

---

### Post by Pacopag on 2008-08-06
Nope.  It didn't work.

---

### Post by pytheas22 on 2008-08-06
hmmm, maybe those commands need to be run later for some reason, like after the system has booted completely instead of during boot.  What if you change the file /etc/init.d/ethernet-fix.sh to:
```

#!/bin/bash
#this file fixes ethernet

ifconfig eth0 down
ifconfig eth0 up
ifconfig eth0 down
ifconfig eth0 up
ifconfig eth0 down
ifconfig eth0 up
```

Does that make it any better?  If not, just to confirm, if you run the ifconfig eth0 up/down commands after you've logged into Gnome, the connection works fine then, right?

---

### Post by Pacopag on 2008-08-06
Well.  It works sometimes, but not others.  The good news is that this is a relatively new install of ubuntu, so I'm not going to cry about if I have to re-install ubuntu.  But before I do that, is there anything else that I can try?

---

### Post by pytheas22 on 2008-08-06
So I guess the ifconfig eth0 up/down stuff doesn't seem to fix it after all?  You could see if these commands help (if you didn't already):
```

sudo rmmod r8169
sudo modprobe r8169
sudo ifconfig eth0 up
```

That would reinsert the driver, which may make a difference.  Otherwise, reinstalling Ubuntu may be the simplest way out of this, although we could troubleshoot it more on this installation if you prefer (looking at dmesg for information on why eth0 crashes would be the next step).

---

### Post by Pacopag on 2008-08-06
Well, I've already re-installed ubuntu, and to my great delight, the wired connection still isn't working.  It seems like it's just not getting an ip address.  I'll try those commands you gave me.  Thanks.

---

### Post by Pacopag on 2008-08-06
That didn't work either.  It said something like the device couldn't be found when I did
ifconfig eth0 up.

I re-installed ubuntu again, but I still have the same problem.

---

### Post by pytheas22 on 2008-08-06
> Well, I've already re-installed ubuntu, and to my great delight, the wired connection still isn't working. It seems like it's just not getting an ip address. I'll try those commands you gave me. Thanks

Just to rule out a couple of other things:

1. do you have Windows on the same machine, and if so does the ethernet work there?  This would rule out hardware failure, which is a possibility.  The fact that the device broke all of a sudden in Ubuntu isn't that surprising--normally I'd say that either an update or some other change to the system broke it--but if it's also not working on a fresh install, where the configuration should be identical to what it was when the card was working, then I'd want to look into hardware failure as the problem.

2. are you sure it's not a problem with your router?  Are there other wired devices on your network and if so do they work?  Did you try rebooting your router or using a different ethernet cable just to be sure?

Otherwise, see if removing the driver helps.  I'm sorry this wasn't as simple as we thought a few hours ago.

---

### Post by Pacopag on 2008-08-06
Yes I have windows on the same system and it works fine there.  I also tried disconnecting the router and plugging straight into the modem, but that didn't work either.  Very strange.  I would have thought that a fresh install would have fixed it for sure.

---

### Post by pytheas22 on 2008-08-07
Strange.  If you want to keep troubleshooting this, could you please post the output of this stuff on your newly installed system, after a fresh reboot into Ubuntu:
```

lsmod | grep 8169
lshw -C Network
ifconfig
sudo rmmod r8169
sudo modprobe r8169
sudo ifconfig eth0 up
```

Also, maybe you want to remove the SOLVED tag from this thread so that others can jump in if they have more ideas...

---

### Post by Pacopag on 2008-08-07
Look.  pytheas.  I really appreciate your help.  But the computer with the problem actually belongs to my brother.  I'm trying to turn him into a linux guy.  But this is not a good way for him to start out, and he's become scared, and sadly just wants to put windows on his computer now.  It's really too bad.  I love my Ubuntu box, and I've never encountered a problem that the good people of this forum couldn't help me fix.  I am completely confident that you would have found the solution to this problem if we put in a little more time.  Thank you so much for your time and effort.

---

### Post by pytheas22 on 2008-08-07
In that case, sorry it didn't work out, but I hope you can convince your brother to give Linux another shot some other time...

---

### Post by frmdstryr on 2009-08-11
if you see this, i still have this problem.  I used to have it in 8.04 where anytime i used dhcp i wouldn't be able to connect to anything but i could get it to work by using a manual connection.  Now I upgraded to 9.04 and the manual way wont work anymore... the internet worked fine from fresh install. Works with windows, got same responces with "sudo dhclient eth0"... 
help me please! thanks.

---

### Post by pytheas22 on 2009-08-11
> **frmdstryr said:**
> if you see this, i still have this problem.  I used to have it in 8.04 where anytime i used dhcp i wouldn't be able to connect to anything but i could get it to work by using a manual connection.  Now I upgraded to 9.04 and the manual way wont work anymore... the internet worked fine from fresh install. Works with windows, got same responces with "sudo dhclient eth0"... 
help me please! thanks.

Do you have a manual IP set currently?  What is the output of:
```

cat /etc/network/interfaces
ifconfig
lshw -C network
dmesg | grep -e rtl -e eth
```

---

