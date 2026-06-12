---
title: "Wireless problem in Gutsy: Intel Pro/Wireless 2200BG"
date: 2007-10-25
forum: Networking &amp; Wireless
---

### Post by Aholiab on 2007-10-25
I'm trying to get my wireless working in Gutsy. My solution path below depends on the [HOWTO]("http://ubuntuforums.org/showthread.php?t=13576") at this site for Warty.

Here is what I did:

1. I'm using “2.6.22-14-generic”.
2. After “sudo apt-get install linux-headers-2.6.22-14-generic”, nothing needed to be installed.
3. "sudo apt-get install build-essential"; I'm up-to-date.
4. I then downloaded intel_ipw2200_1.2.0.tgz, “Intel PRO/Wireless 2200BG Driver.”
5. I also downloaded ipw2200-fw-3.0.tgz, “Intel® PRO/Wireless 2200BG Driver Firmware.”
6. After moving to the download folder, I did this: “sudo mv ipw2200-fw-3.0.tgz /usr/lib/hotplug/firmware/”
7. I moved the driver file: "cd /usr/lib/hotplug/firmware/"
8. I did this: “tar zxf ipw2200-fw-3.0.tgz”. So the firmware should be properly installed.
9. After moving to the download folder, I did this: “sudo mv ipw2200-1.2.0.tgz /usr/src"
10. "cd /usr/src/"
11. I did this: “tar zxf ipw2200-1.2.0.tgz”
12. I did this: “cd /usr/src/ipw2200-1.2.0”
13. I tried to "make", but scazillions of errors appears. I could post them. :(

:confused:

So I cannot proceed. Can anyone please help?

---

### Post by kishore_kivi on 2007-10-25
Try Installing Wicd, it worked for me.
It works great with WPA -Personal Security.

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

It is easy!

---

### Post by bobyy on 2007-10-25
Can you post here a  #lspci  and #ifconfig -a ..vicd will help you just if you will have wirelles driver enabled.(anyway the code of vicd is a litel dirty.)...
Can i ask you if you have the windows drivers ? if yes. you can try instal with NDISWRAPPER...

---

### Post by Aholiab on 2007-10-25
Below are the results of #lspci and #ifconfig -a.

No, I do not have the Windows drivers any longer. I screwed up my Windows partition, so I put Ubuntu on the entire hard drive. Bummer. Maybe I could get them online, if that would help.

That's not my smiley below; it's just a colon and a "D".

===
phil@Phil-VAIO:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
06:03.0 CardBus bridge: Texas Instruments PCI7420 CardBus Controller
06:03.2 FireWire (IEEE 1394): Texas Instruments PCI7x20 1394a-2000 OHCI Two-Port PHY/Link-Layer Controller
06:03.3 Mass storage controller: Texas Instruments PCI7420/7620 Combo CardBus, 1394a-2000 OHCI and SD/MS-Pro Controller
06:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
06:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile (rev 03)
phil@Phil-VAIO:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:01:4A:F0:44:80  
          inet addr:192.168.0.10  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::201:4aff:fef0:4480/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:26870 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23640 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:30692829 (29.2 MB)  TX bytes:3590650 (3.4 MB)

eth1      Link encap:Ethernet  HWaddr 00:13:CE:DB:74:F0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:269997 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20800 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:84 (84.0 b)
          Interrupt:22 Base address:0xc000 Memory:b0106000-b0106fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1279 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1279 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:118507 (115.7 KB)  TX bytes:118507 (115.7 KB)

phil@Phil-VAIO:~$

---

