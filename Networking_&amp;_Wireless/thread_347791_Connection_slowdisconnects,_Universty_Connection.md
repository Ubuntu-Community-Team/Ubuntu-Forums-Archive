---
title: "Connection slow/disconnects, Universty Connection"
date: 2007-01-27
forum: Networking &amp; Wireless
---

### Post by skyhopper88 on 2007-01-27
I'm new at troubleshooting Ubuntu, so bare with me. In Windows I'm getting speeds of 6699 kbps down/8830 up. In Ubuntu however, I get  974/857! Something isn't set up right. I am running Edgy on my desktop with my ethernet coming straight from the wall to my onboard ethernet. Network Manager is telling me no network devices have been found but I'm online at the moment, and it has seen the wired connection before. I have set it to automatic and static addresses, no change. If I try to configure eth0 in Network Tools I get 

> The configuration could not be loaded
You are not allowed to access the system configuration.


'dmesg |grep eth' gives me
> 
[17179586.204000] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.54.
[17179586.204000] forcedeth: using HIGHDMA
[17179586.724000] eth0: forcedeth.c: subsystem: 0105b:0caf bound to 0000:00:14.0
[17179619.416000] eth0: no IPv6 routers present
[17179984.528000] eth0: no IPv6 routers present

'ifconfig' gives me

> eth0      Link encap:Ethernet  HWaddr 00:15:58:25:FD:09  
          inet addr:69.65.220.163  Bcast:69.65.221.255  Mask:255.255.254.0
          inet6 addr: fe80::215:58ff:fe25:fd09/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8672 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4471 errors:83 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4874922 (4.6 MiB)  TX bytes:1126354 (1.0 MiB)
          Interrupt:225 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


'ifconfig -a -v' gives me

> eth0      Link encap:Ethernet  HWaddr 00:15:58:25:FD:09  
          inet addr:69.65.220.163  Bcast:69.65.221.255  Mask:255.255.254.0
          inet6 addr: fe80::215:58ff:fe25:fd09/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:84500 errors:0 dropped:0 overruns:0 frame:0
          TX packets:67923 errors:201 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:86128984 (82.1 MiB)  TX bytes:7287269 (6.9 MiB)
          Interrupt:225 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)



'dmesg |grep net' gives me

> [17179571.716000] audit: initializing netlink socket (disabled)
[17179586.204000] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.54.


'ifconfig eth0' gives me

> eth0      Link encap:Ethernet  HWaddr 00:15:58:25:FD:09  
          inet addr:69.65.220.163  Bcast:69.65.221.255  Mask:255.255.254.0
          inet6 addr: fe80::215:58ff:fe25:fd09/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:82497 errors:0 dropped:0 overruns:0 frame:0
          TX packets:66299 errors:201 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:83817927 (79.9 MiB)  TX bytes:7151651 (6.8 MiB)
          Interrupt:225 Base address:0x2000 


'cat /etc/network/interfaces' gives me

> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


'ifup eth0' gives me 
> ifup: interface eth0 already configured


I've disabled IPV6 as well, nada. I need to get this sorted out soon, as I use this for schoolwork. Any help would be appreciated.

---

### Post by skyhopper88 on 2007-01-27
I was able to get into Network Tools by adding 'gksu' the command, but that just gives me the same access to what I found in Networking. Any ideas? Normal browsing is ok, but dowloading and updating take eons (which is alot of what I do)

---

### Post by skyhopper88 on 2007-01-28
Sorry, I just realised I repeated a lot of the same info. The connection doesn't seem to be dropping anymore (hope I don't jinx myself), but it's still slow. Right now I'm using a X-over cable, not sure if that makes any difference. I switched it out with my roomate's but I'm not sure what it was (just said Belkin on it...). That didn't help any. I'm not exactly sure what the specs on my onboard card are other than it's a Nvidia Ethernet Controller. In Windows I got similar (slow) speeds until I set it to full duplex, that's done with ethtool, correct? Well...
'ethtool eth0' gives me

> Cannot get device settings: Operation not permitted
Cannot get wake-on-lan settings: Operation not permitted
Cannot get message level: Operation not permitted
Cannot get link status: Operation not permitted
No data available


I may have to continue doing stuff in Windows until I get this sorted out, which I really don't want to do.

---

### Post by skyhopper88 on 2007-01-28
I updated the kernel from linux-image-2.6.17-10-generic to linux-image-2.6.17-50-generic, no luck. 
*slams head on desk*

---

