---
title: "Cannot Conect to Router with Firefox."
date: 2007-02-09
forum: Networking &amp; Wireless
---

### Post by Becan186 on 2007-02-09
Hello Everone,
Yes I am another newbee to Linux and Ubuntu 6.06, also Forums for that matter.

I cannot connect to the internet or my router using firefox by typing "http://192.168.1.254" for router or say "http://www.google.com", now I am searching for some help and guidance to get a connection.

I have a devoted HDD with an install of Ubuntu 6.06. This is in a removable HDD tray, I also have a 2nd HDD also in a tray with XP on it, when XP HDD is in the PC it will freely connect to my Router and internet, Therefore shall we presume no hardware problems.

System:
Gigabyte GA-K8N Pro-Sli, with nForce4 Chipset.
Amd 64x2 Dual core processor
Billion ADSL Router BIPAC-7402

Can anybody help me with the next step of action to setup a connection. Also ho can i ping in Ubuntu?

Thanks in advance
Ben

---

### Post by cookie200 on 2007-02-09
what does ifconfig say?

---

### Post by Becan186 on 2007-02-09
ifconfig says:

eth0      Link encap:Ethernet  HWaddr 00:14:85:EF:D1:84
          inet6 addr: fe80::214:85ff:feef:d184/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:3888 (3.7 KiB)
          Interrupt:217 Base address:0xe000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:21 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1456 (1.4 KiB)  TX bytes:1456 (1.4 KiB)


Also ping 192.168.1.254
Says
Network is unreachable

---

