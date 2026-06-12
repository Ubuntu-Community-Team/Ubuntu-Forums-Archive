---
title: "USB0 &amp; IPv6"
date: 2004-11-25
forum: Networking &amp; Wireless
---

### Post by Allen S on 2004-11-25
I am trying to communicate with my Zaurus SL-6000 over usb. I can get it to connect and disconnect when I turn the Z on and off but iwconfig shows the usb0 interface as being IPv6 so I can't communicate with it.

usb0      Link encap:Ethernet  HWaddr 56:27:C7:C4:11:EC
          inet6 addr: fe80::5427:c7ff:fec4:11ec/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1002 (1002.0 b)  TX bytes:398 (398.0 b)

How can I get this to useIP4?

I have already uncommented the line in modules.conf (?) to turn it off, did modules-update and even rebooted.

Thanks
Allen

---

