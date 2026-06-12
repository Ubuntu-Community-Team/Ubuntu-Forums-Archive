---
title: "ethernet connection not working (DSN problem?) on ubuntu 15.10"
date: 2018-10-16
forum: Networking &amp; Wireless
---

### Post by paola812 on 2018-10-16
Dear users,

   I'm a newby of Ubuntu. I've ubuntu 15.10 installed on a laptop and since 6 days I cannot connect anymore to internert via wired connection. I don't know what I did wrong, but I was connected with a VPN and when I disconnected I could not connect anylonger (nor with neither without VPN).

The connection name changed from eth0 to something strange containing my MAC address. I could put the name back following this post:
[https://askubuntu.com/questions/689501/how-to-rename-network-interface-in-15-10](https://askubuntu.com/questions/689501/how-to-rename-network-interface-in-15-10)
but it didn't help.

When I type
```
ipconfig
``` I get:
```
eth0 Link encap:Ethernet  HWaddr 9c:eb:e8:29:08:6c  
    inet addr:192.168.1.68  Bcast:192.168.1.255  Mask:255.255.255.0
    inet6 addr: fe80::9eeb:e8ff:fe29:86c/64 Scope:Link
     UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
    RX packets:113 errors:0 dropped:0 overruns:0 frame:0
    TX packets:2027 errors:0 dropped:0 overruns:0 carrier:0
    collisions:0 txqueuelen:1000 
    RX bytes:9048 (9.0 KB)  
    TX bytes:175165 (175.1 KB)
lo        
       Link encap:Local Loopback  
       inet addr:127.0.0.1  Mask:255.0.0.0
       inet6 addr: ::1/128 Scope:Host
        UP LOOPBACK RUNNING  MTU:65536  Metric:1
        RX packets:51 errors:0 dropped:0 overruns:0 frame:0
        TX packets:51 errors:0 dropped:0 overruns:0 carrier:0
       collisions:0 txqueuelen:0 
       RX bytes:7547 (7.5 KB)  TX bytes:7547 (7.5 KB)
```

Then:
```
route -n
```

```

Kernel IP routing table
Destination     
Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 eth0

```

Then: ```
sudo lshw -C network 
```
 ```
 
*-network               
       description: Ethernet interface
       physical id: 1
logical name: eth0
serial: 9c:eb:e8:29:08:6c
size: 100Mbit/s
capacity: 1Gbit/s
capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=r8152 driverversion=v1.08.1 (2015/07/28) duplex=full ip=192.168.1.68 link=yes multicast=yes port=MII speed=100Mbit/s
 
```

There is no product name, but maybe it is normal(?)

However when I type:
```
ping 8.8.8.8
```
```

PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=120 time=52.1 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=120 time=52.0 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=120 time=51.9 ms
^C
--- 8.8.8.8 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms

```

It works fine, but then when I type:
```
ping www.google.com
```
it doesn't do anything.

I found here 
[https://askubuntu.com/questions/804272/connected-to-ethernet-but-no-internet/804302#804302?newreg=a7ea316ad090468abbcdaaf0d5bcc3d6](https://askubuntu.com/questions/804272/connected-to-ethernet-but-no-internet/804302#804302?newreg=a7ea316ad090468abbcdaaf0d5bcc3d6)
that it might the dhcp server not giving me a DNS server to look up names, but I could not find how to fix it.

Firefox just tells me "server not found"

The Wifi connection does the same.

In the Connection editor I've put IPv6 on "Ignored"

I also deleted the old network names  doing:
```
sudo rm /etc/NetworkManager/system-connections/...old connection name ...
```

I have tried to do: (I admit it: I didn't know what I was doing)
```

sudo nano /etc/NetworkManager/NetworkManager.conf

[main]
plugins=ifupdown,keyfile,ofono
#dns=dnsmasq

```
sudo service network-manager restartand comment the dns=dsnmasq line, as suggested here:
[https://askubuntu.com/questions/690511/how-to-change-dns-in-ubuntu-15-10](https://askubuntu.com/questions/690511/how-to-change-dns-in-ubuntu-15-10)
but it doesn't do anything (I've put it back as it was)

Internet connection, wired and wifi, works on other laptops. I rebooted the box for internet connection too.

I apologize if similar threads have already been posted. As I'm a newby I could not find the solution in all the posts I've read.

Thank you very much for your help

Cheers
Paola

---

### Post by TheFu on 2018-10-16
Ubuntu 15.10 support ended over 2 yrs ago.  Forum policy doesn't allow help for unsupported versions.
Ubuntu Support information: [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)  It is worth looking over.

Ubuntu 16.04 or 18.04 ARE supported for 5 yrs from the release month (even years, April release).  Please move or do a fresh install of either of those releases.  There will be a new release in a few weeks, 18.10 (2018/Oct).  Don't use it.  It only has 9 months of support.

Appears to me that your networking is fine.  Just the DNS isn't.  
Also, probably a typo, but ipconfig isn't a valid Linux command.

---

### Post by paola812 on 2018-10-18
Dear TheFu,
   thank you for your reply.
Unfortunately I cannot update the ubuntu version, it's my company's laptop and I'm not allewed to. And no, they don't provide us any support :/
Best regards
Paola

---

### Post by slickymaster on 2018-10-18
Thread moved to **Networking & Wireless** for a better fit

---

### Post by TheFu on 2018-10-18
> **paola812 said:**
> Dear TheFu,
   thank you for your reply.
Unfortunately I cannot update the ubuntu version, it's my company's laptop and I'm not allewed to. And no, they don't provide us any support :/
Best regards
Paola

There are a few serious remote access flaws in the 15.10 release. If your management doesn't know this, they should be informed.
I cannot help with network manager stuff. I've never used it. Sorry.

---

### Post by paola812 on 2018-10-24
Thank you for your reply!!
I'll try to convince them to switch version :)
Paola

---

### Post by paola812 on 2018-10-24
Dear TheFu,

  for info, in case someone else has the same issue that I have, I run:
run dpkg-reconfigure resolvconf
and reboot
and now it seems to work (at least in wifi)

Still thank you so much for your help!
Best regards
Paola

---

