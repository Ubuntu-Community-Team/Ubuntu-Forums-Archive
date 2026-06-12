---
title: "cannot connect to Internet"
date: 2008-07-08
forum: Networking &amp; Wireless
---

### Post by maxidrom11 on 2008-07-08
UBUNTU 8.04 Hardy Heron 
Laptop Acer Aspire 3682WXMi
External ADSL modem: Zyxel 660M
I need to connect via pppoe
I edited **/etc/network/interfaces**
```

auto lo ppp0
iface lo inet loopback
allow-hotplug eth0
iface eth0 inet static
   name eth0
   address 192.168.0.2
   network 192.168.0.0
   broadcast 192.168.0.255
   netmask 255.255.255.0
   gateway 192.168.0.1
iface ppp0 inet ppp
   provider ppp0

```
also edited **/etc/ppp/peers/ppp0** :
```

noipdefault
defaultroute
replacedefaultroute
hide-password
lcp-echo-interval 20
lcp-echo-failure 3
connect /bin/true
noauth
persist
mtu 1492
noaccomp
default-asyncmap
plugin rp-pppoe.so eth0
user "my user login information"

```

to bring up internet connection 
I do type:
```
sudo /sbin/ifup ppp0
```
it says:
```
interface ppp0 already configured
```and nothing happens
then I do
```
sudo /sbin/ifconfig -a
```
it says:
```
ath0      Link encap:Ethernet  HWaddr 00:19:7d:29:5c:4a  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth0      Link encap:Ethernet  HWaddr 00:16:36:c7:6e:5b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1828 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1828 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:91400 (89.2 KB)  TX bytes:91400 (89.2 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-19-7D-29-5C-4A-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:151 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:0 (0.0 B)  TX bytes:6946 (6.7 KB)
          Interrupt:18 
```

---

### Post by df6269 on 2008-07-08
Which device are you using for connect via pppoe?
wireless or Ethernet

---

### Post by maxidrom11 on 2008-07-08
> **df6269 said:**
> Which device are you using for connect via pppoe?
wireless or Ethernet

I use **Ethernet**-> **eth0**

---

### Post by superprash2003 on 2008-07-08
your eth0 aint getting an ip!!even 192.168.0.2 doesnt seem to be working.. have you restarted networking or ubuntu after you made changes to the interfaces file?

---

### Post by maxidrom11 on 2008-07-08
I restarted UBUNTU after I have made all the editing to **/etc/network/interfaces** and **/etc/ppp/peers/ppp0**

---

### Post by maxidrom11 on 2008-07-08
I edited **/etc/network/interfaces** again:
```

auto lo eth0 ppp0
iface lo inet loopback
allow-hotplug eth0
iface eth0 inet static
   name eth0
   address 192.168.1.2
   network 192.168.1.0
   broadcast 192.168.1.255
   netmask 255.255.255.0
   gateway 192.168.1.1

iface ppp0 inet ppp
   provider ppp0
```
In Terminal:
```
sudo /sbin/ifup ppp0
```
it says:
```
interface ppp0 already configured
```
 and nothing happens :mad:

after changes:
```

ath0      Link encap:Ethernet  HWaddr 00:19:7d:29:5c:4a  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth0      Link encap:Ethernet  HWaddr 00:16:36:c7:6e:5b  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:36ff:fec7:6e5b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:78 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:92 (92.0 B)  TX bytes:6214 (6.0 KB)
          Interrupt:16 

wifi0     Link encap:UNSPEC  HWaddr 00-19-7D-29-5C-4A-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:467 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:0 (0.0 B)  TX bytes:21482 (20.9 KB)
          Interrupt:18 

```

---

### Post by maxidrom11 on 2008-07-08
if I do:
```
**sudo /sbin/ifup ppp0**
```
it says the same:
```
interface ppp0 already configured
```

---

### Post by superprash2003 on 2008-07-08
are you able to ping your router?? in the terminal type ping 192.168.1.1 and post output here

---

### Post by maxidrom11 on 2008-07-08
in terminal:
```
ping 192.168.1.1
```

and I see:

```
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=254 time=0.498 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=254 time=0.491 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=254 time=0.484 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=254 time=0.478 ms
64 bytes from 192.168.1.1: icmp_seq=5 ttl=254 time=0.486 ms
64 bytes from 192.168.1.1: icmp_seq=6 ttl=254 time=0.491 ms
64 bytes from 192.168.1.1: icmp_seq=7 ttl=254 time=0.511 ms
64 bytes from 192.168.1.1: icmp_seq=8 ttl=254 time=0.504 ms
64 bytes from 192.168.1.1: icmp_seq=9 ttl=254 time=0.505 ms
**[COLOR="DarkRed"]and so on ...[/COLOR]**

```

---

### Post by linuxonbute on 2008-07-08
> **maxidrom11 said:**
> in terminal:
```
ping 192.168.1.1
```

and I see:

```
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=254 time=0.498 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=254 time=0.491 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=254 time=0.484 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=254 time=0.478 ms
64 bytes from 192.168.1.1: icmp_seq=5 ttl=254 time=0.486 ms
64 bytes from 192.168.1.1: icmp_seq=6 ttl=254 time=0.491 ms
64 bytes from 192.168.1.1: icmp_seq=7 ttl=254 time=0.511 ms
64 bytes from 192.168.1.1: icmp_seq=8 ttl=254 time=0.504 ms
64 bytes from 192.168.1.1: icmp_seq=9 ttl=254 time=0.505 ms
**[COLOR="DarkRed"]and so on ...[/COLOR]**

```

You might like to read this:
[http://www.linuxhelp.net/guides/pppoe/](http://www.linuxhelp.net/guides/pppoe/)

---

### Post by superprash2003 on 2008-07-08
thats a good sign.. try reconfiguring ppoe by going to the terminal and typing sudo pppoeconf

---

