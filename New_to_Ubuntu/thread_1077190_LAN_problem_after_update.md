---
title: "LAN problem after update"
date: 2009-02-22
forum: New to Ubuntu
---

### Post by sagumay on 2009-02-22
my scenario:

installed ubuntu 8.10 on my MSI Wind U100 everything is fine after installation except wireless device. i decided to update my ubuntu through update manager (i am connected via LAN) the update is done i restarted my Wind then suddenly my LAN cannot obtain ip address from the router, i even put a static ip address but still no luck a pop-up message is saying that the network has been disconnected but physically the cable is still there...please i need some help.

Thank you very much in advance...

---

### Post by x33a on 2009-02-22
post the output of 
```
lspci
ifconfig
```

---

### Post by sagumay on 2009-02-23
sagumay@MSIWind:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev ff)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8187SE Wireless LAN Controller (rev 22)
sagumay@MSIWind:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:21:85:4d:68:30  
          inet6 addr: fe80::221:85ff:fe4d:6830/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:369098730 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:221 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:158 errors:0 dropped:0 overruns:0 frame:0
          TX packets:158 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13320 (13.3 KB)  TX bytes:13320 (13.3 KB)

sagumay@MSIWind:~$ 




"here it is, thank you"

---

### Post by x33a on 2009-02-23
are the drivers loaded? which driver were you using previously?

post the output of
```
iwconfig
iwlist scan
```

---

