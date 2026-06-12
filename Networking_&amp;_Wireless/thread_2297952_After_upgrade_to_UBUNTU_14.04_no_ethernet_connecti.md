---
title: "After upgrade to UBUNTU 14.04 no ethernet connection"
date: 2015-10-07
forum: Networking &amp; Wireless
---

### Post by Inti_Amaru on 2015-10-07
[COLOR=#000000][INDENT]Hi, After updating to [COLOR=#417394]Ubuntu[/COLOR] [COLOR=#417394]14.04[/COLOR], WiFi & [COLOR=#417394]Ethernet[/COLOR] connections stop. By installing ***modprobe b43***, WiFi works now, but on [COLOR=#417394]Ethernet[/COLOR] (cable connected through USB 2.0 Fast [COLOR=#417394]Ethernet[/COLOR] Adapter JP 208B No. 88772A) only google & gmail connect, while other websites no.
 I checked replies to similar problem and tried various suggestions, but nothing helped to reestablish Ethernet.
 Thank you for any suggestions that may work.

ifconfig:
 [/INDENT]
[/COLOR]```


lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:65536 Metric:1
RX packets:2809 errors:0 dropped:0 overruns:0 frame:0
TX packets:2809 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:247766 (247.7 KB) TX bytes:247766 (247.7 KB)


wlan0 Link encap:Ethernet HWaddr c4:85:08:22:77:7f 
inet addr:192.168.1.5 Bcast:192.168.1.63 Mask:255.255.255.192
inet6 addr: fd14:b968:28a2:d500:c685:8ff:fe22:777f/64 Scope:Global
inet6 addr: fe80::c685:8ff:fe22:777f/64 Scope:Link
inet6 addr: fd14:b968:28a2:d500:ad5b:8d42:9f01:912f/64 Scope:Global
inet6 addr: 2800:370:4f:c530:c685:8ff:fe22:777f/64 Scope:Global
inet6 addr: 2800:370:4f:c530:ad5b:8d42:9f01:912f/64 Scope:Global
inet6 addr: 2800:370:4f:c530::4/128 Scope:Global
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:18935 errors:0 dropped:0 overruns:0 frame:0
TX packets:15747 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:11891994 (11.8 MB) TX bytes:2414329 (2.4 MB)
```

---

### Post by howefield on 2015-10-08
Hello and welcome to the forum, I have moved your post to a more suitable location, the "*Networking & Wireless*" forum where there some very knowledgeable posters for your issue.

[http://ubuntuforums.org/showthread.php?t=1006656](http://ubuntuforums.org/showthread.php?t=1006656)
[http://ubuntuforums.org/misc.php?do=bbcode](http://ubuntuforums.org/misc.php?do=bbcode)

---

### Post by Inti_Amaru on 2015-10-08
Hi,
Here is response to *ifconfig*
```

ifconfig
lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:65536 Metric:1
RX packets:2809 errors:0 dropped:0 overruns:0 frame:0
TX packets:2809 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:247766 (247.7 KB) TX bytes:247766 (247.7 KB)

wlan0 Link encap:Ethernet HWaddr c4:85:08:22:77:7f 
inet addr:192.168.1.5 Bcast:192.168.1.63 Mask:255.255.255.192
inet6 addr: fd14:b968:28a2:d500:c685:8ff:fe22:777f/64 Scope:Global
inet6 addr: fe80::c685:8ff:fe22:777f/64 Scope:Link
inet6 addr: fd14:b968:28a2:d500:ad5b:8d42:9f01:912f/64 Scope:Global
inet6 addr: 2800:370:4f:c530:c685:8ff:fe22:777f/64 Scope:Global
inet6 addr: 2800:370:4f:c530:ad5b:8d42:9f01:912f/64 Scope:Global
inet6 addr: 2800:370:4f:c530::4/128 Scope:Global
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:18935 errors:0 dropped:0 overruns:0 frame:0
TX packets:15747 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:11891994 (11.8 MB) TX bytes:2414329 (2.4 MB)

```

---

### Post by Inti_Amaru on 2015-10-10
219 visits, but no any suggestion of solution, it demonstrate that Internet connection issue affects many. I wander when Ubuntu programmers are going to realize and correct the problem. Is LTS real? It seams to me that UBUNTU is taking a WINDOWS road; producing new "looks" with more problems than solutions. 

 Time to use another Linux OS. Thank you for help... Over & out.

---

