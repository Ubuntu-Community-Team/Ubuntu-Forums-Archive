---
title: "No access to Internet, Ubuntu 14.04.3 LTS"
date: 2015-10-12
forum: Networking &amp; Wireless
---

### Post by dirkman2 on 2015-10-12
Hi everyone, I have problem with access to Internet, maybe driver of ethernet card on supported in this version of Ubuntu. 
**ifconfig**

eth0      Link encap:Ethernet  HWaddr 74:d4:35:09:b7:f4  
          inet addr:192.168.0.24  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::76d4:35ff:fe09:b7f4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:47 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:774 (774.0 B)  TX bytes:1780 (1.7 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:203 errors:0 dropped:0 overruns:0 frame:0
          TX packets:203 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:14526 (14.5 KB)  TX bytes:14526 (14.5 KB)

[B]ip a


[/B]1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether 74:d4:35:09:b7:f4 brd ff:ff:ff:ff:ff:ff
    inet6 fe80::76d4:35ff:fe09:b7f4/64 scope link 
       valid_lft forever preferred_lft forever

Access to Internet via router(DIR300) with cable. Please, can anyone help me with solve this problem? Thanks.

---

### Post by TheFu on 2015-10-12
Maybe this will help? [http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking](http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking)
Basically, figure out where the issue lies using pings from close to farther away using IP addresses.

---

### Post by joe.koenig on 2015-10-13
Dunno where to even start trying to narrow down the issue: 
 $ ifconfig -a
 $ route -n
 $ cat /etc/hosts
Can you access your router?

---

### Post by michi1983 on 2015-10-14
```
cat /etc/network/interfaces
``` would also be very helpful

---

### Post by dirkman2 on 2015-11-01
To [**[COLOR=#000000]joe.koenig[/COLOR]**]("http://ubuntuforums.org/member.php?u=1058729") - no I can't access to my router via browser.
ifconfig -a 

eth0      Link encap:Ethernet  HWaddr 74:d4:35:09:b7:f4  
          inet6 addr: fe80::76d4:35ff:fe09:b7f4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:94 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1435 (1.4 KB)  TX bytes:397 (397.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1893 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1893 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:164181 (164.1 KB)  TX bytes:164181 (164.1 KB)

route -n 
here's empty

cat /etc/hosts

127.0.0.1    localhost
127.0.1.1    4eburek

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

cat /etc/network/interfaces

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

---

### Post by michi1983 on 2015-11-03
You got an IP address from the router on your first post but not anymore?
Please try a ```
ping 192.168.0.1
``` and ```
ping www.google.com
``` and ```
nslookup www.google.com
``` and ```
traceroute www.google.com
``` and please use code-tags when you post the output of those commands.

---

### Post by praseodym on 2015-11-03
Please show:
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
```

---

