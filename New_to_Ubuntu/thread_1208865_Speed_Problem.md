---
title: "Speed Problem"
date: 2009-07-09
forum: New to Ubuntu
---

### Post by Ed Case on 2009-07-09
Hello all, I'm trying to get a grip on this Ubuntu. I have installed 6.06 on an old Compaq Proliant, but speeds to and from the server are worse than a dial up modem. I have an XP machine and the server on a wired 10/100 connection to the router then to a broadband cable modem. Speeds from the XP to the outside world average 8-10Mgs, but speed from the server to the XP and to the repositories is only 40-45kbps, about like a dial up modem, anyone got any ideas?

---

### Post by iponeverything on 2009-07-09
Try a more recent release. The download is free and with your broadband connection, it should not take long.

---

### Post by Ed Case on 2009-07-10
Thanks ip, I tried a more recent release a while ago, but the CDROM isn't recognised, that's why I used the older Dapper, it supported the CDROM.

---

### Post by superprash2003 on 2009-07-10
are these download speeds or torrent speeds?? post output of** ifconfig **from the terminal

---

### Post by Ed Case on 2009-07-10
Here it is superprash, thank you



eth0      Link encap:Ethernet  HWaddr 00:00:E8:16:35:1A  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::200:e8ff:fe16:351a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:157 errors:0 dropped:0 overruns:0 frame:0
          TX packets:171 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16479 (16.0 KiB)  TX bytes:22947 (22.4 KiB)
          Interrupt:5 Base address:0x6d00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)

---

### Post by superprash2003 on 2009-07-11
you could try disabling ipv6 [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4) .. and if you still face issues then try changing MTU values [http://www.prash-babu.com/2009/06/how-to-change-mtu-in-ubuntu-using-gui.html](http://www.prash-babu.com/2009/06/how-to-change-mtu-in-ubuntu-using-gui.html)

---

### Post by Yvan300 on 2009-07-11
In what release was your CD drive not recognised and when you are talking about your sluggish speeds are you refering to the download speed inside Add and Remove/Synaptics or do you mean your download speed in firefox etc.

---

### Post by Ed Case on 2009-07-11
Superprash, thank you, I have just blacklisted ipv6. I am on the server with command line only. The only place I know to find MTU is on my router.

Yvan.
Thank you for the response, I have tried 7.* and 8.*, neither recognises the cdrom. Perhaps, if I could find the relevant driver in ver 6.06, I could copy it to floppy and then use that to install 9.04 or maybe a little earlier LTS server. The speed is over the LAN between server on 6.06 and a desktop on XP SP3. The connection is wired on 10/100 cards.

ipv6 now disabled, but no change, still about 1Mg per 75 seconds over the LAN, WINS enabled,

Thanks both

---

### Post by Yvan300 on 2009-07-11
Wow, i didn't realised you were running a server, well then what may actually be bottlenecking your system is the version of ubuntu you are running. Why not buy another cd-rom, a cd rom drive these days would be quite cheap but then again can be a waste of money if your problem persists. But what you can do is get a boot floppy so that you will be able to boot from usb and thus be able to install jaunty, hope it works :)

---

