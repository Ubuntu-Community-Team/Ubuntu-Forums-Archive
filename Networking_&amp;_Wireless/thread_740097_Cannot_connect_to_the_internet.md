---
title: "Cannot connect to the internet"
date: 2008-03-30
forum: Networking &amp; Wireless
---

### Post by netscorpion on 2008-03-30
Hello guys,

I could really use some help. I am unable to connect to the internet, but am able to ping the router without any problems. I just installed kubuntu on my computer. I am absolutely new to linux and could really use some help in trying to fix this. Any suggestion or help is much appreciated. Since i'm new, i would appreciate if you made everything very simple and tell me exactly what to do else i might not be able to do it.

Thanks a lot

Netscorpion

---

### Post by netscorpion on 2008-03-30
I just thought i'd go ahead and add ifconfig output as that is the first thing everyone asks to do

eth0      Link encap:Ethernet  HWaddr 00:04:4B:03:79:98
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::204:4bff:fe03:7998/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:144 errors:0 dropped:0 overruns:0 frame:0
          TX packets:62 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:16347 (15.9 KiB)  TX bytes:6388 (6.2 KiB)
          Interrupt:5 Base address:0xc000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:95 errors:0 dropped:0 overruns:0 frame:0
          TX packets:95 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:6820 (6.6 KiB)  TX bytes:6820 (6.6 KiB)

---

### Post by prshah on 2008-03-30
> **netscorpion said:**
> I just thought i'd go ahead and add ifconfig output as that is the first thing everyone asks to do


Also please add output of ```
cat /etc/resolv.conf
```

---

