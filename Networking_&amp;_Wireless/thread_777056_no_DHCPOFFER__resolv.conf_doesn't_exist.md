---
title: "no DHCPOFFER / resolv.conf doesn't exist"
date: 2008-05-01
forum: Networking &amp; Wireless
---

### Post by Shilong on 2008-05-01
Hi folks

I've set up two laptops here, both hang on the same switch, one works like a charm out of the box, the other (Thinkpad T60) just refuses to connect to the internet. It's a fresh installation, cards are recognised, modules loaded...

```
root@michele-laptop:~# lspci | grep -i net
02:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
03:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
```

After messing around a bit, I found out that /etc/resolv.conf doesn't exist - so I just created it manually (a copy from the other machine)
```
root@michele-laptop:~# cat /etc/resolv.conf
nameserver 62.2.17.60
nameserver 62.2.24.162
nameserver 62.2.17.61
```

No success so far. /etc/network/interfaces is empty with the exception of lo
Syslog tells me the following about every two minutes:
```
May  1 00:30:37 michele-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
May  1 00:30:45 michele-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
May  1 00:30:56 michele-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
May  1 00:31:08 michele-laptop dhclient: No DHCPOFFERS received.
May  1 00:31:08 michele-laptop dhclient: No working leases in persistent database - sleeping.

```

and ifconfig says:
```
:~# ifconfig
ath0      Protokoll:Ethernet  Hardware Adresse 00:16:CF:AB:50:0E 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

ath0:avah Protokoll:Ethernet  Hardware Adresse 00:16:CF:AB:50:0E 
          inet Adresse:169.254.5.60  Bcast:169.254.255.255  Maske:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

eth0      Protokoll:Ethernet  Hardware Adresse 00:15:58:7C:F9:57 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:192578 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1177 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:100
          RX bytes:12809927 (12.2 MB)  TX bytes:160976 (157.2 KB)
          Basisadresse:0x3000 Speicher:ee000000-ee020000

eth0:avah Protokoll:Ethernet  Hardware Adresse 00:15:58:7C:F9:57 
          inet Adresse:169.254.7.209  Bcast:169.254.255.255  Maske:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Basisadresse:0x3000 Speicher:ee000000-ee020000

lo        Protokoll:Lokale Schleife 
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6 Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1671 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1671 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0
          RX bytes:128767 (125.7 KB)  TX bytes:128767 (125.7 KB)

wifi0     Protokoll:UNSPEC  Hardware Adresse 00-16-CF-AB-50-0E-00-00-00-00-00-00-00-00-00-00 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:207244 errors:0 dropped:0 overruns:0 frame:38849
          TX packets:4002 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:199
          RX bytes:18757049 (17.8 MB)  TX bytes:183756 (179.4 KB)
          Interrupt:21 
```

Does anybody have an idea why I can't get a dhcpoffer on eth0?

Thanks alot, cheers :)

---

### Post by Holy Cheater on 2008-05-01
Could you manually configure your netcard to see if you can exchange data (to check if card properly working)?
If it is working, then the problem is with configuration of dhcp server which you are using (if you're using some router box, check if there's a MAC permission for you network card)

---

### Post by Shilong on 2008-05-01
What do you mean by manually configure? Give it a static ip?

I tried
```
root@michele-laptop:~# /etc/dbu*/event*/25Network* stop
```

then edited /etc/network/interfaces to set a static ip, but

```
root@michele-laptop:~# /etc/init.d/networking restart
 * Reconfiguring network interfaces...  
SIOCADDRT: No such process
Failed to bring up eth0.

```

---

### Post by superprash2003 on 2008-05-01
go to system->administration->network and choose eth0.. then enter static ip address there.. and then post ifconfig results

---

### Post by Shilong on 2008-05-01
```
eth0      Protokoll:Ethernet  Hardware Adresse 00:15:58:7C:F9:57  
          inet Adresse:77.56.85.201  Bcast:255.255.255.255  Maske:255.255.254.0
          inet6 Adresse: fe80::215:58ff:fe7c:f957/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:34807 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:100 
          RX bytes:2338024 (2.2 MB)  TX bytes:8308 (8.1 KB)
          Basisadresse:0x3000 Speicher:ee000000-ee020000 

```

I just used the same data as ifconfig on the other machine showed me, but doesn't make any difference...

---

### Post by superprash2003 on 2008-05-01
do you get an ip address like 77.56.85.201 in the pc?

---

### Post by Shilong on 2008-05-01
yes - it's a bit strange, but that's what I get on the other machine which works fine... so I just copied it to the other one, but I get no connection there

---

### Post by Shilong on 2008-05-01
ok, I had a typo in the netmask... now /etc/networking restart runs through without errors, but that's what syslog tells me:

```
May  1 22:59:57 michele-laptop avahi-daemon[5185]: Interface eth0.IPv4 no longer relevant for mDNS.
May  1 22:59:57 michele-laptop avahi-daemon[5185]: Leaving mDNS multicast group on interface eth0.IPv4 with address 77.56.85.201.
May  1 22:59:57 michele-laptop avahi-daemon[5185]: Withdrawing address record for fe80::215:58ff:fe7c:f957 on eth0.
May  1 22:59:57 michele-laptop avahi-daemon[5185]: Withdrawing address record for 77.56.85.201 on eth0.
May  1 22:59:57 michele-laptop avahi-daemon[5185]: Joining mDNS multicast group on interface eth0.IPv4 with address 77.56.85.201.
May  1 22:59:57 michele-laptop avahi-daemon[5185]: New relevant interface eth0.IPv4 for mDNS.
May  1 22:59:57 michele-laptop avahi-daemon[5185]: Registering new address record for 77.56.85.201 on eth0.IPv4.
May  1 22:59:57 michele-laptop kernel: [ 1635.848000] ADDRCONF(NETDEV_UP): eth0: link is not ready
May  1 22:59:58 michele-laptop kernel: [ 1637.452000] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
May  1 22:59:58 michele-laptop kernel: [ 1637.452000] e1000: eth0: e1000_watchdog: 10/100 speed: disabling TSO
May  1 22:59:58 michele-laptop kernel: [ 1637.456000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
May  1 23:00:00 michele-laptop avahi-daemon[5185]: Registering new address record for fe80::215:58ff:fe7c:f957 on eth0.*.
May  1 23:00:09 michele-laptop kernel: [ 1648.452000] eth0: no IPv6 routers present

```

So I tried to configure the routing table manually:

```
route add default gw 77.56.64.0 eth0
SIOCADDRT: No such process
```

What does that mean?

---

### Post by superprash2003 on 2008-05-01
are you able to ping your router?

---

### Post by Shilong on 2008-05-02
Yes and no: I get 100% packet loss, so I think I can at least send the ping request - otherwise I would expect something like "Network unreachable"...

---

### Post by Shilong on 2008-05-02
Ok, I took the computer to university today and tried to connect to the wireless there: According to NetworkManager, I get a connection (75%), but I don't get any information about it (IP 0.0.0.0 and so on)...

---

