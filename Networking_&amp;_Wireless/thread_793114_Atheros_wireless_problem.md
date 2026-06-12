---
title: "Atheros wireless problem"
date: 2008-05-13
forum: Networking &amp; Wireless
---

### Post by vedran.omeragic on 2008-05-13
I'm trying to set up network, but I'm having problems with my network card, which is atheros 802.11

I have searched forums and tried this below, as shown in [**this thread**]("http://ubuntuforums.org/showthread.php?t=225290")

> 

[QUOTE]
sudo gedit /etc/network/interfaces
Edit the file and add these lines (delete all the other stuff that's in there):
> 
auto lo
iface lo inet loopback

auto ath0
iface ath0 inet dhcp
wireless-essid Strong

Save the file and restart your network:
> 
sudo /etc/init.d/networking restart
Ideally this should be it.
[/QUOTE]
When I do the final step, and restart the network, I get following message:

>  * Reconfiguring network interfaces...                                          ath0: ERROR while getting interface flags: No such device
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device ath0 ; No such device.
There is already a pid file /var/run/dhclient.ath0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.


How can I fix this? and how can device possibly not exist (be detected)?
Thank you

---

### Post by dmizer on 2008-05-13
post the output of:
```
ifconfig
```

as well as the output of:
```
lshw -C network
```

---

### Post by vedran.omeragic on 2008-05-14
**ifconfig**
> eth0      Link encap:Ethernet  HWaddr 00:1b:38:3d:20:c1  
          inet addr:10.0.20.201  Bcast:10.0.20.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:38ff:fe3d:20c1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4291443 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4378464 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2359206581 (2.1 GB)  TX bytes:2784022571 (2.5 GB)
          Interrupt:220 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2535 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2535 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:169164 (165.1 KB)  TX bytes:169164 (165.1 KB)

[B]
lshw -C network[/B]

>   *-network               
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0e:00.0
       logical name: eth0
       version: 01
       serial: 00:1b:38:3d:20:c1
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=10.0.20.201 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:14:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0


---

### Post by dmizer on 2008-05-14
according to [this thread](http://ubuntuforums.org/showthread.php?t=743299) you'll need to use ndiswrapper to drive your card.

blacklist the native driver:
```
echo "blacklist ath_pci" | sudo tee -a /etc/modprobe.d/blacklist
```

then take a look at this page for how to configure ndiswrapper: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?)

---

### Post by Paris Heng on 2008-05-14
After blacklist, you may use Madwifi as well.

---

### Post by vedran.omeragic on 2008-05-14
OK, once I get to the part 3.4.2. where I have to install new driver:

> vedran@root:~$ sudo ndiswrapper -i /home/vedran/atheros/Install/net5211.inf
installing net5211 ...
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64

Then in section 3.4.2.1. where I check if installation was correct, I don't get either of two messages, which means I have not install right driver. I've tried searching but I just can't seem to find the right one. 
Here is more info on my driver in ID:

> 14:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
14:00.0 0200: 168c:001c (rev 01)

---

### Post by dmizer on 2008-05-14
go here: [http://www.atheros.cz/](http://www.atheros.cz/) and download the windows XP driver corresponding to your card.  it will be one of these:

AR5006EG
AR5006EGS
AR5006EX
AR5006EXS

---

