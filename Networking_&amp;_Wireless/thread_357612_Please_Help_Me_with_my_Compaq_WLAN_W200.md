---
title: "Please Help Me with my Compaq WLAN W200"
date: 2007-02-09
forum: Networking &amp; Wireless
---

### Post by crazydrum567 on 2007-02-09
I just installed Edgy Eft on my laptop. I'm not very aquainted with Ubuntu so please help me with the easiest way to do this. There is a built in WLAN W200 wlan card from Compaq. Here is a link to the driver (I don't know if it will help you solve the problem or not, as i said, I'm new to all this) Link: [http://h10025.www1.hp.com/ewfrf/wc/genericSoftwareDownloadIndex?lc=en&cc=us&softwareitem=hb-22765-1](http://h10025.www1.hp.com/ewfrf/wc/genericSoftwareDownloadIndex?lc=en&cc=us&softwareitem=hb-22765-1)

Please help me get my wireless card working!

---

### Post by gradedcheese on 2007-02-10
Please open a terminal (Applications->Terminal) and run "lspci" and then post the output here.  Also run "ifconfig" and "iwconfig" and then post the output here.

---

### Post by mylinuxcluster on 2007-02-11
Check out [https://help.ubuntu.com/community/WifiDocs/Device/CompaqW200](https://help.ubuntu.com/community/WifiDocs/Device/CompaqW200) :)

---

### Post by Idrive on 2007-04-06
> **gradedcheese said:**
> Please open a terminal (Applications->Terminal) and run "lspci" and then post the output here.  Also run "ifconfig" and "iwconfig" and then post the output here.
Well im not the thread starter but I was wondering if you could help me out.  I got the light to turn on I just can't seem to get wireless working.  Here are the things you asked for:
> dustin@dustin-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845 845 (Brookdale) Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 (Brookdale) Chipset AGP Bridge (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
02:04.0 Communication controller: Agere Systems LT WinModem (rev 02)
02:06.0 CardBus bridge: Texas Instruments PCI1420
02:06.1 CardBus bridge: Texas Instruments PCI1420
02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VM (KM) Ethernet Controller (rev 42)
02:0e.0 USB Controller: NEC Corporation USB (rev 41)
02:0e.1 USB Controller: NEC Corporation USB (rev 41)
02:0e.2 USB Controller: NEC Corporation USB 2.0 (rev 02)
dustin@dustin-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:02:A5:C0:CE:84  
          inet addr:192.168.1.8  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::202:a5ff:fec0:ce84/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:23309 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17525 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10878145 (10.3 MiB)  TX bytes:6061711 (5.7 MiB)

eth1      Link encap:Ethernet  HWaddr 00:0B:CD:8D:23:27  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1653 (1.6 KiB)  TX bytes:2640 (2.5 KiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

dustin@dustin-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"JDAT"  Nickname:"HERMES I"
          Mode:Managed  Frequency:2.457 GHz  Access Point: None   
          Bit Rate:5.5 Mb/s   Sensitivity:1/3  
          Retry limit:4   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=3/92  Signal level=-77 dBm  Noise level=-80 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:45
          Tx excessive retries:34  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

dustin@dustin-laptop:~$ 


---

### Post by merlinus on 2007-06-06
The instructions at help.ubuntu.com worked, after some editing of orinoco.c

See [http://ubuntuforums.org/showthread.php?t=466379](http://ubuntuforums.org/showthread.php?t=466379)

Many thanks to chili555!

-merlin

---

