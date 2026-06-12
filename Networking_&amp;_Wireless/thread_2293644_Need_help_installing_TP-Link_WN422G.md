---
title: "Need help installing TP-Link WN422G"
date: 2015-09-06
forum: Networking &amp; Wireless
---

### Post by reviaj on 2015-09-06
I've been looking around but I can make this work, I'm new to Ubuntu or Linux in general so detailed instructions would be very much appreciated

---

### Post by reviaj on 2015-09-06
I found this -  [https://wireless.wiki.kernel.org/en/users/Drivers/ath9k_htc](https://wireless.wiki.kernel.org/en/users/Drivers/ath9k_htc)  but I really don't know how to proceed

---

### Post by Bucky Ball on 2015-09-06
*Thread moved to **Networking and Wireless**.*
> **reviaj said:**
> I found this -  [https://wireless.wiki.kernel.org/en/users/Drivers/ath9k_htc](https://wireless.wiki.kernel.org/en/users/Drivers/ath9k_htc)  but I really don't know how to proceed

Welcome. In that case don't proceed. You may not even need it. What leads you to believe you do? :)

Please open a terminal and, to start with, post he output of this command. You won't see your password when you type it in. That is normal.

```
sudo lshw -C network
```

PS: Check the third link in my signature. The more info you can give the better your chances of support. :)

---

### Post by reviaj on 2015-09-06
*-network DESACTIVADO   
       descripción: Interfaz inalámbrica
       producto: PRO/Wireless 3945ABG [Golan] Network Connection
       fabricante: Intel Corporation
       id físico: 0
       información del bus: pci@0000:0c:00.0
       nombre lógico: wlan0
       versión: 02
       serie: 00:19:d2:92:40:b9
       anchura: 32 bits
       reloj: 33MHz
       capacidades: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuración: broadcast=yes driver=iwl3945 driverversion=3.19.0-25-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11abg
       recursos: irq:27 memoria:efdff000-efdfffff
  *-network
       descripción: Ethernet interface
       producto: BCM4401-B0 100Base-TX
       fabricante: Broadcom Corporation
       id físico: 0
       información del bus: pci@0000:03:00.0
       nombre lógico: eth0
       versión: 02
       serie: 00:18:8b:bb:d5:40
       tamaño: 100Mbit/s
       capacidad: 100Mbit/s
       anchura: 32 bits
       reloj: 33MHz
       capacidades: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuración: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.71 latency=64 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       recursos: irq:17 memoria:ef9fe000-ef9fffff
  *-network DESACTIVADO
       descripción: Interfaz inalámbrica
       id físico: 2
       información del bus: usb@1:7
       nombre lógico: wlan1
       serie: b0:48:7a:95:e8:b8
       capacidades: ethernet physical wireless
       configuración: broadcast=yes driver=ath9k_htc driverversion=3.19.0-25-generic firmware=1.3 link=no multicast=yes wireless=IEEE 802.11bgn

---

### Post by Bucky Ball on 2015-09-06
Try:

```
sudo apt-get install --reinstall linux-firmware
```

From [here]("http://ubuntuforums.org/showthread.php?t=2222374").

Post any errors or tell us if that worked (please see the last link in my signature and use code tags for terminal output, thanks ;))

---

### Post by reviaj on 2015-09-06
```

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.

```

---

### Post by reviaj on 2015-09-06
I changed to Xubuntu because Unity was running really slow on my pc and I ran the command again
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0 B/24.3 MB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 206067 files and directories currently installed.)
Preparing to unpack .../linux-firmware_1.127.15_all.deb ...
Unpacking linux-firmware (1.127.15) over (1.127.15) ...
Setting up linux-firmware (1.127.15) ...

```

But the wireless usb isn't working yet

---

### Post by Bucky Ball on 2015-09-07
You have marked this thread as solved. Is it? If so, how did you fix your issue? Please share with the community. Thanks.

---

