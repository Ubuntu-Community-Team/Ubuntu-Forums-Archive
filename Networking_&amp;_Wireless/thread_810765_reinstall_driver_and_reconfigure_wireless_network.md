---
title: "reinstall driver and reconfigure wireless network?"
date: 2008-05-28
forum: Networking &amp; Wireless
---

### Post by Lourie2 on 2008-05-28
I had my machine connect to the network wirelessly for about 3 weeks after setting it up with HOWTO: RT73 (RT71) serialmonkey drivers.  This evening, it lost connection after about being on the net for a minute.  When I do a iwconfig, I get: ```
name@name-IBM:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
```

What I think I have to do, is reinstall the driver and reconfigure.  What do I have to do before I do that, or should I do something different?

---

### Post by Bartender on 2008-05-28
Hi, Lourie - 
Betcha installed updates, including the latest kernel update?

Try plugging into an ethernet connection and reinstalling those drivers.

---

### Post by Lourie2 on 2008-05-28
You're right!!!  Was the last thing I did this morning, before shutting down.  Thanks for the advice, I'll try it.

---

### Post by Lourie2 on 2008-05-28
Hi. I had to reinstall my wireless network driver with HOWTO: RT73 (RT71) serialmonkey drivers after having installed the latest kernel update.  I have reached the point where I should be able to connect to the internet, but this is not possible.

Something I did not know, was which "yyyymmddhh" I should use, as there were 3 blue entries.  I settled for the third one, as I thought it would be the correct one. (Thinking... Perhaps the 1st one would work, as it had worked previously, but then, perhaps this has nothing to do with it).

This is the last bit of output:
```
name@name-IBM:/usr/src/rt73-cvs-2008050914/Module$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:11:25:67:08:b7  
          inet addr:192.168.1.65  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:25ff:fe67:8b7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1705 errors:0 dropped:0 overruns:0 frame:0
          TX packets:757 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:777203 (758.9 KB)  TX bytes:84362 (82.3 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:714 errors:0 dropped:0 overruns:0 frame:0
          TX packets:714 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:35700 (34.8 KB)  TX bytes:35700 (34.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:0e:2e:4a:c0:f7  
          inet6 addr: fe80::20e:2eff:fe4a:c0f7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:162 errors:0 dropped:0 overruns:0 frame:0
          TX packets:110 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17060 (16.6 KB)  TX bytes:7260 (7.0 KB)

name@name-IBM:/usr/src/rt73-cvs-2008050914/Module$ sudo ifconfig wlan0 up
name@name-IBM:/usr/src/rt73-cvs-2008050914/Module$ sudo iwconfig wlan0 essid "correct name"
name@name-IBM:/usr/src/rt73-cvs-2008050914/Module$ sudo iwconfig wlan0 key "correct key"
name@name-IBM:/usr/src/rt73-cvs-2008050914/Module$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:0e:2e:4a:c0:f7
Sending on   LPF/wlan0/00:0e:2e:4a:c0:f7
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPOFFER of 192.168.1.68 from 192.168.1.254
DHCPREQUEST of 192.168.1.68 on wlan0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.68 from 192.168.1.254
bound to 192.168.1.68 -- renewal in 37057 seconds.
name@name-IBM:/usr/src/rt73-cvs-2008050914/Module$ sudo ifconfig wlan0 up
name@name-IBM:/usr/src/rt73-cvs-2008050914/Module$ sudo iwconfig wlan0 essid "correct name"
name@name-IBM:/usr/src/rt73-cvs-2008050914/Module$ sudo iwconfig wlan0 key "correct key"
name@name-IBM:/usr/src/rt73-cvs-2008050914/Module$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 6421
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:0e:2e:4a:c0:f7
Sending on   LPF/wlan0/00:0e:2e:4a:c0:f7
Sending on   Socket/fallback
DHCPREQUEST of 192.168.1.68 on wlan0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.68 from 192.168.1.254
bound to 192.168.1.68 -- renewal in 37850 seconds.
name@name-IBM:/usr/src/rt73-cvs-2008050914/Module$
```

I did the last bit twice, just to make sure I did it right.

---

### Post by chili555 on 2008-05-28
> I have reached the point where I should be able to connect to the internet, but this is not possible.You are indeed connected:> DHCPACK of 192.168.1.68 from 192.168.1.254
bound to 192.168.1.68 -- renewal in 37057 seconds.Have you tried and failed to browse the web?

---

### Post by Lourie2 on 2008-05-28
Yes, and also, the network icon has a yellow triangle on it.

---

### Post by chili555 on 2008-05-28
Please let us see:```
ping -c3 192.168.1.254
ping -c3 74.125.47.147
cat /etc/resolv.conf
```Thanks.

---

### Post by Lourie2 on 2008-05-28
Chili555, you are right, I am now connected... traditional medicine...Shutdown and restart... Thanks for your help.

---

