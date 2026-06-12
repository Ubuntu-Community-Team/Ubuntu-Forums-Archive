---
title: "my LAN CARD suddenly stopeed working"
date: 2013-12-27
forum: Networking &amp; Wireless
---

### Post by amith_m on 2013-12-27
hi everyone,


     My LAN CARD suddenly stopped working, it is not at all responding, it is not even getting the ip adress ,can anyone help me to resolve this....please..

---

### Post by hmag on 2013-12-27
Hello

Same for me, this is probably due to a recent upgrade of the Ubuntu kernel.
No hardware issue for me, I checked by booting on a live installation CD, ... then the LAN is recognized.

In 'ifconfig', only 'lo' and 'wlan0' interfaces are present, no 'eth0' or 'eth1' :

```

root@asus2:/etc/init.d# ifconfig
lo        Link encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:309 erreurs:0 :0 overruns:0 frame:0
          TX packets:309 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:27423 (27.4 KB) Octets transmis:27423 (27.4 KB)

wlan0     Link encap:Ethernet  HWaddr dc:85:de:6d:f0:32  
          inet adr:192.168.2.6  Bcast:192.168.2.255  Masque:255.255.255.0
          adr inet6: fe80::de85:deff:fe6d:f032/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:1959 erreurs:0 :0 overruns:0 frame:0
          TX packets:1788 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:1957418 (1.9 MB) Octets transmis:357642 (357.6 KB)
```

A few informations on my hardware are provided below (lspci) as well as the **dmesg **as attachment... sorry, couldnot, upload dialog box puts an orange exclamation icon and does not explain what it means ;-(  - will see that later )

Regards
HMag

```
root@asus2:/etc/init.d# lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1c.3 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 4 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM76 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
02:00.0 Network controller: Qualcomm Atheros AR9485 Wireless Network Adapter (rev 01)
03:00.0 Ethernet controller: Qualcomm Atheros AR8161 Gigabit Ethernet (rev 10)
root@asus2:/etc/init.d# 

```

---

