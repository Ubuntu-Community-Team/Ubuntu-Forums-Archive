---
title: "Network gone kaput!"
date: 2007-12-30
forum: Networking &amp; Wireless
---

### Post by nipun_jain on 2007-12-30
Okay, so here's the deal. Have been using Ubuntu since Dapper Drake, used to upgrade to newer releases when they became available. Recently upgraded to Gutsy, everything worked perfectly and then my network (Acer Aspire 5002 laptop with SiS900 PCI Fast Ethernet connected to Beetle 220 BX ADSL modem) via ethernet stopped working. When I pinged the modem, it said Network is Unreachable. Thinking I might have uninstalled some networking package (I removed some useless stuff using synaptic), I reinstalled ubuntu gutsy and everything worked fine.

I connected to the internet, left it on for an hour or so, returned back to see the connection dropped. Could not reconnect (pppoe connection using pon). Again ping to my modem failed (network is unreachable). I didn't make any changes to the system (install any hardware or software), the network just stopped working like that. It still works perfectly in windows XP.



So **in short,** on my **Gutsy** system with **SiS900 PCI Fast Ethernet** ethernet card, **networking interface eth0 stopped working abruptly**. Tried disabling IPv6 to no avail.

Some info you might need. Also have attached some screenshots that you might find helpful in helping me :)

```
root@nipun-laptop:/home/nipun# ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:C0:9F:CA:DA:2B  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1274 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:76440 (74.6 KB)  TX bytes:0 (0.0 b)
          Interrupt:16 Base address:0x1800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:772 (772.0 b)  TX bytes:772 (772.0 b)

```

```
root@nipun-laptop:/home/nipun# cat /etc/network/interfaces
auto lo
iface lo inet loopback


iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

auto eth0
iface eth0 inet manual

```

```
root@nipun-laptop:/home/nipun# lspci -nn
00:00.0 Host bridge [0600]: Silicon Integrated Systems [SiS] 760/M760 Host [1039:0760] (rev 03)
00:01.0 PCI bridge [0604]: Silicon Integrated Systems [SiS] SG86C202 [1039:0002]
00:02.0 ISA bridge [0601]: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] [1039:0963] (rev 25)
00:02.1 SMBus [0c05]: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller [1039:0016]
00:02.5 IDE interface [0101]: Silicon Integrated Systems [SiS] 5513 [IDE] [1039:5513]
00:02.6 Modem [0703]: Silicon Integrated Systems [SiS] AC'97 Modem Controller [1039:7013] (rev a0)
00:02.7 Multimedia audio controller [0401]: Silicon Integrated Systems [SiS] AC'97 Sound Controller [1039:7012] (rev a0)
00:03.0 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 1.0 Controller [1039:7001] (rev 0f)
00:03.1 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 1.0 Controller [1039:7001] (rev 0f)
00:03.2 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 2.0 Controller [1039:7002]
00:04.0 Ethernet controller [0200]: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet [1039:0900] (rev 91)
00:06.0 CardBus bridge [0607]: Texas Instruments PCI1410 PC card Cardbus Controller [104c:ac50] (rev 02)
00:0b.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:00.0 VGA compatible controller [0300]: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter [1039:6330]

```

---

### Post by ubutufan on 2007-12-30
In the interfaces file maintain the first two lines only and comment out the rest

---

### Post by nipun_jain on 2008-01-04
Hey, that seems to work! But how do I make it permanent? I made another connection using pppoeconf and after a while the interfaces file was the same as before. Had to edit and reboot to get my network to work.

---

### Post by ubutufan on 2008-01-04
I am pleased you had your connection working.

At this point I suggest you switch over to Wicd. Information & installation instructions you may find at [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

The instructions are very simple. Please note that once Wicd is installed it will automatically remove Network manager and take over. It will not mess around any further with the interfaces file.

---

