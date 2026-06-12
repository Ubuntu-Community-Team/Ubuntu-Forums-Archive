---
title: "Can't made WiFi to work on Acer 5024 with Ubuntu 6.10 amd64"
date: 2006-11-03
forum: Networking &amp; Wireless
---

### Post by klimtom on 2006-11-03
Anybody knows how to made Wi-Fi to work on Acer 5024? I have Ubuntu  6.10 installed (Amd64), kernel 2.6.17.10. 
I installed NDisWrapper 0.3 and loaded drivers from [ftp://ftp.support.acer-euro.com/notebook/aspire_3020_5020/driver/winxp64bit](ftp://ftp.support.acer-euro.com/notebook/aspire_3020_5020/driver/winxp64bit).
All is as i espected...and my eth1 became wlan0, with the correct MAC address. I now installed acer_acpi... ok, I used the ".ko" trick because i have a 2.6.x kernel, i wrote what s written in all similar forums, ending with:

echo "enabled : 1" > /proc/acpi/acer/wireless

I think all is all right even if my LED has not lightened... But MY wireless is NOT RECOGNIZED AT ALL! :( 

I don't know what to try more... I'm a totally newbie to Linux World...please someone help!!! 

I attach some of my configuration...just for make things simpler (and avoid some questions ^^ )... Those are the results for lspci and ifconfig commands:


klimtom@klimtom-laptop:~$ sudo lspci
[...]
06:05.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
[...]

klimtom@klimtom-laptop:~$ sudo ifconfig -a
eth1      Link encap:Ethernet  HWaddr 00:0A:E4:E1:3D:DF  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:169 Base address:0xe400 

lo        Link encap:Local Loopback  
          LOOPBACK  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:0E:9B:CA:85:CA  
          inet addr:192.168.1.47  Bcast:192.168.1.255  Mask:255.255.255.0
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:58 Memory:c0204000-c0206000

---

