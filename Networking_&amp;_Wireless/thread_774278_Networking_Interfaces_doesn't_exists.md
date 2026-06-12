---
title: "Networking Interfaces doesn't exists"
date: 2008-04-29
forum: Networking &amp; Wireless
---

### Post by Khalis7 on 2008-04-29
Hi. I'm using Hardy and recently I attempted to configure both my intel 3945abg wireless and Broadcom LAN device through network tools but it kept saying the interfaces doesn't exist. This is the output of my ifconfig:

```
khalis7@khalis7:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:18:8b:af:79:f9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:669 errors:0 dropped:0 overruns:0 frame:0
          TX packets:669 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:80163 (78.2 KB)  TX bytes:80163 (78.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1b:77:49:bb:aa  
          inet addr:10.83.76.245  Bcast:10.83.76.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:373756 errors:0 dropped:0 overruns:0 frame:0
          TX packets:376598 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:237352271 (226.3 MB)  TX bytes:103971351 (99.1 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1B-77-49-BB-AA-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

If anyone could point me to another thread with similar problem that would be nice to me.

---

### Post by superprash2003 on 2008-04-29
wlan0 seems to be fine.. you arent gettin an ip in eth0... have you tried rebooting?

---

### Post by Khalis7 on 2008-04-29
> **superprash2003 said:**
> wlan0 seems to be fine.. you arent gettin an ip in eth0... have you tried rebooting?

I've rebooted my PC for many times but it still saying the wireless and LAN interfaces doesn't exist. It's kind of peculiar when this happening in Hardy whereas in Gutsy, I had never encountered such problem.:confused:

---

### Post by Khalis7 on 2008-05-02
Hi.. With regards to my networking interfaces problem, I still couldn't solve it and I don't have any idea in solving it. Is there anyone could suggest to me what I can do to solve my problem once and for all???

---

