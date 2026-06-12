---
title: "wireless was working now not"
date: 2005-05-23
forum: Networking &amp; Wireless
---

### Post by sanman_nor on 2005-05-23
my wireless was working but now its not I went into network tools and the hardweare address is not avalible how do I find that and fix it 
I do not know if this is related but since I upgreaded to hoary hedgehogg my comp has been getting slower and slower

---

### Post by Ali_Baba on 2005-05-23
Try ifconfig on terminal.That should give information about your connection.See how it look and paste it to this thread,then whe have better changes to help :)

---

### Post by sanman_nor on 2005-05-23
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:02:3F:92:97:56
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::202:3fff:fe92:9756/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1762 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1794 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1099236 (1.0 MiB)  TX bytes:323956 (316.3 KiB)
          Interrupt:17 Base address:0x3000

eth1      Link encap:Ethernet  HWaddr 00:02:2D:B3:50:E3
          inet6 addr: fe80::202:2dff:feb3:50e3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:74 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 Base address:0x100

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16581 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16581 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1512425 (1.4 MiB)  TX bytes:1512425 (1.4 MiB)

---

### Post by Ali_Baba on 2005-05-25
I think you should look at these HOWTOs, there is some wireless cards too. 
[http://www.ubuntuforums.org/showthread.php?t=31094](http://www.ubuntuforums.org/showthread.php?t=31094) :)

---

