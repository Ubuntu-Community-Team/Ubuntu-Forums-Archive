---
title: "Acer 6920 attansic L1 network problem"
date: 2008-06-17
forum: Networking &amp; Wireless
---

### Post by medesand on 2008-06-17
Hi .
I have install ubuntu on my laptop acer aspire 6920 ..
and I HAVE NO NETWORK
attansic L1 is the name of the card.

what can i do ? pls help !

---

### Post by chili555 on 2008-06-17
I think the driver for this is *atl1.* Please open a terminal and do:```
sudo modprobe atl1
sudo ifconfig eth0 up
sudo dhclient eth0
```Did you get an IP address? Let us know and, if it worked, we'll try to make this permanent.

---

### Post by medesand on 2008-06-17
I am new in linux .. so 
it says :



dan@dan-laptop:~$ sudo modprobe atl1

dan@dan-laptop:~$ sudo ifconfig eth0 up
 eth0: ERROR while getting interface flags: No such device

dan@dan-laptop:~$ sudo dhclient eth0

Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.

All rights reserved.
For info, please visit 
[http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: 
unknown hardware address type 801
SIOCSIFADDR: 
No such device
eth0: ERROR while getting interface flags: 
No such device
eth0: ERROR while getting interface flags: 
No such device
wmaster0: 
unknown hardware address type 801
Bind socket to interface: 
No such device

dan@dan-laptop:~$ 

I don`t have an ip adress

---

### Post by chili555 on 2008-06-17
Well, I hoped we could fix it quickly and easily, but no such luck. Please show us:```
ifconfig
sudo lshw -C network
```I assume you have not rebooted since you modprobed atl1.> attansic L1 is the name of the card.
That's a wired ethernet card. Is that the interface you want to activate?

Thanks.

---

### Post by medesand on 2008-06-17
dan@dan-laptop:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1758 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1758 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:87900 (85.8 KB)  TX bytes:87900 (85.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1d:e0:8a:63:fb  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-1D-E0-8A-63-FB-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


dan@dan-laptop:~$ sudo lshw -C network
  *-network UNCLAIMED     
       description: Ethernet controller
       product: Attansic Technology Corp.
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: b0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list
       configuration: latency=0
  *-network
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: wmaster0
       version: 61
       serial: 00:1d:e0:8a:63:fb
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl4965 latency=0 module=iwl4965 multicast=yes wireless=IEEE 802.11g
dan@dan-laptop:~$

---

### Post by medesand on 2008-06-17
> **chili555 said:**
> Well, I hoped we could fix it quickly and easily, but no such luck. Please show us:```
ifconfig
sudo lshw -C network
```I assume you have not rebooted since you modprobed atl1.That's a wired ethernet card. Is that the interface you want to activate?

Thanks.

Yes

I don`t have a wired network .. even if i plug in the network cable.
wired network is missing

---

### Post by chili555 on 2008-06-17
We are trying to undo this:> *-network UNCLAIMED Usually, the hardware will be 'claimed' when the correct driver is loaded. Generally, we also get a logical name, typically, for an ethernet device, eth0. Here is mine:> *-network               
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       ---snip--- 
       driver=e1000
       ---snip---We already modprobed *atl1* and changed nothing apparently. Please do:```
sudo rmmod atl1
sudo modprobe atl2
sudo lshw -C network
```Has UNCLAIMED gone away?> even if i plug in the network cable.We are not going to get anywhere without the cable attached. Before you do anything, attach the cable and do not remove it.

---

### Post by medesand on 2008-06-17
done that .. Stil network UNCLAIMED

---

### Post by chili555 on 2008-06-18
Something is weird here. May we please see:```
dmesg | grep -i Attansic
```Thanks.

---

### Post by medesand on 2008-06-18
125.476055   Attansic L2 Ethernet Network Driver - ver. 1.0.40.2
125.476063   Copyright 2006 Attansic Corporation

---

### Post by chili555 on 2008-06-18
If it doesn't work with *atl1* or *atl2* (admittedly, *atl2* was a shot in the dark), then we must reach into the warp core. I was searching and found what looks to me to be a German site discussing the Attansic card on an Acer 6920! The last post here, the one with the two smilies, refers back to Ubuntu forum, where I found...me! [http://sidux.com/PNphpBB2-viewtopic-t-10864.html](http://sidux.com/PNphpBB2-viewtopic-t-10864.html)

Now, I am not 100% sure this is the same card, but I also don't think it will hurt us to build a module that may not fit or match our card. After all, our machines now contain dozens upon dozens of driver modules.

Here is the Ubuntu forum link: [http://ubuntuforums.org/showthread.php?t=770173](http://ubuntuforums.org/showthread.php?t=770173)

The process is enumerated quite well in post #7. You will be building a driver module *atl1e*, which we hope will kick your card to life. If not, it's quite easy to uninstall.

Post back if you get stuck.

---

### Post by medesand on 2008-06-18
Solved ! \\:D/\\:D/\\:D/

It work`s just fine !

Thank you verry much man!

---

### Post by medesand on 2008-06-18
back again ..

worked .. made updates .. restart .. and again No Network

*edit

Find the problem .. system - administration - hardware drivers 

attansic .. it was enable .. but not in use .. made in use and it works.

---

