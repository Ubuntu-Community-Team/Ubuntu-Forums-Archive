---
title: "Problems with PPPOE internet (somewhat urgent)"
date: 2009-02-16
forum: New to Ubuntu
---

### Post by KevNice on 2009-02-16
My workplace uses a PPPOE ADSL connection through a wireless modem, and I've encountered a strange problem. 

Firstly, the way they have it set up is by first connecting through the wireless, under limited connectivity, and then dialing into the PPPOE provider. I've gotten this to work on Windows Vista.

Now when I started up Ubuntu for the first time, my wireless card detected several different networks. The network in question tried to connect, but wouldn't go through, so I tried setting up the PPPOE directly using sudo pppoeconf. I run it, checks everything, and set it up. The connection doesn't work, however, because I didn't get through the wireless network first (I didn't realize this was necessary until after the fact, when I did it on Vista).

So I rebooted to try again on Ubuntu. However, now no wireless networks are detected. I run "sudo pppoeconf", and each time it tries to find my cards, it times out and nothing happens. I tried a "sudo poff" and then tried pppoeconf again, but the same thing happens. No network cards are detected, and there are no networks under the drop down list, which were there the first time. The error says something like "another thing is running the pppoe process".

It works under Vista, but I don't have MS office so I can't do any word processing, so I need Ubuntu for work.

Anyone know how to correct this issue? Perhaps I need to reset pppoeconf so it doesn't interrupt with network detection? It should still display the networks, though..

---

### Post by KevNice on 2009-02-18
bump?

---

### Post by KevNice on 2009-02-20
Here is the output of sudo lshw -c net:

```
 *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1b:77:e0:0d:1e
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:ad:95:e1
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=219.69.72.87 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 7a:48:c6:89:00:ea
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

I don't understand. The wireless has always worked perfectly before the other day (running Ibex).

---

### Post by KevNice on 2009-02-21
_

---

### Post by KevNice on 2009-02-22
While playing with some other things, I noticed something that may be causing the problem.

My gedit /etc/network/interfaces file looks like this:


```
auto lo
iface lo inet loopback


auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig wlan0 up # line maintained by pppoeconf
provider dsl-provider

auto wlan0
iface wlan0 inet manual
```

Now I am still a noob, but it seems like something is wrong here. I am currently (at home) connected to a wired broadband connection under eth0, yet I see it nowhere on this file.

Here is my ifconfig (again now at home on broadband wired connection) in case it helps:

```
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1c:23:ad:95:e1  
          inet addr:219.70.22.120  Bcast:219.70.22.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:576  Metric:1
          RX packets:3999 errors:31 dropped:0 overruns:0 frame:31
          TX packets:3550 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1755011 (1.7 MB)  TX bytes:413646 (413.6 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:152 errors:0 dropped:0 overruns:0 frame:0
          TX packets:152 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12080 (12.0 KB)  TX bytes:12080 (12.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1b:77:e0:0d:1e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-1B-77-E0-0D-1E-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

also, my internet is realllly slow under Ubuntu

---

### Post by KevNice on 2009-02-26
alright then... back to Hardy I guess.:-?

---

