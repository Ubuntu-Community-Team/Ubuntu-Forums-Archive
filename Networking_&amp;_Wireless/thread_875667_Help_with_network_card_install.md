---
title: "Help with network card install"
date: 2008-07-31
forum: Networking &amp; Wireless
---

### Post by sd37167 on 2008-07-31
OK,

So I am pretty much new to linux in general and have almost no clue what i'm doing so any and all help is greatly appreciated.

I installed 8.04 just fine.  The onboard LAN works, but the network card I had laying around from an old system doesn't seem to.  From what I've been able to tell it is detected but thats it...when I run:

sudo lshw -C network

I get the following output:

```
stephen@linux-fw:~$ sudo lshw -C network
  *-network DISABLED      
       description: Ethernet interface
       product: Hangzhou Silan Microelectronics Co., Ltd.
       vendor: Hangzhou Silan Microelectronics Co., Ltd.
       physical id: 8
       bus info: pci@0000:04:08.0
       logical name: eth1
       version: 01
       serial: 00:e0:20:00:07:6d
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sc92031 driverversion=2.0c duplex=full latency=64 link=yes maxlatency=40 mingnt=20 module=sc92031 multicast=yes port=MII speed=100MB/s
```


Thats all I have been able to figure out and I have no clue what to do to even begin fixing the problem. The onboard LAN does work, btw. 
Thanks!

---

### Post by chili555 on 2008-07-31
I assume this is only part of your *lshw.* It should show both the on-board and add-on network cards. This part:> *-network DISABLEDmakes me wonder if there is a setting in the computer's BIOS to use either on-board, add-on or both network cards and, moreover, if the setting is set correctly. Will you check?

---

### Post by sd37167 on 2008-07-31
As far as the lshw goes, that is all that is returned, so I am not getting anything for the onboard device that is working....not sure what that means.

I checked the settings and even when I turn the onboard LAN off, I get the same results, except the card is then listed as eth0.

Any ideas on why I don't get anything back for eth0 from the lshw?

---

