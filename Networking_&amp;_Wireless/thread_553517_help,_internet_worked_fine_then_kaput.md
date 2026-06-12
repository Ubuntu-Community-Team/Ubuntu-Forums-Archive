---
title: "help, internet worked fine then kaput"
date: 2007-09-17
forum: Networking &amp; Wireless
---

### Post by dzza on 2007-09-17
Hi, i'm a complete computer noob, so any help here is appreciated:

I have a linux box with feisty fawn installed on it, and for the last month i've been connected to the internet just fine via ethernet to a T1 line.  Recently I added a linksys router, but still connect from my pc to the router via ethernet cable.  Everything was working all the same for a few days, and I was able to get a good wireless signal from my laptop.  A couple days ago, however, I left with the internet in peak condition and when i got home my current dl had stopped and my internet connection was lost.  

The internet connection says it's still connected, but any attempt to access a website or anything net-related times out.  The same goes for the laptop over the wireless connection.  I then tried reverting to the direct connection from the wall to the comp, but that didn't change anything.  Then, following some thread i found, i tried the commands ifdown eth0 and ifup eth0 for all wired configurations.  I have no idea what i'm doing or what's wrong.  Any help would be great.

dunno if this helps, but here is what i get from ifconfig:

dave@COMPUTOR:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:E9:7D:71:D6
          inet addr:192.168.1.119  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:e9ff:fe7d:71d6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1485 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1500 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:278153 (271.6 KiB)  TX bytes:203515 (198.7 KiB)
         Interrut:16 Base address:0xe800
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:388 errors:0 dropped:0 overruns:0 frame:0
          TX packets:388 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:35963 (35.1 KiB)  TX bytes:35963 (35.1 KiB)


and here is what i get from device manager:

Protocol:  IPv4 
IP address:  192.168.1.112
Netmask/Prefix:  255.255.255.0
Broadcast:  192.168.1.255
Scope:  

Protocol:  IPv6
IP address:  fe80::215::e9ff:71d6
Netmask/Prefix:  64
Broadcast:
scope:  Link


Additionally, i configured the router through windows xp on my laptop, and again all was well for a couple days and then it just wasnt.

Thanks for any help
-Dave

---

### Post by Brandon.Viking on 2007-09-18
Sounds strange. If your getting an IP address was that setup manually or by DHCP and the router?

Does the router have the latest firmware on it .... ??? sometimes that can cause connectivity issues.

things you can type to get more information....
```
sudo ip route list
``` or ```
netstat -nr
``` will provide the routing table of the box
```
sudo iptables -L
``` will show firewall rules
```
sudo ethtool
``` will show the interface configuration in case that may have changed, you can also lock the speed and duplex settings if that is required with this tool.

also 
DNS settings can be checked by 
```
sudo cat /etc/resolv.conf
``` verify the domain is correct and that the DNS servers are still valid from your ISP ... some may rotate which means that after a while you may have no ability to resolve names but the connections are still good.

When it happens next time try pinging your favorite website (like slashdot or google) and its IP address (you need to write the IP down while DNS is working if its the problem)

Hope that gives you more information for troubleshooting the connection issue.

Regards,
Brandon.

---

