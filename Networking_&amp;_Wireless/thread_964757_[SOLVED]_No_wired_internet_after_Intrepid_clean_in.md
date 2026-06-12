---
title: "[SOLVED] No wired internet after Intrepid clean install"
date: 2008-10-31
forum: Networking &amp; Wireless
---

### Post by Absorbed on 2008-10-31
My ethernet worked fine on Hardy, but with Intrepid it doesn't. Tinkering with Network manager hasn't fixed anything.

lspci -knn:
```
01:08.0 Ethernet controller [0200]: Intel Corporation 82801DB PRO/100 VE (LOM) Ethernet Controller [8086:1039] (rev 82)
	Kernel driver in use: e100
	Kernel modules: e100, eepro100
```

ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:0d:87:f3:9c:b4  
          UP BROADCAST RUNNING MULTICAST  MTU:64  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1240 (1.2 KB)  TX bytes:1859 (1.8 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:74 errors:0 dropped:0 overruns:0 frame:0
          TX packets:74 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3692 (3.6 KB)  TX bytes:3692 (3.6 KB)
```

if I ping my router:
```
connect: Network is unreachable
```

when I first typed "sudo ifup eth0" I get this:
```
ifup: interface eth0 already configured
```

I then typed "sudo ifdown eth0" and got this:
```
Ignoring unknown interface eth0=eth0.
```

But when I typed "sudo ifup eth0" again after the above two commands I got this:
```
Ignoring unknown interface eth0=eth0.
```

This was the point where I hit the limit of my knowledge. I think my problem might be related to this thread: [http://ubuntuforums.org/showthread.php?t=963335](http://ubuntuforums.org/showthread.php?t=963335) When I typed "sudo ifconfig eth0 10.0.0.8" I got "SIOCSIFADDR: No buffer space available".

Help!

---

### Post by Absorbed on 2008-10-31
There is a workaround for this problem here: [http://ubuntuforums.org/showpost.php?p=6075466&postcount=25](http://ubuntuforums.org/showpost.php?p=6075466&postcount=25)

1. Disable NetworkManager:
```
sudo update-rc.d -f NetworkManager remove
```

2. Reboot

3. 
```
dhclient eth0
```

After that the internet worked fine.

I made the internet stay after a reboot by adding this to my /etc/network/interfaces:
```
auto eth0
iface eth0 inet dhcp

```

---

### Post by janbockaert on 2008-10-31
hi,

this worked for me, i only had tot type

```
sudo dhclient eth0
```

to get my connection.

---

### Post by dwende on 2008-11-01
This does NOT work for me. Anyone got any good ideas.

If have tried both using the static way and also using
dhclient eth0

Neither way gives me even a route to my router.

i.e.
ping 10.0.0.2
gives 100% packet loss.

---

### Post by StowmarKate on 2008-12-10
Hi guys, I tried this and I now can't get my wireless working (wired is fine). Help!

---

