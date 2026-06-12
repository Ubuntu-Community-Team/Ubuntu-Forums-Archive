---
title: "Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller - Gutsy.Help!"
date: 2007-10-27
forum: Networking &amp; Wireless
---

### Post by RC211V on 2007-10-27
Guys my Internet works with 7.10 Beta but it doesn't with the final release! :mad: I have a direct connection to the internet trough ethernet to  my Uni LAN. Please help.

```
feanor@localhost:~$ sudo lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 04)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 04)
01:00.0 VGA compatible controller: ATI Technologies Inc M22 [Mobility Radeon X300]
**02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 15)**
06:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
06:06.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:06.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
06:06.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
06:06.4 Generic system peripheral [0805]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller

feanor@localhost:~$ sudo cat /etc/network/interfaces
auto lo
iface lo inet loopback


feanor@localhost:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:A0:D1:20:C1:4E  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:128 errors:0 dropped:0 overruns:0 frame:0
          TX packets:128 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9840 (9.6 KB)  TX bytes:9840 (9.6 KB)

feanor@localhost:~$ route -v
Kernel IP routeing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
feanor@localhost:~$ 
```

---

### Post by Lambert on 2007-10-28
Run the following commands and post output of first two here.

```


ethtool -i eth0

sudo ethtool eth0

sudo dhclient eth0

```

the last command tries to set up network parameters from the dhcp server so after running check your connection.

---

### Post by RC211V on 2007-10-31
Mate thnx for your reply. Now I just came back from a trip. Ihave been away for 4 days. I turned on my pc and my internet works. I don't know if it will work after I restart. I use the commands as before (ifconfig, cat /etc/network/interfaces etc) and they give the same result but this time with the correct ip etc. It is very strange. If I restart and I have a problem I'll reply again.  :confused:

---

### Post by RC211V on 2007-10-31
Ok so after the restart it doen't work. 

```
feanor@localhost:~$ ethtool -i eth0
driver: sky2
version: 1.18
firmware-version: N/A
bus-info: 0000:02:00.0
feanor@localhost:~$ sudo ethtool eth0
[sudo] password for feanor:
Settings for eth0:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Half 1000baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Half 1000baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: Unknown! (65535)
        Duplex: Unknown! (255)
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pg
        Wake-on: d
        Current message level: 0x000000ff (255)
        Link detected: no
```

---

### Post by RC211V on 2007-11-05
Anyone with a soluiton? I tried debian this week and my internet works. Isn't ubuntu debian based?
Btw is this wrong?
```
Supports Wake-on: pg
        Wake-on: d
```

---

### Post by RC211V on 2007-11-06
Anyone?

---

