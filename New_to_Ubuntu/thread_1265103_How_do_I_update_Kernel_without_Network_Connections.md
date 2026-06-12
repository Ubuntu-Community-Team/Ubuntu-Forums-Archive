---
title: "How do I update Kernel without Network Connections?"
date: 2009-09-13
forum: New to Ubuntu
---

### Post by jamesalroy on 2009-09-13
SUPER Newbee here.  I'm trying to upgrade 8.04, but my nic and wireless are not available?  what can I do.  I have jaunty on another partition, but I don't know what to read to bridge my knowledge with how to solve.  Oh, and 8.04 because I'm taking a Linux class and 8.04 and 8.10 is our OS.  My LT is a Toshiba, P305-S8919.  In Jaunty, everything appears immediately, but I didn't learn a thing.  Kinda want the knowledge more than the result.

---

### Post by sancho panza on 2009-09-13
Please help us to help you by being more precise and detailed about what exactly the problem is and what it is that you wish to fix.

Cheers,

---

### Post by jamesalroy on 2009-09-13
My nic or wireless is not listed as a connection in Hardy.

---

### Post by sancho panza on 2009-09-13
Please provide details as to what wireless card you have. Maybe posting the output of the "ifconfig" command in the terminal might help.

Cheers,

---

### Post by jamesalroy on 2009-09-13
This is from Hardy:

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1922 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1922 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:96100 (93.8 KB)  TX bytes:96100 (93.8 KB)



This is from Jaunty:

eth0      Link encap:Ethernet  HWaddr 00:23:8b:a7:e5:15  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:22:fa:49:83:9e  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::222:faff:fe49:839e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:72 errors:0 dropped:0 overruns:0 frame:0
          TX packets:47 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10441 (10.4 KB)  TX bytes:7521 (7.5 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-22-FA-49-83-9E-33-39-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by coffeeaddict22 on 2009-09-13
If you're looking for knowledge, you'll probably get it messing around with the wireless networking.  The ifconfig output you've given shows there is no active driver for the card.
From personal experience, a lot of the cards were still using ndiswrapper prior to 8.10; in 8.10 a lot of drivers moved into the kernel.  The fun began because if you upgrade to a new version, your /home folder stays untouched... and that's where ndiswrapper hides its setup files.

There's a good wireless troubleshooter at [the wiki]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide") as well as a few other pages in there; the main catch is that with the rapid state of flux in wireless, some of it is "deprecated" so be a bit careful.

From your ifconfig output, we next need to know what's happening in terms of drivers. lshw -C network should tell you what you need to know; post it back if you want more assistance.

---

### Post by r.osmanov on 2009-09-13
I had very similar problem few months ago. 

To solve the network problem is definitely needed. But the question actually was to move packages from one box to another. 

[**AptOnCD**]("http://aptoncd.sourceforge.net/download.html") is very handy. I use it often, since I've similar situation.
The application creates an ISO image with **.deb** packages installed on current PC. 
AptOnCD features both restore from ISO and from CD/DVD. It's interface is straightforward.

However, if something went wrong when you "restored" packages, you could use the following procedure.

ISO file generated with AptOnCD contains a folder called "packages".
The folder contains .deb files. So you can mount ISO and install just what you want:
```
# Type in terminal
cd /path/to/iso/image.iso
mkdir /media/iso
sudo mount image.iso /media/iso -o loop
# ...you can use "mount" command to see what is currently mounted on the system
ls /media/iso # see what is in ISO
```Then you can make everything with DEBs. E.g. you have something.deb in ISO. To install it you can type:
```
mkdir /tmp/deb
cd /tmp/deb
cp /media/iso/something.deb ./
sudo dpkg -i something.deb
```To unmount the image use "unmount" command:
```
sudo unmount /media/iso/
```Good luck.

---

### Post by jamesalroy on 2009-09-13
This is from Jaunty, do you what the output from Hardy too?

*-network
       description: Wireless interface
       product: Wireless WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 00
       serial: 00:22:fa:49:83:9e
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=192.168.1.101 latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
  *-network
       description: Ethernet interface
       product: 88E8040T PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 12
       serial: 00:23:8b:a7:e5:15
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 46:0d:95:66:1c:75
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by coffeeaddict22 on 2009-09-13
Don't worry about the output from Hardy.  The wireless drivers have come a long way in the last 12 months, so it's not likely to help.

wmaster0 is the base wireless channel, used to make the actual device driver invisible to the system- have a look at [this]("http://linuxwireless.org/en/developers/Documentation/mac80211#The_master_device_wmaster0").  However, it's about to be deprecated.  It can be OK, but if you can't see your wireless on another logical name it's usually not so good.

I've run into this with ndiswrapper causing conflicts before.  open a terminal and type ```
lsmod
```; you should be able to see the wireless drivers in there.  If ndiswrapper is there, then do ```
sudo modprobe -r ndiswrapper
```; post back if you need more help.  If you get a terminal command you aren't sure of, type into a terminal ```
man xxxx
``` where xxxx is the command; it'll give you a heap of information on the command.
The reason ndiswrapper causes so many 'learning experiences' is it keeps a startup script in the /home folder; that isn't touched when you upgrade your distro (by design), but the wireless drivers moved into the kernel recently, so now you get a conflict.  

The comment by r.osmanov is also correct; however, you need to be running the same system on both boxes.  Don't use an APT-on CD to take programs from a 32 to 64 bit system, and you can try moving them between Hardy and Jaunty, but the repositories are different for a reason, so don't be surprised if bad things happen.

---

### Post by jamesalroy on 2009-10-12
Mr. Coffee,

I ran the lsmod on Hardy -- no entries for ndiswrapper, there was an entry in Jaunty,  then I did some reading on the link you listed.  Followed it to here.

[http://marc.info/?l=linux-wireless&m=125487834518318&w=2](http://marc.info/?l=linux-wireless&m=125487834518318&w=2)

Should I turn this page into a script?

---

