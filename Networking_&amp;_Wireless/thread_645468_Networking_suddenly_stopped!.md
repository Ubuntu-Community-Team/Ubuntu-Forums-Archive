---
title: "Networking suddenly stopped!"
date: 2007-12-20
forum: Networking &amp; Wireless
---

### Post by geeree on 2007-12-20
Hello,

I use Ubuntu 7.10 on a Dell Inspiron 640m. Until a few days ago, my networking was working fine. I could connect to anonymous public wireless automatically (just by switching on the computer's wireless) and I routinely used the LAN. Now I notice the following three problems: 

[LIST=1]
[*]I cannot connect to anonymous wireless. 'iwconfig' shows that my wireless port is called 'eth1'. But when I try 'sudo ifup eth1' it says it cannot configure the "unknown port" eth1. 
[*]I cannot automatically connect to the wired network either. But this is curable by doing 'sudo ifup eth0'.
[*]All this while, when my computer is not connected to *any* network, the nm-applet on the GNOME panel shows me as connected! A right-click on the applet gives an inactive 'Connection Information' field so that does not help. When I do 'ifconfig' I find a port "eth0:avah" that has a non-trivial IP address!
[/LIST]
All this three problems did not exist four days ago. They have happened quite suddenly. Could anyone please help?

Girish.

---

### Post by GSF1200S on 2007-12-20
> **geeree said:**
> Hello,

I use Ubuntu 7.10 on a Dell Inspiron 640m. Until a few days ago, my networking was working fine. I could connect to anonymous public wireless automatically (just by switching on the computer's wireless) and I routinely used the LAN. Now I notice the following three problems: 

[LIST=1]
[*]I cannot connect to anonymous wireless. 'iwconfig' shows that my wireless port is called 'eth1'. But when I try 'sudo ifup eth1' it says it cannot configure the "unknown port" eth1. 
[*]I cannot automatically connect to the wired network either. But this is curable by doing 'sudo ifup eth0'.
[*]All this while, when my computer is not connected to *any* network, the nm-applet on the GNOME panel shows me as connected! A right-click on the applet gives an inactive 'Connection Information' field so that does not help. When I do 'ifconfig' I find a port "eth0:avah" that has a non-trivial IP address!
[/LIST]
All this three problems did not exist four days ago. They have happened quite suddenly. Could anyone please help?

Girish.

Ill be glad to try and help- lets go ahead and take a physical look at some commands-

First off, what wireless card (just curious)?

```
ifconfig
```

```
iwconfig
```

```
iwlist scanning
```

```
cat /etc/network/interfaces
```

```
lshw -C network
```

---

### Post by geeree on 2007-12-20
Thanks. I did that 'iwlist scanning' and then used the System>Administration>Network to get started. But I am still wondering what is that 'eth0:avah', and why my 'nm-applet' has started misbehaving, and why the wireless "roming mode" wouldn't work.

> **GSF1200S said:**
> 
First off, what wireless card (just curious)?


Intel PRO/Wireless 3945ABG.

> ```
ifconfig
```

Did this. Here is the puzzling line; the 'eth0:avah' has now become 'eth2:avah':

```
eth2:avah Link encap:Ethernet  HWaddr 00:15:C5:7D:C2:DA  
               inet addr:169.254.10.97  Bcast:169.254.255.255  Mask:255.255.0.0
               UP BROADCAST MULTICAST  MTU:1500  Metric:1
               Interrupt:17 

```

Rest of the things are okay now. Thank you so much! 

Girish.

---

### Post by GSF1200S on 2007-12-20
> **geeree said:**
> Thanks. I did that 'iwlist scanning' and then used the System>Administration>Network to get started. But I am still wondering what is that 'eth0:avah', and why my 'nm-applet' has started misbehaving, and why the wireless "roming mode" wouldn't work.



Intel PRO/Wireless 3945ABG.



Did this. Here is the puzzling line; the 'eth0:avah' has now become 'eth2:avah':

```
eth2:avah Link encap:Ethernet  HWaddr 00:15:C5:7D:C2:DA  
               inet addr:169.254.10.97  Bcast:169.254.255.255  Mask:255.255.0.0
               UP BROADCAST MULTICAST  MTU:1500  Metric:1
               Interrupt:17 

```

Rest of the things are okay now. Thank you so much! 

Girish.

Haha, I just kind of assisted you- you did most the work yourself :)

By the way, if we're to figure out the problems with your network applet, etc- I still need the results from those commands ;)

---

### Post by geeree on 2008-01-11
Hi GSF1200S,

Although many days have passed since I posted here last (I'd been travelling), my problem with the nm-applet persists. It will be very nice if you could still help me out.

> **GSF1200S said:**
> By the way, if we're to figure out the problems with your network applet, etc- I still need the results from those commands

I am now connected to a LAN here via a wired connection and here are what these various commands say: 

```

girish@geeku:~$ ifconfig
eth2      Link encap:Ethernet  HWaddr 00:15:C5:7D:C2:DA  
          inet addr:192.168.9.156  Bcast:192.168.9.255  Mask:255.255.255.0
          inet6 addr: fe80::215:c5ff:fe7d:c2da/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21712 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1794 errors:0 dropped:0 overruns:0 carrier:0
          collisions:121 txqueuelen:1000 
          RX bytes:4174670 (3.9 MB)  TX bytes:312633 (305.3 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

```

girish@geeku:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth1
#iface eth1 inet dhcp


#iface eth2 inet dhcp

auto ath0
#iface ath0 inet dhcp

auto wlan0
#iface wlan0 inet dhcp


#iface eth0 inet dhcp



auto eth0

iface ppp0 inet ppp
provider ppp0



iface eth2 inet dhcp

iface eth1 inet dhcp
wireless-essid WLIucaa-Nalanda

auto eth2

auto ppp0

```

```

girish@geeku:~$ sudo lshw -C network
[sudo] password for girish:

  *-network
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=ipw3945 latency=0 module=ipw3945
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth2
       version: 02
       serial: 00:15:c5:7d:c2:da
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=1.01 duplex=half ip=192.168.9.156 latency=64 link=yes module=b44 multicast=yes port=twisted pair speed=10MB/s

```

I haven't included `iwconfig' and `iwlist scanning' because my wireless is off at the moment. 

Girish.

---

