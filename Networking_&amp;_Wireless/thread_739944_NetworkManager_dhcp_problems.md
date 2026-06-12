---
title: "NetworkManager dhcp problems"
date: 2008-03-30
forum: Networking &amp; Wireless
---

### Post by schmolch on 2008-03-30
I have 3 Computers connected to my Router (the blue linksys many people have) - all running (X)Ubuntu 7.10 and on one of them NetworkManager is not able to get a IP adress via dhcp.
It tries and tries but nothing happens.
I can assign a ip manually, i even can run "dhclient eth1" myself and it works, but it doesn't with NetworkManager.

Is there any logfile where i can look for clues what the problem is?

---

### Post by superprash2003 on 2008-03-30
did you set it to automatic configuration(DHCP) in system->administration->network

---

### Post by schmolch on 2008-03-30
yes i did.

I can set it to manual configuration and set a static ip, but the dhcp does not work at all.

---

### Post by Iowan on 2008-03-30
With the machine set for DHCP and networking restarted, what are the results of **ifconfig** and the contents of **/etc/network/interfaces**?

---

### Post by schmolch on 2008-03-30
Ok so i switched it back from static ip to dhcp and rebooted.

ifconfig says:```

eth1      Protokoll:Ethernet  Hardware Adresse 00:40:B9:1D:CF:00  
          inet6 Adresse: fe80::240:b9ff:fe1d:cf00/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:109 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:7070 (6.9 KB)  TX bytes:810 (810.0 b)
          Interrupt:10 Basisadresse:0x8000 

```
and /etc/network/interfaces:```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth1
iface eth1 inet dhcp
address 192.168.1.107
netmask 255.255.255.0
gateway 192.168.1.1
```

"iface eth1 inet dhcp" was initially commented out which i changed, but thats obviously not the cause of the failure and on my other machine its commented out as well and does work.

---

