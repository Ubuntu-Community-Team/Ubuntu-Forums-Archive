---
title: "Activate LAN card with 10.10 - Dell"
date: 2011-03-08
forum: New to Ubuntu
---

### Post by Engineer65 on 2011-03-08
Have installed 10.10 on a Dell Inspiron - B130.  Seems to be working fairly well but can't get things to connect to the internet via wireless.  The lan card is on and active, have entered the WEP encryption codes, have entered the SSID but to no avail.  I suspect I have a problem with a proprietory driver with Dell but not sure.  Since I have no connection with the computer, even if I had a driver located, how would I install it?  Need to know if that is most likely the problem, if there is a driver available, and how to get it installed.  In other words, help.

---

### Post by kimberlite on 2011-03-08
Let's see the output of the following terminal commands:
```
ifconfig
```
```
lspci |grep Network
```

---

### Post by Engineer65 on 2011-03-08
ifconfig-
eth0
link encap:Ethernet  HWaddr 00:14:22:97:35:af
UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
Collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
Interrupt:18
 
lo
Link encap: Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr:  ::1/128 Scope:Host
UP LOOPBACK RUNNING  MTU:16436  Metric:1
RX packets:8 errors:0 dropped:0 overruns:0 frame:0
TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueue:0
RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

---

### Post by Engineer65 on 2011-03-08
lspci |grep Network
 
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless Lan Controller (rev 02)

---

### Post by Engineer65 on 2011-03-10
Found solution at help.ubuntu.com/community/WifiDocs/Driver then under Driverbcm43XX.  Some file names are a little different but easily figured out.  Follow the instructions and it works.  Instructions indicated might have to restart to make it work but mine started working as soon as the driver was installed.  The problem is that Broadcom uses a proprietory driver for its lan board which can't be supplied with the 10.10 download so you have to go thru the procedures in the article to get it to work.

---

