---
title: "No internet"
date: 2008-06-23
forum: Networking &amp; Wireless
---

### Post by darkreaction on 2008-06-23
So i downloaded Wicd and I cant connect to the internet I want to re install network manager but I need to download it. I am on a live cd right now is there any way to fix it from here?

---

### Post by apjone on 2008-06-23
> **darkreaction said:**
> So i downloaded Wicd and I cant connect to the internet I want to re install network manager but I need to download it. I am on a live cd right now is there any way to fix it from here?

Never used, but a google reveals it is a GUI tool for networking. Are you trying to connect to the net using wired connection?

---

### Post by apjone on 2008-06-23
if you open a terminal in the live cd and run

```

ifconfig

```

and

```

cat /etc/resolv.conf

```

and post the out put of both here I can give you enough help that youd be able to get online without the live cd.

---

### Post by darkreaction on 2008-06-23
```
ubuntu@ubuntu:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:18:4d:77:bc:3c  
          inet6 addr: fe80::218:4dff:fe77:bc3c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth0      Link encap:Ethernet  HWaddr 00:15:f2:08:f2:d2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3458 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3458 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:172900 (168.8 KB)  TX bytes:172900 (168.8 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-18-4D-77-BC-3C-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:468 errors:0 dropped:0 overruns:0 frame:15500
          TX packets:873 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:42752 (41.7 KB)  TX bytes:40158 (39.2 KB)
          Interrupt:19 

wlan0     Link encap:Ethernet  HWaddr 00:11:50:78:44:3a  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:50ff:fe78:443a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5753 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6763 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5117189 (4.8 MB)  TX bytes:1335414 (1.2 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-11-50-78-44-3A-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

```
ubuntu@ubuntu:~$ cat /etc/resolv.conf
### BEGIN INFO
#
# Modified_by:  NetworkManager
# Process:      /usr/bin/NetworkManager
# Process_id:   8605
#
### END INFO

search hosts.bc1.bresnan.net


nameserver 69.145.248.50
nameserver 69.145.232.4
nameserver 69.145.248.4

```

---

### Post by superprash2003 on 2008-06-23
are you able to open [http://72.14.207.99](http://72.14.207.99)

---

### Post by darkreaction on 2008-06-24
No I have no connection to anything

---

### Post by apjone on 2008-06-24
Your /etc/network/interfaces will probably look something like this

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

```

What we will do is give you a static IP

so boot up your machine as you would and from a terminal run
```

cp /etc/network/interfaces interfaces.bak
sudo gedit /etc/network/interfaces

```

and replace 

```

auto eth0
iface eth0 inet dhcp

```

with 

```

auto eth0
iface eth0 inet static
address 192.168.1.2
netmask 255.255.255.0
gateway 192.168.1.1

```

then save it and run

```

ifdwon eth0
ifup eth0

```

And that should get you working on static IP over wired networking.

---

### Post by apjone on 2008-06-24
> **superprash2003 said:**
> are you able to open [http://72.14.207.99](http://72.14.207.99)

I think more people know googles IP than there own :lolflag:

---

