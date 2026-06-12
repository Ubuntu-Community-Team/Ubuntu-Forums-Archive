---
title: "Broadcom 4318 Rev 2 Wireless Help."
date: 2008-05-06
forum: Networking &amp; Wireless
---

### Post by andybob on 2008-05-06
Hey all:

I have been having many issues getting my wireless card to work.  I did the whole tutorial that is posted in here for Broadcom cards ad I still can't get it to work.  I am near my wits end with this and I would love to get if figured out because I LOVE Ubuntu.

Here is my iwconfig:

> andybob@andybob-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

It knows it is there.

Here is the sudo lshw -C network

> andybob@andybob-laptop:~$ sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:14:22:8e:be:d8
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=74.74.96.204 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
  *-network:1
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
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:14:a5:3e:50:e3
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

And lastly here is the lspci:
> 
andybob@andybob-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

Alright, so I installed ndiswrapper with all the Drivers like the tutorial said, restarted my computer, clicked on the network icon in the Gnome display and there aren't any networks listed.

So then I go to "Connoct to another wireless network" enter the Essid and the password and nothing happens.  It will go for a while and then a dialoge boc comes up saying I have to enter then password again and it never works.  Is there something I am missing???? Any help is wonderfully appreciated.

Thanks,


Andybob

---

### Post by agim on 2008-05-06
did the tutorial you followed include adding the file wirelessfix.sh and running it?

If not, check this post. There is an extra step in Hardy. In that post, see steps 5 through 8.

---

### Post by andybob on 2008-05-06
> **agim said:**
> did the tutorial you followed include adding the file wirelessfix.sh and running it?

If not, check this post. There is an extra step in Hardy. In that post, see steps 5 through 8.

Yep, did it.  Should I re-do the whole thing?


Andybob

---

### Post by agim on 2008-05-06
I don't understand what wmaster0 is in your iwconfig output. It might be whats causing the trouble.

---

### Post by Ayuthia on 2008-05-06
From you lshw -C network information, it looks like the b43 and ssb are still loaded.  You might also want to check ndiswrapper -v and ndiswrapper -l to make sure that ndiswrapper is happy in the version and has a proper driver.

You can try and see if your wireless turns on by doing:
```
sudo modprobe -r b43 ssb
sudo modprobe ndiswrapper
```

---

### Post by andybob on 2008-05-06
Sudo Modprobe -r b43 ssb output:
> 
andybob@andybob-laptop:~$ sudo modprobe -r b43 ssb
FATAL: Module ssb is in use.

I did the > sudo modprobe ndiswrapper as well and nothing happened.


Andybob

---

### Post by andybob on 2008-05-06
ndiswrapper -v output:
> 
andybob@andybob-laptop:~$ ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.24-16-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.52
vermagic:       2.6.24-16-generic SMP mod_unload 586

ndiswrapper -l output:

> andybob@andybob-laptop:~$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4318) present (alternate driver: bcm43xx)



Andybob

P.S. I appreciate your help.

---

### Post by Ayuthia on 2008-05-06
Sorry, I missed the information in your lspci that you had a Broadcom wired.  Try:
```
sudo modprobe -r b43 b44 ssb
sudo modprobe ndiswrapper
```

---

