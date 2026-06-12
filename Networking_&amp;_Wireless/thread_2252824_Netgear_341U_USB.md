---
title: "Netgear 341U USB"
date: 2014-11-14
forum: Networking &amp; Wireless
---

### Post by Claude_Sutton on 2014-11-14
HP Pavilion
Ubuntu 14.04 64 bit

Cradlepoint 1200B router.

Cradlepoint lists the Netgear 341U as a supported option.

Netgear 341U works when installed in router using ethernet cable.

However the 341U can not be updated, and I have been notified that one is due, unless the 341U is in a USB slot in the computer.  Can not update in the router.

Ubuntu will not recognize the 341U.

I have installed GobiNet and GobiSerial.

I also installed Gobi-loader in hopes that would help.

I also created a Sprint connection in the connections page.

I am using Sprint and am in a decent 4G area.

lsusb lists the 341U.

When it is in the usb slot in the computer, the connection menu in the menu bar shows it is there by the fact that it lists the sprint connection I created  and is lists broadband as an option.

I hope someone here has a suggestion.

---

### Post by Claude_Sutton on 2014-11-15
No reply so......

For ubuntu 14.04.


Who is using sprint aircards and what brand has been successful for you?

I am tired of fooling with the Netgear although it may be the problem is due to it being two years old and never used.

---

### Post by Claude_Sutton on 2014-11-15
I have finally got the netgear 341U problem down to the fact that ifconfig does not list it.

Lsusb does.

my kernal is supported.

GobiNet and GobiSerial have the required files.

So I need to get the air card recognized in /dev/ttyUSB.

I don't know how.

---

### Post by Claude_Sutton on 2014-11-15
The output of ifconfig:

 			eth0      Linkencap:Ethernet  HWaddr 08:2e:5f:8a:54:ba  
          UPBROADCAST MULTICAST  MTU:1500  Metric:1
          RXpackets:56758 errors:0 dropped:0 overruns:0 frame:0
          TXpackets:51428 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000 
          RXbytes:52787526 (52.7 MB)  TX bytes:6695393 (6.6 MB)
eth1      Linkencap:Ethernet  HWaddr a2:bb:92:6d:08:08  
          UPBROADCAST NOARP MULTICAST  MTU:1500  Metric:1
          RXpackets:0 errors:0 dropped:0 overruns:0 frame:0
          TXpackets:0 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000 
          RX bytes:0(0.0 B)  TX bytes:0 (0.0 B)
lo        Linkencap:Local Loopback  
          inetaddr:127.0.0.1  Mask:255.0.0.0
          inet6addr: ::1/128 Scope:Host
          UPLOOPBACK RUNNING  MTU:65536  Metric:1
          RXpackets:21381 errors:0 dropped:0 overruns:0 frame:0
          TXpackets:21381 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:0 
          RXbytes:1929675 (1.9 MB)  TX bytes:1929675 (1.9 MB)
wlan0     Linkencap:Ethernet  HWaddr 4c:eb:42:6b:25:6f  
          UPBROADCAST MULTICAST  MTU:1500  Metric:1
          RXpackets:11521 errors:0 dropped:0 overruns:0 frame:0
          TXpackets:10198 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000 
          RXbytes:9400055 (9.4 MB)  TX bytes:1440474 (1.4 MB)

---

### Post by Claude_Sutton on 2014-11-16
I have found out how to update the air card through the router and have done so.

However, I still can not get the card to work when installed in the USB slot in the computer.

To update in the router, load the router in one browser window with the customary 192.168.0.1.

Find the page where NAT is selected and force the selection of NAT.

Do not close this browser window.

Open a second window and in the address box 192.168.1.1

The Srint 341U modem window will then open and after entering the password, you can update, change settings, etc.

I am not familiar with other routers, but with the Cradlepoint router you can not close the router window and load the modem window. 

I really don't care, except that I hate to admit it beat me, about not being able to use the card in the computer slot.  Even when traveling, I take my router.

Although this still leaves part of the problem unsolved, I post this with the thought thaat it might help someone else get closer to the solution they are looking for.

---

