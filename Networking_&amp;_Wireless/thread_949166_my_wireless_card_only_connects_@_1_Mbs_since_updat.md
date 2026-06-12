---
title: "my wireless card only connects @ 1 Mb/s since update"
date: 2008-10-15
forum: Networking &amp; Wireless
---

### Post by kmb101 on 2008-10-15
I think this might be a bug in yesterdays updates. I updated yesterday via the update manager and now my wlan0 only connects at 1 Mb/s and before I updated I connected at 54 Mb/s. I have a broadcom card 4318 I am using the b43 driver with no previous problems. I have compaq laptop R4125us running Ubuntu 8.04 LTS. Any help or suggestions appreciated.

---

### Post by penguinpi.com on 2008-10-16
use ethtool to see what the interface is set to

~# ethtool wlan0


What is "Speed:" set to. or just post the whole output.

---

### Post by kmb101 on 2008-10-16
Thanks for the suggestion. How do I use ethtool? I tried the command and it said not found. Thats what I really need is a command to change my cards settings in case it happens again. I have not had this problem until now. Thanks in advance.

---

### Post by theevilhamster on 2008-10-16
not in ubuntu now because i'm having wireless problems too (AH! THE IRONY!) but try this:

```
sudo apt-get install ethtool
```

then run

```
ethtool
```

let me know if this works and i hope it helps.

---

### Post by kmb101 on 2008-10-16
Seems like alot of people are having wireless problems. I could be doing something wrong. I did install ethtool successfully but the ethtool command does not work you have to add something to it and I am to new to know what that is. I hope you get your wireless problems fixed. Thanks again

---

### Post by kmb101 on 2008-10-16
This is my output.
kevin@Presario4125:~$ ethtool wlan0
Settings for wlan0:
No data available
kevin@Presario4125:~$ ethtool -a wlan0
Pause parameters for wlan0:
Cannot get device pause settings: Operation not supported
kevin@Presario4125:~$ ethtool -i wlan0
Cannot get driver information: Operation not supported
kevin@Presario4125:~$ ethtool speed
Settings for speed:
Cannot get device settings: No such device
Cannot get wake-on-lan settings: No such device
Cannot get message level: No such device
Cannot get link status: No such device
No data available
kevin@Presario4125:~$

---

### Post by penguinpi.com on 2008-10-16
Seems like it is not installed. your sure its wlan0 not eth1 or something. check ifconfig. does lspci find your wireless device?

Commands

~# ifconfig

~# lspci  (look for something that looks like your wireless)

---

### Post by kmb101 on 2008-10-16
> **penguinpi.com said:**
> Seems like it is not installed. your sure its wlan0 not eth1 or something. check ifconfig. does lspci find your wireless device?

Commands

~# ifconfig

~# lspci  (look for something that looks like your wireless)
This is my output it is installed.
wlan0     Link encap:Ethernet  HWaddr 00:90:4b:ef:38:52  
          inet addr:192.168.0.102  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::290:4bff:feef:3852/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16777 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8681 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13370513 (12.7 MB)  TX bytes:1476202 (1.4 MB)
Any suggestions??? I just need my speed back to 54 Mb/s. It is a slow connection to me at 1 Mb/s. Its hard to watch videos or listen to streaming radio at this speed. Thanks!!

---

