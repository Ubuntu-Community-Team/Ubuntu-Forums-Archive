---
title: "Networking kubuntu 6.06 and powerbookG4, OSX 10.4.8"
date: 2007-02-22
forum: Networking &amp; Wireless
---

### Post by metalsam on 2007-02-22
So i got my kubuntu desktop plugged into my internet connection in my wall (in my university accomadation), and I want to network my powerbook to it so I can browse files and connect to the internet through it. Just plugging it in doesnt work. 

I tried manually configuring my ethernet on the powerbook, so that the router IP matched that of my kubuntu box, but that hasnt worked. I then pinged kubuntu box, but got no results from that.

Any ideas ? Thank you.

---

### Post by TheWizzard on 2007-02-22
> **metalsam said:**
> So i got my kubuntu desktop plugged into my internet connection in my wall (in my university accomadation), and I want to network my powerbook to it so I can browse files and connect to the internet through it. Just plugging it in doesnt work. 

I tried manually configuring my ethernet on the powerbook, so that the router IP matched that of my kubuntu box, but that hasnt worked. I then pinged kubuntu box, but got no results from that.

Any ideas ? Thank you.

can you be a bit more specific? do you want to access the files on your kubuntu box? 
then you need to configure something like samba or ssh on your kubuntu box. 

please explain your problem more accurate.

---

### Post by metalsam on 2007-02-22
I want to access files on the kubuntu box, as well as use it as a gateway to the internet.

---

### Post by ldbooth on 2007-02-22
Well if you want to plug directly into your kubuntu desktop from the powerbook you will first need a crossover cable -- not your ordinary ethernet cable. 

The other way to go is to use a router to create your own personal network and feed the internet thru the router to each computer. Then you could easily set up a samba share to access files b/t computers.

---

### Post by metalsam on 2007-02-24
I dont need a crossover, mac ethernet has crossover built in. Ive got samba running fine now, but im still stick on how to share the internet. Looks like I need to use iptables.

I installed shorewall - I read that would do it - but it doesnt have a gui. Are there any gui programs I can sue to directly sshare internet ?

---

### Post by mips on 2007-02-24
Use firestarter.

I think you are configuring your mac incorrectly from what you are explaining.

What is the config of your ubuntu box ? (ifconfig -a)
What config do you have on your mac ?

---

### Post by metalsam on 2007-02-25
kubuntu ifconfig -a:

```

eth0      Link encap:Ethernet  HWaddr 00:40:F4:72:4C:DD
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::240:f4ff:fe72:4cdd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:34 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3241 (3.1 KiB)  TX bytes:2529 (2.4 KiB)
          Interrupt:209 Base address:0xef00

eth1      Link encap:Ethernet  HWaddr 00:13:20:AD:77:F7
          inet addr:172.17.4.146  Bcast:172.17.255.255  Mask:255.255.0.0
          inet6 addr: fe80::213:20ff:fead:77f7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12143 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6709 errors:0 dropped:0 overruns:0 carrier:0
          collisions:2453 txqueuelen:1000
          RX bytes:6944725 (6.6 MiB)  TX bytes:1191683 (1.1 MiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:41 errors:0 dropped:0 overruns:0 frame:0
          TX packets:41 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:3820 (3.7 KiB)  TX bytes:3820 (3.7 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

Mac ifconfig -a :
```

lo0: flags=8049<UP,LOOPBACK,RUNNING,MULTICAST> mtu 16384
        inet 127.0.0.1 netmask 0xff000000 
        inet6 ::1 prefixlen 128 
        inet6 fe80::1%lo0 prefixlen 64 scopeid 0x1 
gif0: flags=8010<POINTOPOINT,MULTICAST> mtu 1280
stf0: flags=0<> mtu 1280
en0: flags=8863<UP,BROADCAST,SMART,RUNNING,SIMPLEX,MULTICAST> mtu 1500
        inet6 fe80::214:51ff:fe22:30b4%en0 prefixlen 64 scopeid 0x4 
        inet 192.168.0.2 netmask 0xffffff00 broadcast 192.168.0.255
        ether 00:14:51:22:30:b4 
        media: autoselect (100baseTX <full-duplex>) status: active
        supported media: none autoselect 10baseT/UTP <half-duplex> 10baseT/UTP <full-duplex> 10baseT/UTP <full-duplex,hw-loopback> 100baseTX <half-duplex> 100baseTX <full-duplex> 100baseTX <full-duplex,hw-loopback> 1000baseT <full-duplex> 1000baseT <full-duplex,hw-loopback> 1000baseT <full-duplex,flow-control> 1000baseT <full-duplex,flow-control,hw-loopback>
en1: flags=8863<UP,BROADCAST,SMART,RUNNING,SIMPLEX,MULTICAST> mtu 1500
        ether 00:14:51:7c:7a:53 
        media: autoselect (<unknown type>) status: inactive
        supported media: autoselect
fw0: flags=8863<UP,BROADCAST,SMART,RUNNING,SIMPLEX,MULTICAST> mtu 4078
        lladdr 00:14:51:ff:fe:22:30:b4 
        media: autoselect <full-duplex> status: inactive
        supported media: autoselect <full-duplex>

```

Ill give firestarter a go.

---

