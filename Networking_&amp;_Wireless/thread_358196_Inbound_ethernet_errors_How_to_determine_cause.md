---
title: "Inbound ethernet errors: How to determine cause?"
date: 2007-02-10
forum: Networking &amp; Wireless
---

### Post by kebes on 2007-02-10
First off, this is a problem occuring on a Mandrake 10.1 box, not my Ubuntu machine. Hope no one minds if I post a couple questions anyway!


Basically the network connection on the Mandrake box has gotten worse over the last little while. Outbound data from the machine is very fast (>100 kB/s) but inbound data is always painfully slow. Basically any inbound connection I attempt runs at about 0-10 kB/s, and constantly times out and has to reconnect. (So that the average transfer rate is 0.1 kB/s.)

This problem occurs whether I try to download a file on the Mandrake box, or whether I try and upload a file to that box from another computer. You can also see the problem in ifconfig:
```

# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:AA:B2:CC:2E:07
          inet addr:192.168.15.100  Bcast:192.168.15.255  Mask:255.255.255.0
          inet6 addr: fe80::2a0:ccff:fee1:a8c7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:950405 [COLOR="Red"]errors:33350[/COLOR] dropped:0 overruns:0 frame:38020
          TX packets:1017591 errors:66 dropped:0 overruns:0 carrier:29
          collisions:0 txqueuelen:1000
          RX bytes:145442604 (138.7 Mb)  TX bytes:158893137 (151.5 Mb)
          Interrupt:9 Base address:0xb000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:92301 errors:0 dropped:0 overruns:0 frame:0
          TX packets:92301 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:74934286 (71.4 Mb)  TX bytes:74934286 (71.4 Mb)

```

As you can see, there are tons of errors with regard to received packets. Note that if I transfer a file within the machine (ftp localhost, for instance) it is fast and without problem.



I'm not sure whether the problem is software or hardware. It may be that the ethernet card is dying (in which case I'll replace it), but I suppose it could also be that network settings have been messed up (although I have not changed anything recently).


My questions are:
Does anyone know how to detect if your ethernet card is bad?
Does anyone know how to differentiate between a software or hardware leading to the timeouts?
Does anyone know how to determine what exactly those errors that ifconfig reports are? Maybe if I knew the nature of the error I could try to fix it?

Any help (even random things to try) is much appreciated!

---

