---
title: "Setting up static IP address on a wep wifi"
date: 2013-10-20
forum: Networking &amp; Wireless
---

### Post by alfredomg on 2013-10-20
Hello,

I have this rather old laptop running Ubuntu 10.04 which I mostly use as a server for various things. The laptop is usually connected to my router via a wired connection, using a static IP. That has worked very well so far. However, I need to temporarily move the laptop to another room in the house and would like to use a static IP on its wifi so I can continue accessing it as a server during this time. However, I've been unsuccessful in getting the wireless connection to work at all. I haven't used the wifi connection literally in years and I think at some point it was disabled and I think it's because of that I've been unsuccessful (basically, I've messed up with it quite a bit). I've been following this thread, but haven't been successful so far: [http://ubuntuforums.org/showthread.php?t=1704257](http://ubuntuforums.org/showthread.php?t=1704257)

Here you can see my /etc/network/interfaces file (the key and the network name are fake/placeholders):
```

auto lo eth0
iface lo inet loopback
iface eth0 inet static
    address 192.168.1.5
    netmask 255.255.255.192
    gateway 192.168.1.1

auto eth1
iface eth1 inet static
    address 192.168.1.8
    netmask 255.255.255.192
    gateway 192.168.1.1
    wireless-key 1234ABCDEF56789
    wireless-essid MyNetwork

```

Here's the output to the ifconfig and iwconfig commands:

```

me@pc:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:43:4b:d6:ec  
          inet addr:192.168.1.5  Bcast:192.168.1.63  Mask:255.255.255.192
          inet6 addr: fe80::211:43ff:fe4b:d6ec/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:176633 errors:0 dropped:0 overruns:0 frame:0
          TX packets:181793 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:47251614 (47.2 MB)  TX bytes:39008783 (39.0 MB)
          Interrupt:11 

eth1      Link encap:Ethernet  HWaddr 00:12:f0:02:47:bd  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1 errors:0 dropped:10 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:84 (84.0 B)
          Interrupt:5 Base address:0x4000 Memory:fafef000-fafeffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:369 errors:0 dropped:0 overruns:0 frame:0
          TX packets:369 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:93885 (93.8 KB)  TX bytes:93885 (93.8 KB)

me@pc:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"f2\x0D\xB71X\xA3Z%]\x05\x17X\xE9^\xD4\xAB\xB2\xCD\xC6\x9B\xB4T\x11\x0E\x82tA!=\xDC\x87"  
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Any ideas on how I can get the wifi to work? Thanks a lot in advance for your help.

By the way, my computer is a DELL Latitude D600.

---

### Post by mörgæs on 2013-10-20
Hi, welcome to the fora. 

10.04 is an old release and by far most users here have moved to something newer. Have you thought of a fresh install of 12.04 or 13.10?

---

### Post by alfredomg on 2013-10-21
Thanks for the welcoming! 

Yes, I'll probably install a newer version of ubuntu. That should help take care of this problem. However, since it's a rather old laptop, I'll probably go for lubuntu or something lightweight.

---

### Post by mörgæs on 2013-10-23
Good choice.
If this solves your problem please mark the thread so.

---

