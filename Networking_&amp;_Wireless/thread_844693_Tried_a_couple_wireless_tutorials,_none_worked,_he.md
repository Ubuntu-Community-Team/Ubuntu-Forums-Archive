---
title: "Tried a couple wireless tutorials, none worked, help?"
date: 2008-06-29
forum: Networking &amp; Wireless
---

### Post by Xpyd3r on 2008-06-29
Okay so lets see here 

It's a Dell XPS, and I didn't get the Window's CDs and daughter used it to the point it got all screwed up, and was irrecoverable without throwing money at it, so I installed Hardy as I use Linux, and ran into these wireless problems. 


lspci

> 00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
02:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
02:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
02:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
02:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)


iwconfig

> lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"Netgear"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1B:2F:58:FC:48   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=78/100  Signal level=-24 dBm  Noise level=-51 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:21


ifconfig

> eth0      Link encap:Ethernet  HWaddr 00:14:22:8b:59:c2  
          inet addr:10.0.0.2  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::214:22ff:fe8b:59c2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1290 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1411 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1329323 (1.2 MB)  TX bytes:268647 (262.3 KB)
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 00:13:ce:54:1c:5d  
          inet addr:10.0.0.4  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:ceff:fe54:1c5d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:881 errors:0 dropped:0 overruns:0 frame:0
          TX packets:71 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1087084 (1.0 MB)  TX bytes:7115 (6.9 KB)
          Interrupt:17 Base address:0xc000 Memory:dfbfd000-dfbfdfff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1786 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1786 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:89300 (87.2 KB)  TX bytes:89300 (87.2 KB)


iwlist scan

> lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:1B:2F:58:FC:48
                    ESSID:"Netgear"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 9 Mb/s; 11 Mb/s
                              6 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=98/100  Signal level=-28 dBm  
                    Extra: Last beacon: 220ms ago


Oh yea, and btw, the Wifi light isn't on and the Fn+F2 doesn't light it up.

Any ideas what I'm doing wrong? Anything I'm forgetting to change or check?  Any and all help is greatly appreciated, I'm at my wits end with this, and I'm about ready to just run a dang ethernet cord

---

### Post by plewisfdx on 2008-06-29
Looks like eth1 (wireless) is good to go with an ip address and all! (10.0.0.4)

And it looks like eth0 already has an ethernet cable hooked up to it (ip address 10.0.0.2)

Hardy broke the wifi light on my Dell laptop as well, but the wifi is workin.

Are you getting errors when you try to access websites, because it looks like all is well?

---

### Post by wabbalee on 2008-06-29
I had trouble too getting wireless to work properly on my acer tm2480, but i fixed it. see this post [http://ubuntuforums.org/showthread.php?t=814117](http://ubuntuforums.org/showthread.php?t=814117) post #6 and #9

---

### Post by Xpyd3r on 2008-06-30
Could I maybe have not restarted? Because after a bit more playing, and shutting off for the night, it worked today when I turned it on, so haha I have no idea, but thanks for the replies guys!

---

