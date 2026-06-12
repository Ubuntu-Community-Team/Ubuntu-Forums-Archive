---
title: "no wireless connection"
date: 2009-11-10
forum: New to Ubuntu
---

### Post by sophie1983 on 2009-11-10
Hi I'm completely new to ubuntu. I just got rid of windows XP and got ubuntu 9.10 on my HP compaq nx6310 laptop. Everything is working really well apart from my wireless internet. My mobile broadband works fine. The wireless light never flashes and in the network manager there are no listed wireless networks (this is true when I'm at home with another computer able to detect and use my home wireless and at work where other peoples computer can use the wireless fine).

ifconfig read out is:

eth0      Link encap:Ethernet  HWaddr 00:17:08:35:2c:df  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

hso0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:10.94.229.179  P-t-P:10.94.229.179  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1486  Metric:1
          RX packets:1908 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1956 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:10 
          RX bytes:1762736 (1.7 MB)  TX bytes:257011 (257.0 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lspci read out is:

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 01)
02:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
02:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
02:0e.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
08:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

When I ping ubuntu.com I get 100% successful packets

I have spent all day trying to sort this out by searching forums for suggestions, but nothing that other people has said works for has worked for me.

Any suggestions please?


Thanks

---

### Post by prshah on 2009-11-10
> **sophie1983 said:**
> 
ifconfig read out is:
eth0      Link encap:Ethernet  HWaddr 00:17:08:35:2c:df  
hso0      Link encap:UNSPEC  HWaddr lo        Link encap:Local Loopback  

lspci read out is:

02:0e.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
08:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)


From your output, it doesn't seem as though the wireless hardware has been recognized. You can confirm this using the ```
iwconfig
``` command. If this is in fact the case, then you can follow [this thread]("http://ubuntuforums.org/showthread.php?t=1288865") to find an appropriate solution for Broadcom wireless in Ubuntu 9.10 (Karmic Koala).

Post back here if you have any difficulties, with details of what you have done and outputs.

---

### Post by sophie1983 on 2009-11-12
Hi thanks so much! It finally worked and now everything is working really well. I'm so pleased that I switched from windows XP to Ubuntu!

Thanks again

---

### Post by welwitschia on 2011-01-05
I had the exact same problem with the exact same machine.

Thanks for your help!

---

