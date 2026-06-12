---
title: "Wifi connection established ?"
date: 2005-04-16
forum: Networking &amp; Wireless
---

### Post by nborde on 2005-04-16
Hi,

My Ubuntu seems to work perfectly on my laptop now, except the Wifi connection.

The connection seems to be established, the Access Point mac adress is the one of my router and packets are sent and recieved.

However I can't ping my router (192.168.1.1) or, of course, do anything on the internet or on the network.

There is the result of *iwconfig* :
```

eth1      IEEE 802.11g  ESSID:"guilde"  
          Mode:Managed  Frequency:2.427 GHz  Access Point: 00:11:D8:18:B4:86   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=-27 dBm  Noise level=-83 dBm
          Rx invalid nwid:0  Rx invalid crypt:231  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

*ipconfig* :
```

eth1      Lien encap:Ethernet  HWaddr 00:0E:35:C9:16:3F  
          adr inet6: fe80::20e:35ff:fec9:163f/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:528 errors:231 dropped:231 overruns:0 frame:0
          TX packets:118 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 lg file transmission:1000 
          RX bytes:0 (0.0 b)  TX bytes:6480 (6.3 KiB)
          Interruption:22 Adresse de base:0xe000 Mémoire:d0200000-d0200fff 

lo        Lien encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6340 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6340 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          RX bytes:575520 (562.0 KiB)  TX bytes:575520 (562.0 KiB)

```

And a screenshot of the connection box :
[img]http://bgw.free.fr/eth1.png[/img]

I thought the problem may be caused by the channel. May be the ubuntu used the wrong channel... I also checked my WEP key... It's ok! So I did that :
```

iwconfig eth1 essid guilde channel 4 mode Managed ap ...

```

I have a Asus WL500G router, directly pluged to my ADSL Modem...

---

### Post by luca_linux on 2005-04-16
Are you sure you have set the gateway ip address and the DNS?

---

### Post by nborde on 2005-04-17
I did.

Anyway I can not ping my router (192.168.1.1) and I'd be able to do that even if DNS and Gateway aren't set using its IP.

I don't understand, I also checked /etc/resolv.conf that's ok.

---

### Post by luca_linux on 2005-04-17
And are you sure you haven't set MAC Address Protection on your router and so you have to enable the MAC address for your card? Or any other protections?

---

### Post by nborde on 2005-04-17
yes I am...

---

### Post by nborde on 2005-04-18
Well it seems that eth1 uses an IPv6 adress and that's the problem.

I tried *ifconfig eth1 192.168.1.3 netmask 255.255.255.0* and then *ifconfig up* but it didn't change anything :/

An idea ?

---

### Post by wobj on 2005-04-18
Hi... I have the same problem with my wifi connection on my laptop. I have the Intel Pro 2200BG card and I use the ipw2200 driver. It's so strange because the wlan-card receives signals from the accesspoint, but still I can't reach my home network or the internet.

---

### Post by luca_linux on 2005-04-18
Try to disable ipv6 support for that device.

---

### Post by wobj on 2005-04-18
how do i disable ipv6?

---

### Post by nborde on 2005-04-19
well I don't know how to disable IPv6... A friend told me I'd have to rebuild the kernel...

---

### Post by Toddy on 2005-04-19
Try setting your router to "open" authentication.  I don't beleive that you can connect if it is set to "shared".

---

### Post by speedman on 2005-04-19
To turn off ipv6 edit /etc/modprobe.d/aliases and change:

alias net-pf-10 ipv6

to:

alias net-pf-10 off


Regards,

SM

---

### Post by Sarcaza on 2005-06-12
I had a similar problem, used the steps in the previous post to disable ipv6 and it seems to work great now.

---

