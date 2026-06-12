---
title: "nForce4 onboard gbit device seen as only a 10mb/s"
date: 2006-09-01
forum: Networking &amp; Wireless
---

### Post by lazzareth on 2006-09-01
I have a problem with my on board gbit card, Asus A8N-SLI

Ubuntu only sees the on board nforce4 gbit card as a 10mb/s not 1000mb/s card

Slight problem I have had for a while, but I am lanning this afternoon, so what better time than never to fix it!

Your help would be much appreciated.

Thank you.



Edit: Would it help if I include 
```

eth0      Link encap:Ethernet  HWaddr 00:13:D4:E3:6C:48
          inet addr:192.168.1.20  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:d4ff:fee3:6c48/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:930349 errors:0 dropped:0 overruns:0 frame:0
          TX packets:792939 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:779734646 (743.6 MiB)  TX bytes:88220680 (84.1 MiB)
          Interrupt:217 Base address:0x2000
```

---

### Post by Uluen on 2006-09-02
What's the output of ```
$ dmesg | grep eth0
```

---

