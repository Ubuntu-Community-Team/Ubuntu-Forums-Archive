---
title: "Wireless problem"
date: 2010-02-02
forum: New to Ubuntu
---

### Post by Nytehawk on 2010-02-02
Hi

I've just installed a dualboot with vista/ubuntu 9.10 and I'm quite happy. But in Ubuntu the wireless won't work at all.

I have a switch with an indicator light that shows if the wireless is on/off and allows to quickly turn it on/off. In vista it works, but in ubuntu it's off and pressing the button does not help. My computer is an acer aspire 2920Z. 

I have been to System> Admin> Hardware Drivers but there where no drivers to install.

The following is answers to questions I've seen asked about similar things:

lspci:
> 00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
04:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)sudo lshw -C network
>   *-network               
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:72:0d:2c:00
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.99 duplex=full firmware=5787m-v3.23 ip=192.168.1.16 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:29 memory:f6000000-f600ffff
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list
       configuration: latency=0
       resources: memory:f8000000-f800ffff
sudo iwlist scan
> lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.


---

### Post by spiderbatdad on 2010-02-02
This wireless card should be working automatically. Include a post of ```
dmesg | tail
```after rebooting, but try the following first:
```
sudo modprobe ath5k
sudo /etc/init.d/networking restart
```

---

### Post by Nytehawk on 2010-02-02
It worked! Thank you so much! :D

---

### Post by spiderbatdad on 2010-02-02
I don't know if the problem will occur again. I have a file in /etc/modprobe.d call "blacklist-ath_pci.conf"

The contents of the file are:
```
# For some Atheros 5K RF MACs, the madwifi driver loads buts fails to
# correctly initialize the hardware, leaving it in a state from
# which ath5k cannot recover. To prevent this condition, stop
# madwifi from loading by default. Use Jockey to select one driver
# or the other. (Ubuntu: #315056, #323830)
blacklist ath_pci

``` You may need to create this file and include the blacklist ath_pci line if you don't have the file and the problem recurs.

---

### Post by Tholley on 2010-02-02
Sorry to hijack this thread, but I have been trying to fix a similar problem for months!
 
I have been trying to get wireless on Jaunty with a Linksys pci adapter, it says I have the driver RT61 installed, but when I open ndisgtk, I get a msg stating "Could not find a network configuration tool." and no network.
 
I found a bug report here ([https://bugs.launchpad.net/ndisgtk/+bug/500541](https://bugs.launchpad.net/ndisgtk/+bug/500541)) that says it is fixed??? Don't know what or if I need to do anything on that. 
 
Here is my lshw output
 
```
kaylen@kaylen-desktop:~$ sudo lshw -C network
[sudo] password for kaylen: 
*-network 
description: Ethernet interface
product: nForce2 Ethernet Controller
vendor: nVidia Corporation
physical id: 4
bus info: pci@0000:00:04.0
logical name: eth0
version: a1
serial: 00:0d:87:48:c0:aa
size: 100MB/s
capacity: 100MB/s
width: 32 bits
clock: 66MHz
capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=192.168.1.103 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
*-network UNCLAIMED
description: Network controller
product: RT2561/RT61 802.11g PCI
vendor: RaLink
physical id: 4
bus info: pci@0000:01:04.0
version: 00
width: 32 bits
clock: 33MHz
capabilities: pm cap_list
configuration: latency=32
*-network DISABLED
description: Ethernet interface
physical id: 1
logical name: pan0
serial: 42:83:d4:fc:e3:87
capabilities: ethernet physical
configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
kaylen@kaylen-desktop:~$ iwlist scan
lo Interface doesn't support scanning.
 
eth0 Interface doesn't support scanning.
 
pan0 Interface doesn't support scanning.

```
 
Will the solution earlier help with mine also? 
 
Thanks!

---

### Post by spiderbatdad on 2010-02-02
Sorry it will not. The above was to load a module specifically for the Atheros wireless card the op has. I don't even see a wireless interface described in your output. I do see unclaimed controller....maybe that's it.

Unclaimed suggests the driver isn't loaded. I'll google around a little to see if I can help you. Maybe someone else will chime in, but it is better to start your own thread, or bump an old thread if you have one going.

---

### Post by Tholley on 2010-02-02
thanks,
 
I have one thing I will try when I get home, Installing gnome-network-admin package from Synaptic, which I googled and found. 
 
If that doesn't fix the prob, then I'll start "another" new thread... and see if I can catch someone who can help this time around.
 
Thanks again!

---

### Post by Nytehawk on 2010-02-03
The problem reappeared again.  

I checked and I have the file "blacklist-ath_pci.conf" and at the end I have the "blacklist ath_pci"-line. 

What can I do to stop this from happening every time I restart?

And thanks again! :)

---

