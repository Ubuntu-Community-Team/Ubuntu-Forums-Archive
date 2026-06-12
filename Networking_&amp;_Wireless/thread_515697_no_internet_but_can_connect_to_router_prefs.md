---
title: "no internet but can connect to router prefs"
date: 2007-08-02
forum: Networking &amp; Wireless
---

### Post by supersonicdarky on 2007-08-02
Router: D-Link DI-524
Problem: I can't connect to the internet (wireless or lan) in ubuntu but I can connect to the router and browse the prefs (192.168.0.1). I cannot ping sites either. Windows can connect just fine.

I saw [this thread](http://ubuntuforums.org/showthread.php?p=3026821), so I'll post the output of those 3 commands:

```
kernel@laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:C0:9F:E8:82:50  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:19 Base address:0x1800 

eth0:avah Link encap:Ethernet  HWaddr 00:C0:9F:E8:82:50  
          inet addr:169.254.8.79  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:19 Base address:0x1800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:110 errors:0 dropped:0 overruns:0 frame:0
          TX packets:110 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8166 (7.9 KiB)  TX bytes:8166 (7.9 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:14:A4:47:25:79  
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:13 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:588 (588.0 b)
          Interrupt:4 

kernel@laptop:~$ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 wlan0
0.0.0.0         192.168.0.1     0.0.0.0         UG        0 0          0 wlan0
0.0.0.0         0.0.0.0         0.0.0.0         U         0 0          0 eth0
kernel@laptop:~$ cat /etc/resolv.conf 
nameserver 192.168.0.1


```

---

### Post by Kosimo on 2007-08-02
Did you introduce your IP manually? Or by DHCP?

Try to go to this address with Firefox:  [http://66.249.93.104/](http://66.249.93.104/)

If you can see the google webpage your problem is a DNS problem

---

### Post by supersonicdarky on 2007-08-02
it works ;o

how would i fix the dns?

i usually have static ip, but dhcp/ip4ll work too

tried changing resolv.conf ip to opendns (208.67.222.222) but doesnt help

---

### Post by Kosimo on 2007-08-02
> **supersonicdarky said:**
> it works ;o

how would i fix the dns?

i usually have static ip, but dhcp/ip4ll work too

tried changing resolv.conf ip to opendns (208.67.222.222) but doesnt help

Try to choose a DHCP server (allowing the system to choose an IP for you) it will also choose a DNS.

If you really want to have a static IP. Then, you have to add a DNS server (hit DNS tab)
You need to know what are your DNS.  Anyway some routers have a DNS server as well, so, just adding your router IP it may work.

Good luck.

---

### Post by supersonicdarky on 2007-08-02
no help :(

what else can i try?

---

### Post by supersonicdarky on 2007-08-06
...bump...

---

