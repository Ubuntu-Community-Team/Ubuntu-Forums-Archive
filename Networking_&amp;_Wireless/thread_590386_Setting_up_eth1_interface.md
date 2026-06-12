---
title: "Setting up eth1 interface"
date: 2007-10-24
forum: Networking &amp; Wireless
---

### Post by frojnd on 2007-10-24
I have this problem that even though I set my /etc/network/interfaces I still can't connect to the internet: I've manually deleted eth0 which is my wired eth cause I thought eth0 and eth1 are "fighting "each other.

Here is the output of /etc/network/interfaces
```
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0


iface eth0 inet dhcp

iface eth1 inet static
address 192.168.0.27
netmask 255.255.255.0
gateway 192.168.0.1
wireless-key aaaaaaaaa1
wireless-essid router2
```

If I wanna to connect to the internet I have to set dns, whic for this router are: 193.2.1.66
193.2.1.72

Here is the output of /etc/resolv.conf
```
nameserver 193.2.1.66
nameserver 193.2.1.72
```


And here is my ifconfig eth1
```
eth1      Link encap:Ethernet  HWaddr 00:19:7E:11:56:1A  
          inet addr:192.168.0.27  Bcast:192.168.0.255  Mask:255.255.255.0
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:5 
```

I can connect at home on my wired network. But here where is wireless something is wrong. I sume that eth1 and eth0 are "fighting" each other. I hope someone will try to help me out.

---

