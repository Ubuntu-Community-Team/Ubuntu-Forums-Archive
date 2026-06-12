---
title: "network error during startup"
date: 2008-11-02
forum: Networking &amp; Wireless
---

### Post by jav_ on 2008-11-02
hi guys,

i used to have a dlink wireless usb adapter with the ndiswrapper firmware...it worked flawlessly but now i have switched to wired ethernet to get my connection...
the problem is everytime i restart i go through the login screen then it just stalls...i press the power button once and it shows all these messages...somewhere along the lines where NetworkManager: *something* Not Found

it looks like i either need the have the usb adapter plugged in or have both usb adapter and ethernet UNPLUGGED in order to get to my desktop...

does anyone know some sort of fix for this?

thanks

---

### Post by jav_ on 2008-11-03
bump

---

### Post by superprash2003 on 2008-11-03
try removing the usb interface from the /etc/network/interfaces file.. do make a backup of interfaces file.

---

### Post by jav_ on 2008-11-03
hmm...it's empty

---

### Post by superprash2003 on 2008-11-04
thats weird.. you should find some interface info there.. what does ifconfig show..

---

### Post by jav_ on 2008-11-04
ifconfig shows

eth0      Link encap:Ethernet  HWaddr 00:01:02:03:04:05  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:2fff:fe29:802b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5188859 errors:378 dropped:0 overruns:0 frame:754
          TX packets:5336001 errors:141 dropped:0 overruns:141 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4239523928 (3.9 GB)  TX bytes:1949828895 (1.8 GB)
          Interrupt:17 Base address:0x2000

---

