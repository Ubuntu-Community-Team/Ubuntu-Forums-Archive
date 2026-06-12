---
title: "Starting BASIC networking… failed
Configuring networking interfaces… failed"
date: 2006-10-12
forum: Networking &amp; Wireless
---

### Post by digitalkarabao on 2006-10-12
Weird. Everything worked for two months and then i started getting this at bootup...

Starting BASIC networking… failed
Configuring networking interfaces… failed

I also observed that I do not receive data when i tunnel my Internet connection and with SSH proxies as well.

Help!

---

### Post by theblackgecko on 2007-03-13
I too get the messages when Ubuntu is starting. However, my wireless internet is working fine. I'm confused!

---

### Post by Mr. C. on 2007-03-13
Show output from a Terminal window from:

```
ifconfig -a
```

MrC

---

### Post by theblackgecko on 2007-03-15
```
ath0      Link encap:Ethernet  HWaddr 00:11:50:71:6E:99
          inet addr:10.0.0.141  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::211:50ff:fe71:6e99/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:134203 errors:45879 dropped:0 overruns:0 frame:45879
          TX packets:96278 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200
          RX bytes:184088769 (175.5 MiB)  TX bytes:8991474 (8.5 MiB)
          Interrupt:169 Memory:d0360000-d0370000

eth1      Link encap:Ethernet  HWaddr 00:14:A4:4E:86:B0
          inet6 addr: fe80::214:a4ff:fe4e:86b0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1194 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:159445 (155.7 KiB)  TX bytes:936 (936.0 b)
          Interrupt:193 Memory:dfdfe000-dfe00000

eth2      Link encap:Ethernet  HWaddr 00:12:3F:04:04:EF
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback
          LOOPBACK  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


```
ath0 is the Atheros wireless card which works just fine. eth2 is the Ethernet port, which is not connected to anything. eth1 is the built in Broadcom Wireless card, which has never worked properly.

---

### Post by Mr. C. on 2007-03-15
Ok, good.  We need to see what type of hardware eth2 is, and what the system has to say about it:

```
lspci
lshw -class network
```

and search dmesg for references to eth2 and a dozen or so lines before and after those references.  Are the entire output:
```

dmesg > dmesg.out
gzip dmesg.out

```
and attach dmesg.out.gz

MrC

---

