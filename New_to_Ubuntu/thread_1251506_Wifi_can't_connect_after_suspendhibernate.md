---
title: "Wifi can't connect after suspend/hibernate"
date: 2009-08-27
forum: New to Ubuntu
---

### Post by mvalviar on 2009-08-27
I'm using this: ```
id:	
network:0
description: 	Wireless interface
product: 	AR2413 802.11bg NIC
vendor: 	Atheros Communications Inc.
physical id: 	
2
bus info: 	
pci@0000:02:02.0
logical name: 	
wifi0
version: 	01
serial: 	00:14:78:ec:09:8c
width: 	32 bits
clock: 	33MHz
capabilities: 	pm bus_master cap_list logical ethernet physical wireless
configuration:	
broadcast	=	yes
driver	=	ath_pci
ip	=	192.168.11.3
latency	=	168
maxlatency	=	28
mingnt	=	10
module	=	ath_pci
multicast	=	yes
wireless	=	IEEE 802.11g
```

and I have a Buffalo AirStation WCR-G54 as a router. I'm using the alternate atheros "madwifi" driver. I can't connect to the network after a suspend/hibernate. It tries to connect and prompts me for the password again and again but can't connect. The only option is to restart the pc. How do I fix this?

---

### Post by phantasmik on 2009-08-27
could you type ifconfig in the terminal and post the results?

it looks like the name of the adapter is wifi0

next time it is doing this issue try typing 
```
sudo ifconfig wifi0 down
``` 
and then 
```
sudo ifconfig wifi0 up
```
try to connect again let me know what happens when you do this, also for giggles could you paste the contents of /etc/network/interfaces

```
sudo nano /etc/network/interfaces
```

---

### Post by mvalviar on 2009-08-27
```
mvalviar@mumee:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:14:78:ec:09:8c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:48638 errors:0 dropped:0 overruns:0 frame:0
          TX packets:53195 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:28415628 (28.4 MB)  TX bytes:17026291 (17.0 MB)

eth0      Link encap:Ethernet  HWaddr 00:1e:90:f4:20:72  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Base address:0xe800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:265 errors:0 dropped:0 overruns:0 frame:0
          TX packets:265 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:26739 (26.7 KB)  TX bytes:26739 (26.7 KB)

```
```

mvalviar@mumee:~$ sudo ifconfig wifi0 down
mvalviar@mumee:~$ sudo ifconfig wifi0 up
mvalviar@mumee:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

```

---

### Post by Mark Phelps on 2009-08-28
Not trying to discourage you, but this is one of the more difficult problems with using Ubuntu.  I've been using it since 7.04 and have NEVER been able to get a single machine to be able to hibernate or suspend and return from either with networking still operational.  This includes several different desktops and laptops.

Funny thing is, the same machines, using a variety of different MS Windows OSs can suspend/hibernate and restart without losing networking just fine.  So, it's not specifically hardware problems.

If it's a laptop, you might search through the laptop subforum to see if there are any threads on your make and model machine.

This problem is generally tied to video drivers, but there are LOTS of other things that contribute to it as well.

---

### Post by mchecca on 2009-08-28
I had the same problem. Before going into standby, go to the network connections icon and uncheck the enable networking option. Then when you come back, make sure you check it back on. I've been doing this for a few months now with no problems.

---

### Post by mvalviar on 2009-08-28
Thanks for the suggestion. Well the thing is I can suspend/hibernate perfectly before when I was using the free wifi driver. However when using the free driver my system crashes so often. 

So I have 2 choices:

1. Use the proprietary driver and be unable to reconnect after suspend/hibernate.

2 Use the free driver and be able to suspend/hibernate but get crashes every now and then.

I'll try to turn off the wifi before I suspend/hibernate and see if it will work.

---

