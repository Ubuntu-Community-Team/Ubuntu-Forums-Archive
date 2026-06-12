---
title: "How do you switch from IPv6 to IPv4?"
date: 2005-10-17
forum: Networking &amp; Wireless
---

### Post by linkunderscore on 2005-10-17
I would really like to know because im getting 820 kb/s when I should be getting 12Mbits on my school network. My router doesn't support IPv6, so I would like to revert to ipv4. 

Thanks.

edit I just realized how stupid  I am. Its a DNS look up issue again. Just like hoary...go figure. Its a shame that ipv4 is the default because ISPs and hardware technology haven't all reached that capability.

---

### Post by bluck on 2005-10-17
[QUOTE=linkunderscore]I would really like to know because im getting 820 kb/s when I should be getting 12Mbits on my school network. My router doesn't support IPv6, so I would like to revert to ipv4. 

Thanks.[/QUOTE]

can you please provide the output from the command `ifconfig -a` ?

---

### Post by linkunderscore on 2005-10-17
```
eth0      Link encap:Ethernet  HWaddr 00:05:5D:32:D4:D0
          inet addr:192.168.1.132  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::205:5dff:fe32:d4d0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2304445 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1927335 errors:0 dropped:0 overruns:0 carrier:0
          collisions:359783 txqueuelen:1000
          RX bytes:1993263084 (1.8 GiB)  TX bytes:571528465 (545.0 MiB)
          Interrupt:19 Base address:0xe800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1323763 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1323763 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:100944630 (96.2 MiB)  TX bytes:100944630 (96.2 MiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

dunno what that means, but i bet you do :)

---

### Post by linkunderscore on 2005-10-20
or not :(

---

### Post by rhinomite on 2005-10-20
Off the top of my head, try this:

edit /etc/modprobe.d/aliases
change the line that reads:
"alias net-pf-10 ipv6"
to
"alias net-pf-10 off"

may need a reboot.
check output of ifconfig after and no IPV6 stats should be present.

---

