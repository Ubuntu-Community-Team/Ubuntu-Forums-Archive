---
title: "Help to install Zyxel ADSL USB modem"
date: 2008-05-24
forum: Networking &amp; Wireless
---

### Post by Antorix on 2008-05-24
Can anybody help to install a Zyxel ADSL USB modem (OMNI, AS6EE, possibly Connexant chipset) on a Ubuntu 8.04 at 64 bit Athlon system? The online documentation is wortheless since it requires an Internet connection, which I cannot setup. (I'm now via Windows Vista).

---

### Post by superprash2003 on 2008-05-25
cant you connect using the LAN port?

---

### Post by Antorix on 2008-05-25
No, I don't have them, just USB.

---

### Post by superprash2003 on 2008-05-25
please post an output of ifconfig

---

### Post by Antorix on 2008-05-25
I don't know what ipconfig is. I don't know what to do at all, I just tried Ubuntu in the live CD mode, saw that my modem doesn't work, referred to the online documentation, it is of no help - and that's all. What should I do? I'm not a hardcore Linux user, I'm unaware of many terms and actions, though I know how to launch terminal :) Can you help?

---

### Post by superprash2003 on 2008-05-25
go to the terminal and type ifconfig .. you will get an output.. highlight the output and right click and click on copy.. come to the forums page and paste it here.. since you dont have internet access there.. save it to a text file and again paste it here

---

### Post by Antorix on 2008-05-26
I was mistaken: I do have Ethernet port, but never used it, since my modem is a USB modem. However, here is the output:

eth0      Link encap:Ethernet  HWaddr 00:15:58:4a:8f:31  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:11964 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11964 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:600184 (586.1 KB)  TX bytes:600184 (586.1 KB)

---

### Post by superprash2003 on 2008-05-26
most routers come with LAN ports.its better you connect via LAN.. you dont have to worry about drivers and stuff.. and is this the ifconfig output when your usb modem is connected via USB?

---

### Post by Antorix on 2008-05-27
How is it possible to connect via LAN using a USB modem? What are you talking about? Yes, it is the output with the modem connected, but the system apparently doesn't see it.

---

### Post by superprash2003 on 2008-05-27
try these drivers [http://sourceforge.net/services/project_services.php?project_id=84006](http://sourceforge.net/services/project_services.php?project_id=84006)

---

### Post by Antorix on 2008-05-27
Ok, I downloaded it, what next?

---

