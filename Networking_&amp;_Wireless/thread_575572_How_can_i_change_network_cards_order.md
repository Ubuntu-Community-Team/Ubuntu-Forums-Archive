---
title: "How can i change network cards order?"
date: 2007-10-14
forum: Networking &amp; Wireless
---

### Post by elnur on 2007-10-14
I got two network cards and want one of them be eth0 and work with internet and the second one, which is eth1 to be used as connector to my laptop.

The problem is that their order is reverse:
Internet card is given name eth1 and eth0 (which is used by default) is connected to laptop. So I got to select another card every time I boot the system. 
And every internet connection takes 5-10 seconds to start, but then works fast, cuz I got fast internet. I think this is caused by firstly trying to connect by eth0 and only then, after fail, it uses eth1


Ifconfig:
```

eth0      Link encap:Ethernet  HWaddr ***
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0xc000 

eth1      Link encap:Ethernet  HWaddr ***
          inet addr:***  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: *** Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16020 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11234 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:20116425 (19.1 MB)  TX bytes:1159797 (1.1 MB)
          Interrupt:19 Base address:0xac00 


```

---

### Post by milosz.galazka on 2007-10-14
Look at cat */etc/udev/rules.d/70-persistent-net.rules* file :)

If you edit it then remember to *chmod +x /etc/udev/rules.d/70-persistent-net.rules* and
*/etc/init.d/udev restart* or reboot....

---

### Post by kevdog on 2007-10-14
Look at the /etc/iftab file -- this is the easiest way to do it.  It has the interface name associated with the MAC address.

---

### Post by ruibernardo on 2007-10-14
Yes, /etc/iftab was fine until Feisty, but it doesn't exist anymore on Gutsy. I agree  with Milosz suggestion. It is the correct one for Gutsy.

---

