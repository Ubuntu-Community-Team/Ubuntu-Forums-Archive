---
title: "WiFi works on windows, but partically on Linux"
date: 2007-03-27
forum: Networking &amp; Wireless
---

### Post by BDwinsAlt on 2007-03-27
I have a Dell Inspiron 1501 and I followed these instructions to set up my wifi card a while back.  [http://ubuntu1501.blogspot.com/2007/01/fixing-wifi-on-dell-1501.html](http://ubuntu1501.blogspot.com/2007/01/fixing-wifi-on-dell-1501.html)

Everything works great on both windows and linux except when I try to connect to an a mode router instead of a b or g it connects and then disconnects.

I use wifi-radar and it says connected to None ip(None) the ip then updates and then goes back to none.  I tried setting the information up manually instead of automatic DCHP.  No luck.

Also, at school they have a wireless router with g mode.  It looks like any other unsecured network but it won't connect to that either.

My laptop has connected to all of the other nonsecured networks I have tried. (Atleast 20).  It even works on my secured network.

Please help me figure this out.  I have a Broadcom Card.  I'll post the ifconfig also.

ifconfig
```

eth1      Link encap:Ethernet  HWaddr 00:16:CF:CE:84:51  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:cfff:fece:8451/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:27691 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6605 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8870216 (8.4 MiB)  TX bytes:1300101 (1.2 MiB)
          Interrupt:201 Memory:c0200000-c0204000 

```

iwconfig
```

lo        no wireless extensions.

eth1      IEEE 802.11g  ESSID:"Davis WiFi"  Nickname:"Davis WiFi"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0D:88:EC:FF:FE   
          Bit Rate=54 Mb/s   Tx-Power:32 dBm   
          RTS thr=2347 B   Fragment thr=2346 B   
          Encryption key:****-****-**   Security mode:open
          Power Management:off
          Link Quality:48/100  Signal level:-65 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.


```

Thanks.

EDIT: Also for the a mode router, on the logs it trys to connect to 255.255.255.255 port 67.

---

### Post by Floppyjoe on 2007-03-27
I am not certain about the A-mode problem but does your school wifi possibly use mac address filtering so only authorized computers can log on to it? This would make it look like an unsecured access point but it would not allow you to log on to it unless your mac address was on the good list.

---

### Post by BDwinsAlt on 2007-03-28
I know they were planning on making a mobile computer lab with just laptops.  A girl in my English class said she can sometimes connect with Windows XP.

Kinda weird.  :(

---

