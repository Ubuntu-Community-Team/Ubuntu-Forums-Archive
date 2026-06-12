---
title: "Ethernet problem after upgrading to updating to Ubuntu 14.04. Related to r8168/r8169"
date: 2016-02-04
forum: Networking &amp; Wireless
---

### Post by Akshay_Jain on 2016-02-04
I upgraded to Ubuntu 14.04 from Ubuntu 12.04. Since then the Ethernet is not working properly (connection dies silently after 5 minutes).
I googled and found out that it had something to do between the modules r8168 and r8169.

Initially executing the following commands solved my purpose
```
sudo modprobe -r r8168 && sudo modprobe r8169
```
But this also stopped working now, and in order to resolve the issue I followed the following weblinks: 
[https://unixblogger.wordpress.com/2011/10/18/the-pain-of-an-realtek-rtl8111rtl8168-ethernet-card/](https://unixblogger.wordpress.com/2011/10/18/the-pain-of-an-realtek-rtl8111rtl8168-ethernet-card/)
[http://ubuntuforums.org/showthread.php?t=2240533&page=3&p=13106182#post13106182](http://ubuntuforums.org/showthread.php?t=2240533&page=3&p=13106182#post13106182)

and few other similar links. Now I have only r8168 module and there is no speed after 5 minutes of reboot.
 Every time disable and then enable networking, I get a 5 minutes of internet access.
Please help me out.

The output of uname -a is
```
[FONT=arial]Linux akki-OptiPlex-3020 3.13.0-77-generic #121-Ubuntu SMP Wed Jan 20 10:50:42 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux[/FONT]

```

ifconfig -a 
```
[FONT=arial]eth0      Link encap:Ethernet  HWaddr 64:00:6a:27:4d:51  [/FONT]
[FONT=arial]          inet addr:192.168.22.8  Bcast:192.168.31.255  Mask:255.255.240.0[/FONT]
[FONT=arial]          inet6 addr: fe80::6600:6aff:fe27:4d51/64 Scope:Link[/FONT]
[FONT=arial]          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1[/FONT]
[FONT=arial]          RX packets:568 errors:0 dropped:0 overruns:0 frame:0[/FONT]
[FONT=arial]          TX packets:57 errors:0 dropped:0 overruns:0 carrier:0[/FONT]
[FONT=arial]          collisions:0 txqueuelen:1000 [/FONT]
[FONT=arial]          RX bytes:67551 (67.5 KB)  TX bytes:15685 (15.6 KB)[/FONT]
[FONT=arial]          Interrupt:44 Base address:0xe000 [/FONT]

[FONT=arial]lo        Link encap:Local Loopback  [/FONT]
[FONT=arial]          inet addr:127.0.0.1  Mask:255.0.0.0[/FONT]
[FONT=arial]          inet6 addr: ::1/128 Scope:Host[/FONT]
[FONT=arial]          UP LOOPBACK RUNNING  MTU:65536  Metric:1[/FONT]
[FONT=arial]          RX packets:2384 errors:0 dropped:0 overruns:0 frame:0[/FONT]
[FONT=arial]          TX packets:2384 errors:0 dropped:0 overruns:0 carrier:0[/FONT]
[FONT=arial]          collisions:0 txqueuelen:0 [/FONT]
[FONT=arial]          RX bytes:207212 (207.2 KB)  TX bytes:207212 (207.2 KB)[/FONT]
```

[FONT=arial]sudo modprobe r8169 
[/FONT]```
[FONT=arial]modprobe: FATAL: Module r8169 not found.[/FONT]
```

Please help me resolve the issue. I will be really thankful.

Akshay

---

