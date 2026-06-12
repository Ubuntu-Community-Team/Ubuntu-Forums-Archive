---
title: "My eth0 has disappeared"
date: 2008-03-29
forum: Networking &amp; Wireless
---

### Post by steveasman on 2008-03-29
Today when I booted up my Ubuntu 7.10 machine I was unable to connect to my network or the internet. It was working fine yesterday.

 Network manager now indicats that there is no ethernet on the machine.  The cable is plugged in and the lights are lit and flashing as they normally do.

My machine's specs:

Motherboard: Intel D915GAV with Intel 82562EZ 10/100 integrated ethernet.

I've tried the following commands and gotten these results:

root@gutsy:/home/asman# ifconfig -a
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

root@gutsy:/home/asman# lspci
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation 82915G Integrated Graphics Controller (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
06:01.0 USB Controller: NEC Corporation USB (rev 43)
06:01.1 USB Controller: NEC Corporation USB (rev 43)
06:01.2 USB Controller: NEC Corporation USB 2.0 (rev 04)

root@gutsy:/home/asman# lshw -C network
root@gutsy:/home/asman#   

root@gutsy:/home/asman# /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                                   eth0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth0.

It looks like it's just not recognizing the ethernet interface anymore.

I haven't made any changes to the machine except applying updates.

Does anybody have any suggestions as to what I should try next?

---

### Post by unknown03 on 2008-03-29
do you know what driver is used for it?

when i tried installing ndiswrapper and getting it to work, it would erase all recollection of my eth1

but in the terminal i typed:

modprobe -r b44
modprobe -r b43
modprobe -r ssb
modprobe -r ndiswrapper
modprobe b44
modprobe ndiswrapper

and that seemed to get it recognized again..

not sure if that helps, but its worth a shot...replace "b44" "b43" etc with your installed driver..in my case, "bcm43xx" was used (b43 for short, or atleast what modprobe recognized)

---

### Post by steveasman on 2008-04-01
Well, today I started it up and all is working fine.  Perhaps a hardware issue?

---

