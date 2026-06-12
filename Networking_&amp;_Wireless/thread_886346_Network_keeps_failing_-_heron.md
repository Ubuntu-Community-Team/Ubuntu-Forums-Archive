---
title: "Network keeps failing - heron"
date: 2008-08-11
forum: Networking &amp; Wireless
---

### Post by Piddell on 2008-08-11
Since my upgrade to heron the network connection keeps failing.
I did a live upgrade but it was so buggy I ended up re-loading from scratch, but this but persists.

I boot up and all looks fine, but I have no access to the network from any application, if I can restore it as follows:

phill@fuzzylogic:~$ sudo dhclient
[sudo] password for phill: 
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:02:55:3b:83:27
Sending on   LPF/eth0/00:02:55:3b:83:27
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPOFFER of 192.168.1.2 from 192.168.1.1
DHCPREQUEST of 192.168.1.2 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.2 from 192.168.1.1
bound to 192.168.1.2 -- renewal in 36329 seconds.
phill@fuzzylogic:~$ 


this is a new feature since my move to heron, all other machines are working ok on the same network

Thoughts?

Phill

---

### Post by Piddell on 2008-08-13
Happened again this morning, any ideas?

---

### Post by Crafty Kisses on 2008-08-13
> **Piddell said:**
> Happened again this morning, any ideas?

That's weird, post these outputs:
```
lshw -C network
```
After that, post this one:
```
iwconfig
```

---

### Post by Piddell on 2008-08-14
New information!
It failed again this morning, so I thought I would login to the router and see what that thought... but I was not able to access it until after I had done a dhclient.  so the problem seems to be that the lan port is disabled.

any way
phill@fuzzylogic:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82801BA/BAM/CA/CAM Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 03
       serial: 00:02:55:3b:83:27
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=full firmware=N/A ip=192.168.1.2 latency=66 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s
phill@fuzzylogic:~$ 

phill@fuzzylogic:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

phill@fuzzylogic:~$ 

both of these logs were when the thing is running ok

---

### Post by Piddell on 2008-08-14
just looked into admin - network and "roaming" was enabled, so I have removed this and set it to DHCP, will see if that makes a difference

---

### Post by Piddell on 2008-08-15
No change this morning.
I ran system- network tools
When I edit the ethernet interface (eth0) it errors and says no such interface exists.  yet it's currently working and the info box below shows all the correct details (ip addresses, data in and out, status: active etc.)

---

### Post by Piddell on 2008-08-16
Same again today - here are the logs before I started it with dhconfig

phill@fuzzylogic:~$ sudo lshw -C network
[sudo] password for phill: 
  *-network               
       description: Ethernet interface
       product: 82801BA/BAM/CA/CAM Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 03
       serial: 00:02:55:3b:83:27
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=full firmware=N/A latency=66 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s


phill@fuzzylogic:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


Which are the same as when it is working ok

---

