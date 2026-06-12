---
title: "Network"
date: 2008-03-18
forum: Networking &amp; Wireless
---

### Post by dhoni on 2008-03-18
Hi all,
I thought I would try out Ubuntu and so far I have been impressed, but I cannot get my internet working, I have a Realtek RTL8139/810x Family fast ethernet NIC #2 card, I have managed to get the drivers and install them (with help from a friend), but it still cant find the card. i have tried the ifconfig eth0 up, but it says error. Am I missing something or is there a command to get the card working?
Thanks in advance.

---

### Post by superprash2003 on 2008-03-18
please post results of ifconfig

---

### Post by dhoni on 2008-03-18
ifconfig

Lo	Link encap:Local Loopback
	 Inet addr: 127.0.0.1    Mask: 255.0.0.0
	 UP LOOPBACK RUNNING MTU: 16436 Metric: 1
	 RX packets:0 errors:0 dropped:0 overruns:0 frame:0
	 TX packets: 0 errors: 0 dropped: 0 overruns: 0 carrier: 0
	 Collisions: 0 txqueuelen: 0
	 RX bytes: 0 (0.0 b)	TX bytes: 0 (0.0 b)

---

### Post by dhoni on 2008-03-18
anyone?

---

### Post by Ardrias on 2008-03-18
Well... are you using Networkmanager? If you are, at least in my experience you'll not have a lot of luck trying to do stuff manually. 

However, if you do try, you need to become root to bring up/down interfaces. 
```
sudo ifconfig eth0 up
``` if the card is indeed seen as eth0.

---

### Post by dhoni on 2008-03-18
thanks for the reply.
I typed that command in and it says ERROR while getting interface flags: No such device. When i go to network settings it's only got 1 type, which is modem connection.

---

### Post by Ardrias on 2008-03-18
You can type ```
cat /var/log/dmesg |grep -i eth
``` and see if you can spot something. On my PC I get something like 
```
[    2.704000] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.60.
[    5.868000] forcedeth: using HIGHDMA
[    6.388000] eth0: forcedeth.c: subsystem: 01043:cb84 bound to 0000:00:10.0
```

For you, perhaps it sets whatever card you have as eth1.

---

### Post by dhoni on 2008-03-18
I typed in car /var/log/dmesg and i found the following to do with the network card.
8139cp: 10/100 PCE Ethernet driver v1.3 (Mar 22, 2004)
8139cp 0000:00:08.0: This (id 10ec:8139 rev 10) is not an 8139c+ compatible chip
8139cp 0000:00:08.0: Try the "8139too" driver instead.

Is this saying I have installed the wrong drivers?

---

### Post by Ardrias on 2008-03-18
It would seem like it. Fixing it is however out of my league :|

---

### Post by dhoni on 2008-03-18
Thanks for your help anyway, btw how do you uninstall the drivers? I tried ndiswrapper -r netrtlx.inf and it is saying that it can’t find the file or where the directory is, thank for your help.

---

