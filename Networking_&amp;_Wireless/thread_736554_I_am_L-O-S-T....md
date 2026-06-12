---
title: "I am L-O-S-T..."
date: 2008-03-26
forum: Networking &amp; Wireless
---

### Post by finalrequiem on 2008-03-26
Ok, I'm running a Lenovo T61p, Intel 4965 ANG (?)...  I am so lost when it comes to wireless stuff, I can't even figure out how to pull up the list of available networks...  I think my wireless is turned off but I can't figure out how to get it to enable.  I have searched the forums a little but, as I stated in another thread, I am still learning Linux since I murdered Vista in a fit of rage...  HELP!         ](*,)

---

### Post by ajmorris on 2008-03-26
hi there,
here are some of the most important commands for network devices:

```
sudo ifconfig
sudo iwconfig
sudo iwlist 
sudo ifup <network device>
```

if you could run the top 2 commands, that will tell us if your wireless device is on.

---

### Post by finalrequiem on 2008-03-26
Here they are:

**_ifconfig:_**
eth0      Link encap:Ethernet  HWaddr 00:1E:37:86:9A:4F  
          inet addr:68.97.127.80  Bcast:68.97.127.255  Mask:255.255.240.0
          inet6 addr: fe80::21e:37ff:fe86:9a4f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:416221 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12467 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:48538895 (46.2 MB)  TX bytes:1500449 (1.4 MB)
          Base address:0x1840 Memory:fe200000-fe220000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

**_iwconfig:_**
IEEE 802.11g  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by dschulz on 2008-03-26
I'd recommend you to install  wifi-radar or kwifimanager (or both!)

$ sudo aptitude install wifi-radar  kwifimanager

[http://wifi-radar.systemimager.org/](http://wifi-radar.systemimager.org/)
[http://kwifimanager.sourceforge.net/](http://kwifimanager.sourceforge.net/)

NetworkManager is another good tool, and probably you have it already installed on your system.

---

### Post by Cap'n Skyler on 2008-03-26
> **finalrequiem said:**
> Ok, I'm running a Lenovo T61p, Intel 4965 ANG (?)...  I am so lost when it comes to wireless stuff, I can't even figure out how to pull up the list of available networks...  I think my wireless is turned off but I can't figure out how to get it to enable.  I have searched the forums a little but, as I stated in another thread, I am still learning Linux since I murdered Vista in a fit of rage...  HELP!         ](*,)
great to whack vista!!
i am trying to get my own wireless worked out,dont give up it is not hard,just a different kind of learning curve.from my own beginner experience,be patient-there are lots of great people here to help you.i also suggest buying a book for Ubuntu,it will help you a lot to understand how linux works,and in particular Ubuntu :)
[http://safari.samspublishing.com/0132435942](http://safari.samspublishing.com/0132435942)
these are very helpful--i have one for fedora 3 LOL 
and browse the forums :)

---

