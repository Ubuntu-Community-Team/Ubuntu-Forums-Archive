---
title: "Atheros ar2413"
date: 2008-05-18
forum: Networking &amp; Wireless
---

### Post by biglog on 2008-05-18
OK after a week of try to get my wireless card working - I give up.

I think I have read all of the relevant post, but no silver bullet.

I've got the drivers recognised  ```
lshw -C network
```

gives
```
*-network               
       description: Ethernet interface
       product: 82557/8/9/0/1 Ethernet Pro 100
       vendor: Intel Corporation
       physical id: 9
       bus info: pci@0000:00:09.0
       logical name: eth0
       version: 09
       serial: 00:d0:59:4a:7e:d7
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A ip=192.168.1.2 latency=66 maxlatency=56 mingnt=8 module=e100 multicast=yes
  *-network
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wifi0
       version: 01
       serial: 00:1d:0f:b7:2d:f6
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci ip=192.168.1.2 latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g
logann@negus-e500:~$ lspci | grep Atheros
06:00.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
```

but the only thing I can see that looks funny is the ```
iwconfig
```

```
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:18 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-81 dBm  Noise level=-81 dBm
          Rx invalid nwid:7163  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

picking up ath0 and not wifi0

any ideas

---

### Post by Monicker on 2008-05-18
ath0 is normal for an atheros chipset, which uses VAPs to create interfaces for connectivity.  You can even have multiple virtual interfaces from wifi0 performing different functions, such as acting as soft access point.

Does the following command show any wireless networks around you?

```
iwlist ath0 scan
```

---

### Post by biglog on 2008-05-19
```
iwlist ath0 scan
```

I can see my wireless connection and my neighbours.

Does It matter that the ```
lshw
``` gives the the ar2413 card the logical name "wifi0"  but it looks like ath0 is configured (or part configured) and wifi0 isn't?

---

### Post by biglog on 2008-05-24
Helloooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooo

---

### Post by clap.your.hands on 2008-05-29
I have the same problem. But when I type iwconfig, I get this:

courtney@courtney:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

Network manager isn´t even recognizing that I have wireless though it did yesterday.

---

### Post by dnile on 2008-06-20
Hi there,

I am also having an issue with this chipset...  Sometimes when I boot up it works fine and other times it doesn't work...

here is what it says now when it is not working and I do

```
sudo lshw -C network


*-network UNCLAIMED
description: Ethernet controller
product: AR2413 802.11bg NIC
vendor: Atheros Communications Inc.
physical id: b
bus info: pci@0000:02:0b.0
version: 01
width: 32 bits
clock: 33Mhz
capabilities: pm bus_master cap_list
configuration: latency =64 maxlatency=28 mingnt=10
```

Now I have read around that if it says UNCLAIMED that means there is a problem with the driver.  Where can I find a driver for this particular chipset and how to reinstall it?


Seems that all I had to do was reinstall the driver.

Used Version 0.9.4.

---

### Post by jarnett on 2008-06-22
I'm having the same problem Biglog with the Wifi0 and Ath0.
I can see networks with Ath0 but application try to use Wifi0 which cannot see networks.

---

### Post by beadrifle on 2010-05-24
Bump.

I'm having the same issue.

---

### Post by hishamzero1 on 2011-02-14
[SIZE=3]hi 

i have the same card but no problems 

i am new in Ubuntu, but there is way to install new driver 
1. aircrack-ng  have program named airdriver-ng throw it you can install a lot of drivers, see the decontamination in "http://www.aircrack-ng.org/doku.php?id=airdriver-ng" 
2. or you can go to this site and install the driver "http://wireless.kernel.org/en/users/Drivers/ath5k" it's support a lot of drivers.
wish you all luck  
[/SIZE]

---

