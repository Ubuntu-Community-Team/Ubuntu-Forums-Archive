---
title: "no wireless network"
date: 2008-08-21
forum: Networking &amp; Wireless
---

### Post by thecaper on 2008-08-21
hey, so this is my second time installing ubuntu first time everything went fine using hardy this time i tried the newest version and was having a hard time with getting the wireless driver installed but i seemed to get it on following [http://ubuntuforums.org/showthread.php?t=873980&highlight=ndiswrapper+a200](http://ubuntuforums.org/showthread.php?t=873980&highlight=ndiswrapper+a200) but i cannot get it to connect via wireless ive made sure the ssid password is correct but it just tried to connect but never does.. and i cant seem to get it to work no matter what i try. i have a toshiba a200-ah1 with the atheros driver for wireless. its showing me my network and all the other networks in my area but not allowing me to connect to my own with my ssid password or someone elses unlocked one. not sure if i need nething else but help would be great.

hobo@HOBO-PC:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:38:14:74:5a  
          inet addr:192.168.2.12  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:38ff:fe14:745a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11480 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9150 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14164116 (13.5 MB)  TX bytes:1138215 (1.0 MB)
          Interrupt:220 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2234 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2234 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:111700 (109.0 KB)  TX bytes:111700 (109.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1b:9e:2f:28:02  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:3660 (3.5 KB)
          Interrupt:16 Memory:d8000000-d8010000

---

### Post by thecaper on 2008-08-23
bump

---

