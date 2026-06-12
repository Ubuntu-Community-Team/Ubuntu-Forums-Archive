---
title: "wired internet connect"
date: 2010-08-04
forum: New to Ubuntu
---

### Post by Had on 2010-08-04
Hi all
I have a modem am300 Linksys with a network cable and a USB cable. I need to connect with USB cable to Internet but There are five LED light on modem: Power , Ethernet , USB , DSL , Internet and are all on  except ethernet but I can't ping or use browser site addresses with a not found error.
Modem have an IP that can go to modem setup and I change it correctly with my provider info. 
I use of pppoeconf application but it can't find any ....  in my computer! But I make one with:
```
pppoeconf tap0
``` 
and this is answers:
```
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:e1:a7:76:76:81  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e1:a7ff:fe76:7681/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:198 errors:0 dropped:0 overruns:0 frame:0
          TX packets:250 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:118672 (115.8 KiB)  TX bytes:24552 (23.9 KiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:560 (560.0 B)  TX bytes:560 (560.0 B)

```
and
```
pon dsl-provider
Plugin rp-pppoe.so loaded.
/usr/sbin/pppd: In file /etc/ppp/peers/dsl-provider: unrecognized option 'nic-tap0'

```
and nothig! I change "nic-tap0" in /etc/ppp/peers/dsl-provider with "eth0" and answer changed to :
```
pon dsl-provider
Plugin rp-pppoe.so loaded.
```
but still nothing happen .
regards!

---

### Post by grahammechanical on 2010-08-04
I am new to helping solve these problems. So, I may not have the right answers. My modem/router has 5 LEDs. Power, Ethernet, Wireless, Broadband, Internet. May be you do not have a broadband connection. Or may be DSL = Broadband. My Ethernet light is out until I put the ethernet cable into the modem and computer. Then the LED comes on. Then Network manger gives a message saying there is an ethernet connection and the icon changes to two black arrows pointing in opposite directions.

Do you have a network manager icon in the top right corner of the screen. If so, left click the icon. Do you get a list of network connections. I have two wired connections eth0 and eth1 and a wireless connection with the name of my ISP. I do not know if any of this helps.

If you go to System - Administration - Users and Groups. You can select your profile. Under Advance settings you can see if you have permission to access the internet using a modem. If you right click the network icon and select a connection to edit, you can mark that connection to connect automatically and make it available to all users. May be this information will help. I am sorry if it does not.

Regards.

---

### Post by dineshs on 2010-08-04
I think it is difficult to get the router working via USB.Why dont you try ethernet?
If ethernet light is not blinking > ifconfig
eth0      Link encap:Ethernet  HWaddr 00:e1:a7:76:76:81  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e1:a7ff:fe76:7681/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:198 errors:0 dropped:0 overruns:0 frame:0
          TX packets:250 errors:0 dropped:0 overruns:0 carrier:0
How this IP?Did you configure manually?

---

### Post by Had on 2010-08-05
My system can't work with network port! this is made in 2001  
No! this configuration made by pppoeconf command. I have a USB Winmodem too and now connect with it but this is very hard and frequently near 20 Min I must spend for each connect!

---

### Post by dineshs on 2010-08-05
> My system can't work with network port! this is made in 2001 But you have got an IP
pl connect your PC to the router via ethernet cable.Then post the results of
```
ping 4.2.2.1 -c3
```

---

### Post by Had on 2010-08-05
Thank you for your response!

this is answers:
```
[SIZE=4][B]# ping 4.2.2.1 -C3
connect: Network is unreachable
[/B][/SIZE]
```
and I think this may be useful :
```
[SIZE=4][B]# traceroute -n 4.2.2.1
traceroute to 4.2.2.1 (4.2.2.1), 30 hops max, 40 byte packets
connect: Network is unreachable[/B][/SIZE]
```

---

