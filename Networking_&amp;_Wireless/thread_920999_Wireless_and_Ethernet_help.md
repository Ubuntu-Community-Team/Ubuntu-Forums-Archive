---
title: "Wireless and Ethernet help"
date: 2008-09-15
forum: Networking &amp; Wireless
---

### Post by darling55 on 2008-09-15
Hello I am very new to ubuntu and my problem is that I cannot connect to any wireless networks or a LAN. I can get Ubuntu to recognize the cards, and the drivers. I have a Toshiba tecra a4 with a Intel bg2200 wireless card and a Marvell Yukon 88E8036 Ethernet. I also have a dual boot setup and both of the connections work in windows xp.

Here are some of my results for lspci, ifconfig, and iwconfig

lspci
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
01:00.0 VGA compatible controller: ATI Technologies Inc M24 1P [Radeon Mobility X600]
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 10)
06:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
06:06.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:06.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
06:06.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
06:06.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
brad@LeadFarmer:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:a0:d1:20:b8:87  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 

eth1      Link encap:Ethernet  HWaddr 00:12:f0:72:03:f3  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 Base address:0xa000 Memory:b000b000-b000bfff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1644 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1644 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:82472 (80.5 KB)  TX bytes:82472 (80.5 KB)

brad@LeadFarmer:~$ iwconfig
lo        no wireless extensions.

eth1      radio off  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

---

### Post by darling55 on 2008-09-16
Anyone?

---

### Post by figmentx on 2008-09-16
I'm going to focus on the nic card first, since that is pretty strange it's not working out of the box.

You mentioned dual boot setup, so I take it you have have installed ubuntu to the hardrive and are not using a livecd right?

Run 2 ping tests for me,

ping 127.0.0.1
ping 192.168.1.1        (or the ip of your LAN's gateway device (router))

tell us what you get back.

---

### Post by darling55 on 2008-09-17
If I ping 192.168.1.1 I get a Destination Host Unreachable message, but i think that that is not the ip of the router. Also I am at college and have no access to the router. In windows when I run ipconfig it tells me that the default gateway is 172.24.1.8 and I can ping that in windows however whenever I ping it from ubuntu I get the destination host unreachable. When I ping 127.0.0.1 it works.

---

### Post by darling55 on 2008-09-19
Bump

---

### Post by thebeege on 2008-10-03
Running the same machine, I just loaded it up and am having similar issues.  I will reply again If and when I solve the problem...
Anyone else who may have some hints please help!

---

### Post by darling55 on 2008-10-04
I think I figured out the problem, I just have to update the BIOS. But whenever I do that I get a error so I am unable to try it.

---

