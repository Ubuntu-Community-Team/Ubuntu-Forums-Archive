---
title: "internet through network"
date: 2008-04-09
forum: Networking &amp; Wireless
---

### Post by aiphergott on 2008-04-09
I have set up a temporary network to get the drivers and firmware from the restricted drivers manager. The internet works, thus this message but anything outside of Firefox won't connect. I set it up with automatic dhcp. Can anyone help me?

---

### Post by tamoneya on 2008-04-09
can you post the output of ifconfig

---

### Post by aiphergott on 2008-04-09
this is what i got

eth0      Link encap:Ethernet  HWaddr 00:16: D3:11:96:1E  
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d3ff:fe11:961e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5134 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4921 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4459751 (4.2 MB)  TX bytes:818743 (799.5 KB)
          Interrupt:20 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

---

### Post by tamoneya on 2008-04-09
that seems to be correct to me. What commands have you been running that result in no internet errors.  Post whatever output they spit out.

---

### Post by aiphergott on 2008-04-09
I am not to good with commands but what i have done before is make sure i am connected to the internet through the Ethernet card. Then run  the restricted drivers manager. click enable firmware for broadcom 43xx chipset family. then the computer automatically installs the right stuff.

Maybe I will just have to wait until i can connect directly to a router.

---

