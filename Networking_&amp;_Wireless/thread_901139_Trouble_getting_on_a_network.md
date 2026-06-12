---
title: "Trouble getting on a network"
date: 2008-08-26
forum: Networking &amp; Wireless
---

### Post by michael.693 on 2008-08-26
Hello, i recently installed ubuntu with help from you guys but im just wondering how to get it on the internet, i have a router. a d-link dir-300 and i do not know how to get ubuntu 8.04 onto the internet. 

Please help




Michael.

---

### Post by jigsaws on 2008-08-26
The easiest way is configure d-link for sharing connection with dhcp server. By default Ubuntu should connect to the dhcp server and get IP address (plus some parameters like default gateway) and it should works out of the box.

---

### Post by ilrudie on 2008-08-26
I agree.  Also its probably already setup for DHCP by default.  Did you try just plugging it in and seeing if the connection comes up?

---

### Post by michael.693 on 2008-08-27
> **ilrudie said:**
> I agree.  Also its probably already setup for DHCP by default.  Did you try just plugging it in and seeing if the connection comes up?

Yes  i did and nothing came up.

---

### Post by tim356 on 2008-08-27
can you run the following command from the terminal and paste the output here:
```
ifconfig
```

---

### Post by michael.693 on 2008-08-27
Ok ill do that and see what it says.

---

### Post by michael.693 on 2008-08-27
Ok i ran it and this is what it says -

lo     link encap:local loopback
       inet addr:127.0.0.1  Mask:255.0.0.0
       inet6 addr: ::1/128 Scope:host
       UP LOOPBACK RUNNING MTU:16436 Metric:1
       RX packets:508 errors:0 dropped:0 Overruns:0 fram:0
       TX packets:508 errors:0 dropped:0 overruns:0 carrier:0
       collisions:0 txqueuelen:0
       RX bytes:25400 (24.8 KB) TX bytes:254.00 (24.8 KB)

 
It was supposed to have the cable in it, right?

---

### Post by jigsaws on 2008-08-27
The problem is that you system has no network card. If it's onboard device check if it is enabled in BIOS.

Then see in network manager (system/administration/networking) if any interfaces can be configured.

---

### Post by michael.693 on 2008-08-27
no network card?




what would it be called in the bios?

---

### Post by michael.693 on 2008-08-27
ALso jsut to add another point with the connection on the top panel it says connecion: lo

---

### Post by michael.693 on 2008-08-27
and when i go into it it says name: lo
Status: idle

Activity
Recieved: 502 packets (24.5 Kb)
Sent:     502 packets (24.5 kb)

---

### Post by jigsaws on 2008-08-27
lo is loopback interface, it's a kind of local, virtual network card. But we need eth0 to connect the net.

Ok, first check your Network manager, then we will think about bios (but it can be called something like OnBoard LAN Adapter or something).

---

### Post by michael.693 on 2008-08-27
oh ok. so what do u want me to do?

---

### Post by jigsaws on 2008-08-27
Run the system/administraction/networking and check if you can configure any "wire connection".

---

### Post by michael.693 on 2008-08-27
Its got a picture of a phone? 
and then unlock when i click on it.

---

### Post by michael.693 on 2008-08-27
Its called point to point connection, underneath it says this network interface is not connected

---

