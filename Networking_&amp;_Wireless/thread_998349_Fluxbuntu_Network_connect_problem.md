---
title: "Fluxbuntu: Network connect problem"
date: 2008-11-30
forum: Networking &amp; Wireless
---

### Post by philB314 on 2008-11-30
(fluxbuntu) Network connection


Hello all,

I am new to fluxbuntu and Linux in general. I have installed fluxbuntu on my system without too much trouble. However, now, I am trying to connect to my home network via a cable, and my computer is not detecting it.

Suppose the password to my network is foobar. How do I install the proper drivers to connect to the Internet?

Thanks,
Phil

---

### Post by cariboo on 2008-11-30
How do you connect to the internet, through a router or direct connection to your router?

Could you paste the output of:

```
sudo lshw -C network > network.txt
```

You have to do the above in a Applications-->Accessories-->Terminal. The above command will create a text file that you can copy  to your computer with the internet connection and include it in your next post.

Jim

---

### Post by philB314 on 2008-11-30
Thanks!

Here is network.txt:  (I apologize for any typos below.  I have to type this manually)

*-network:0 DISABLED
description: Ethernet interface
product: 82557/8/9 Ethernet Pro 100
vendor: Intel Corporation
physical id: 1
bus info: pci@0000:01:01;0
logical name: eth0
version: 08
serial: 00:90:27:3e:88:a0
size: 100MB/s
capacity: 100MB/s
width: 32 bits
clock: 33MHz
capabilities: pm bus_master par_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k4-NAPI duplex=full firmware=N/A latency=64 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s
*-network:1 DISABLED
description: Ethernet interface
product: SMC2-1211TX
vendor: Accton Technology Corporation
physical id: b
bus info: pci@0000:01:0b;0
logical name: eth1
version: 10
serial: 00:10:b5:81:da:31
size: 10MB/s
capacity: 100MB/s
width: 32 bits
clock: 33MHz
capabilities: pm bus_master par_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s


Thanks again.  If I made a mistake, or you need something else, just let me know.

---

### Post by cariboo on 2008-12-02
Both of your nics are supported. The drivers are both kernel modules, so there is no need to go looking for drivers. There could be a possibility that both eth0 and eth1 are disabled in /etc/network/interfaces. the file should look something like this:

```
 cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

# The secondary network interface
auto eth1
iface eth1 inet dhcp
```

if there is a **#** in the lines that start with iface, this may be the problem. To edit the interfaces file, open a terminal and type:

```
sudo nano /etc/network/interfaces
```

If there are **#** signs as mentioned above remove them then press Ctrl-o to save and Ctrl-x to exit. The next step is to restart networking, in the same terminal type:

```
sudo /etc/init.d/networking restart
```

You should see something like this:

```
sudo /etc/init.d/networking start
 * Configuring network interfaces...                                            Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:16:17:9c:84:b5
Sending on   LPF/eth0/00:16:17:9c:84:b5
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPOFFER of 192.168.1.100 from 192.168.1.1
DHCPREQUEST of 192.168.1.100 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.100 from 192.168.1.1
bound to 192.168.1.100 -- renewal in 35500 seconds
```

Hopefully this will get your network up and running.

Jim

---

### Post by dollylamb on 2008-12-02
Your eth0 & eth1 has been disabled, just enable eth0 & it will work.

---

### Post by Sonsum on 2009-02-18
In case you are not sure how to enable eth0:

1. right click to open menu
2. go to System / Networking
3. enter your password
4. Click on "new_config" and click "Edit"
5. Click on "Config" and then "eth0"
6. Check the box next to "Active"

You're all done!

Note: Guide specifically made for Fluxbuntu

---

