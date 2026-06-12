---
title: "Extreme slow connection how to speed it up"
date: 2007-10-26
forum: Networking &amp; Wireless
---

### Post by Alixul on 2007-10-26
Hello,
I have some problem now with running ubuntu and the problem is that the transfer speed is really slow ~400 KB/sec on 100Full-duplex network. and in windows (on the same computer) I have ~10 MB/sec. (Tested with FTP / samba / nfs)
I have disable IPv6 and after that the computer is a standard 7.10 ubuntu.
Is there someway to speed this up?

---

### Post by anagor on 2007-10-26
what network card do you have?

---

### Post by Alixul on 2007-10-27
> **anagor said:**
> what network card do you have?
The network card is a (DELL) 3com 3CCFE575BT-D, it may also be called just 3CCFE575BT

---

### Post by Alixul on 2007-10-27
up

---

### Post by Alixul on 2007-10-27
fly

---

### Post by Alixul on 2007-10-29
Please help me. ^^

---

### Post by anagor on 2007-10-29
is this  pcmcia card?
if so you should find info regarding the pcmcia itself, the speed of the network in this case will depend on the config of pcmcia bus (1bit/32bit for example), also google shows quite a range of posts regarding your card, maybe one of them will have a solution?
sorry I don't have much time nor any expirience with pcmcia to help you, maybe someone else will be able to help you.

---

### Post by Lambert on 2007-10-29
> **Alixul said:**
> Please help me. ^^

Post the output of

```

sudo iwconfig

```

Also as a suggestion change the file /etc/hosts.

Change the line so it looks like this.

127.0.0.1 localhost.localdomain localhost ____

Fill in the blank with the hostname of your computer.

---

### Post by Alixul on 2007-10-31
> **anagor said:**
> is this  pcmcia card?
if so you should find info regarding the pcmcia itself, the speed of the network in this case will depend on the config of pcmcia bus (1bit/32bit for example), also google shows quite a range of posts regarding your card, maybe one of them will have a solution?
sorry I don't have much time nor any expirience with pcmcia to help you, maybe someone else will be able to help you.

Yes, it's a PCMCIA card, I search google and haven't find anything that helped. =(

> **Lambert said:**
> Post the output of

```

sudo iwconfig

```

Also as a suggestion change the file /etc/hosts.

Change the line so it looks like this.

127.0.0.1 localhost.localdomain localhost ____

Fill in the blank with the hostname of your computer.

The /etc/hosts file is configure right after what u told.
The iwconfig gives this output: 
```
lo        no wireless extensions.
eth0      no wireless extensions.
```
But that's becouse the card is not a wireless card. ;)
So here is the ifconfig output:
```
eth0      Link encap:Ethernet  HWaddr XX:XX:XX:XX:XX
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4124 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2164 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:579478 (565.8 KB)  TX bytes:267506 (261.2 KB)
          Interrupt:11 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:55 errors:0 dropped:0 overruns:0 frame:0
          TX packets:55 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5372 (5.2 KB)  TX bytes:5372 (5.2 KB)
```

---

### Post by charles woodward on 2007-10-31
There is another thread on this topic (extremely slow wireless...) - 

Basically there is a bug (it has been reported and confirmed) that is causing internet/network connections to slow down.  In my own case I have watched the speeds drop from normal to 1 bit per second in a matter of moments, and sometimes I have difficulty getting connected at all.

As I've said on the other thread, I hope they get the bug fixed soon.

---

### Post by Alixul on 2007-10-31
> **charles woodward said:**
> There is another thread on this topic (extremely slow wireless...) - 

Basically there is a bug (it has been reported and confirmed) that is causing internet/network connections to slow down.  In my own case I have watched the speeds drop from normal to 1 bit per second in a matter of moments, and sometimes I have difficulty getting connected at all.

As I've said on the other thread, I hope they get the bug fixed soon.

The thing is that this card is NOT a wireless card it's a wired 100MBit  card. ;D

---

