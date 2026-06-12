---
title: "anybody know what this means?"
date: 2008-05-18
forum: Networking &amp; Wireless
---

### Post by buccaneere on 2008-05-18
This is the message window:

> Please contact your system administrator to resolve the following problem:

Could not find information on interface 'ath0:avahi' in /proc/net/dev

Thanks...

---

### Post by buccaneere on 2008-05-19
bumpintodatophere...

---

### Post by superprash2003 on 2008-05-19
it could be that ath0 isnt getting an ip address. could you post an ifconfig output

---

### Post by buccaneere on 2008-05-19
Hi prash...

Wireless connectivity SEEMS to be ok, but I'm sure something is awry.

chucknb@chucknb-desktop:~$ ifconfig
[COLOR="Red"]ath0      Link encap:Ethernet  HWaddr 00:14:78:ED:A5:B7  
          inet addr:192.168.0.103  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::214:78ff:feed:a5b7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:884 errors:0 dropped:0 overruns:0 frame:0
          TX packets:367 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:525201 (512.8 KB)  TX bytes:48619 (47.4 KB)[/COLOR]

eth0      Link encap:Ethernet  HWaddr 00:E0:4C:BA:36:9F  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wifi0     Link encap:UNSPEC  HWaddr 00-14-78-ED-A5-B7-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8782 errors:0 dropped:0 overruns:0 frame:39
          TX packets:481 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:1363340 (1.3 MB)  TX bytes:71299 (69.6 KB)
          Interrupt:20 

----------------------------------------------------------------------


Does this file contents tell me anything?

chucknb@chucknb-desktop:~$ cat /proc/net/dev
Inter-|   Receive                                                |  Transmit
 face |bytes    packets errs drop fifo frame compressed multicast|bytes    packets errs drop fifo colls carrier compressed
    lo:       0       0    0    0    0     0          0         0        0       0    0    0    0     0       0          0
  eth0:       0       0    0    0    0     0          0         0        0       0    0    0    0     0       0          0
 wifi0: 1787794   11756    0    0    0    40          0         0    81193     569    0    0    0     0       0          0
  ath0:  665778    1128    0    0    0     0          0         0    53977     425    0    0    0     0       0          0

Thanks...

---

### Post by superprash2003 on 2008-05-19
looks ok.The avahi isnt there in the ifconfig output.Where are you getting this message?

---

### Post by kevdog on 2008-05-19
Id probably do what the message instructs and contact your sys admin :)

---

### Post by buccaneere on 2008-05-20
> **superprash2003 said:**
> looks ok.The avahi isnt there in the ifconfig output.Where are you getting this message?

There's a network applet in my top panel, with the little warning symbol - red circle with white mark.

If I click on the applet, that message comes up.



> Id probably do what the message instructs and contact your sys admin 
I AM the administrator there, KDog. When I contact myself, I get no response.:confused:

---

### Post by compgeek83 on 2008-05-20
> **buccaneere said:**
> There's a network applet in my top panel, with the little warning symbol - red circle with white mark.

If I click on the applet, that message comes up.




I AM the administrator there, KDog. When I contact myself, I get no response.:confused:

but if your network is down, how do you email the admin....  :lolflag:

---

### Post by buccaneere on 2008-05-21
This is the message window:

> Quote:
Please contact your system administrator to resolve the following problem:

Could not find information on interface 'ath0:avahi' in /proc/net/dev
Thanks...

---

