---
title: "Tcpdump didn't set promiscuous mode by default"
date: 2014-02-07
forum: Networking &amp; Wireless
---

### Post by vincent-hsu on 2014-02-07
[FONT=arial]The tcpdump manual says it will put the interface into promiscuous mode by default.  It isn't work on my Ubuntu 12.04 but[/FONT] it work on my Mac[FONT=arial]. [/FONT][FONT=arial]Alought[/FONT][FONT=arial] I can set it with ifconfig.[/FONT] I want to figure what ubuntu do? [FONT=arial]Anyone have idea about it?[/FONT]
[FONT=arial]
[/FONT]

---

### Post by Doug S on 2014-02-07
Hi and welcome to Ubuntu forums.

How do you know tcpdump is not putting your NIC into promiscuous mode? It might not be obvious from command level stuff. See [this]("http://www.tcpdump.org/faq.html#q7").
I know mine went into promiscuous mode when using tcpdump from the kern.log entries:```
doug@doug-64:~/temp3$ grep promisc kern*
kern.log.2:Jan 23 16:33:39 doug-64 kernel: [1357003.956687] device eth0 left promiscuous mode
kern.log.2:Jan 23 16:33:46 doug-64 kernel: [1357011.606082] device eth1 left promiscuous mode
kern.log.2:Jan 23 16:38:22 doug-64 kernel: [   45.788228] device eth1 entered promiscuous mode
kern.log.2:Jan 23 16:38:46 doug-64 kernel: [   70.048052] device eth0 entered promiscuous mode
kern.log.3:Jan 12 09:53:50 doug-64 kernel: [382615.197803] device eth0 left promiscuous mode
kern.log.3:Jan 12 09:54:03 doug-64 kernel: [382627.860080] device eth0 entered promiscuous mode
kern.log.3:Jan 12 09:54:06 doug-64 kernel: [382631.221819] device eth1 left promiscuous mode
kern.log.3:Jan 12 09:54:18 doug-64 kernel: [382643.460051] device eth1 entered promiscuous mode
kern.log.4:Jan  7 23:35:22 doug-64 kernel: [829372.401259] device eth0 left promiscuous mode
kern.log.4:Jan  7 23:35:27 doug-64 kernel: [829377.662658] device eth1 left promiscuous mode
kern.log.4:Jan  7 23:38:11 doug-64 kernel: [   76.608052] device eth1 entered promiscuous mode
kern.log.4:Jan  7 23:38:44 doug-64 kernel: [  109.376047] device eth0 entered promiscuous mode
```(the files were originally in /var/log , but I copied them so I could unzip the older ones.)

---

### Post by vincent-hsu on 2014-02-09
Okay, I know what happens now. The NIC indeed entered promiscuous mode. I could see it in kernel message. Ubuntu won't show it through ifconfig or ip addr. But it will while I directly set it by "ifconfig eth0 promisc" command as below.
```
eth0      Link encap:Ethernet  HWaddr 50:6a:6d:1c:12:dd          inet addr:172.16.34.101  Bcast:172.16.34.255  Mask:255.255.255.128
          inet6 addr: fe80::5246:5dff:fe8c:11dd/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:3034741 errors:0 dropped:102131 overruns:0 frame:0
          TX packets:22928 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:457033723 (457.0 MB)  TX bytes:2458093 (2.4 MB)
          Interrupt:50 Base address:0xc000
```
You solve my question, thank you.

---

