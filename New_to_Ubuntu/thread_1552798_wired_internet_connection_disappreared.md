---
title: "wired internet connection disappreared"
date: 2010-08-14
forum: New to Ubuntu
---

### Post by Franz_J on 2010-08-14
Hi folks
I installed ubuntu 10.04 64_bit a few weeks ago dual boot with Windows XP. I connected the ethernet cable (wired connection to a broadband modem) and got internet connection immediately - sweet!. without username or password while the windows internet required a password and userneame.
 
But since yesterday I can't get internet connection and therefore can't install anything - help!. The windows XP internet still connects is ok. I use ubuntu exclusivly for OpenFOAM (computational fluid dynamics)
 
I've searched the forums.
 
Firefox message:
Unable to connect
Firefox can't establish a connection to the server at start.ubuntu.com.
* The site could be temporarily unavailable or too busy. Try again in a few
moments.
* If you are unable to load any pages, check your computer's network
connection.
* If your computer or network is protected by a firewall or proxy, make sure
that Firefox is permitted to access the Web.
 
the ifconfig command gives the following - but I dont know what it means
 
,eth0 Link encap:Ethernet HWaddr 00:1b:fc:ac:13:f6 
inet addr:10.0.0.1 Bcast:10.0.0.255 Mask:255.255.255.0
inet6 addr: fe80::21b:fcff:feac:13f6/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:325 errors:0 dropped:0 overruns:0 frame:0
TX packets:388 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:29749 (29.7 KB) TX bytes:39239 (39.2 KB)
Interrupt:23 Base address:0xc000 
lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:8 errors:0 dropped:0 overruns:0 frame:0
TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:480 (480.0 B) TX bytes:480 (480.0 B)
 
The network manger is running and reports that the wired Auto eth0 is connected
when I type nmi-applet the responce is 'couldn't initilse the D-Bus manager'
 
when I ping the message is 'network is unreadable' 
 
syetem check reports internet not connected - not much help
 
Many thanks:confused:
Franz

---

### Post by LewRockwell on 2010-08-14
disconnect your LAN cable from the computer

reboot your LAN equipment

reboot your computer

reconnect your LAN cable to the computer

as always, your mileage may vary

.

---

### Post by Franz_J on 2010-08-14
thanks [LewRockwell]("http://ubuntuforums.org/member.php?u=847166") it worked! :D 

I'm happily modeling once more 
thanks again

---

