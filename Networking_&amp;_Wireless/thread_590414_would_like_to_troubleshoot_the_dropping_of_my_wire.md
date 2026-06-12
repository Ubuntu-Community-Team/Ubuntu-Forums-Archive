---
title: "would like to troubleshoot the dropping of my wired internet connection (using wicd)"
date: 2007-10-24
forum: Networking &amp; Wireless
---

### Post by kraymore on 2007-10-24
I would like to troubleshoot the dropping of my internet connection on a daily basis.  i use the wicd network manager, have a wired connection (as well as wireless during emergencies) and using the wired connection on wicd version 1.3.1 i lose internet connection pretty much daily and i have no idea what log file i should post for troubleshooting purposes.  my router is a WRT150N however i dont think that has any bearing on my losing my connection its relatively new.  when i lose connection i try to regain it using wicd on the wired side as well as neighbors wireless and if it weren't for my neighbors wireless i wouldn't have internet at all.  

could someone please tell me what log file to post ?  

the network adaptor is the one in the 965P chipset (Gigabyte GA-965P-DS3).  i bought it because i had similar problems using a former motherboard.  perhaps that motherboard is actually ok.  

would appreciate any help

---

### Post by redgum11 on 2007-10-26
Hi, I am not hijacking your thread, well sort of. I am hoping that me bringing the same problem to your post will help find a common solution. I used the search feature and could not find a recent post with same issue or fix. I found some threads concerning wireless but just as kraymore's, my issue is with wired. Please dont hesitate to ask for any additional info. Please help resolve this very troublesome issue. I already removed IPv6 to no avail.

Symptoms:

Lose wired ethernet connection after roughly 1:30 uptime and actively using the internet. Issue does not happen on winXP dual boot.
Ethernet is currently PPPoE but issue happens as well with Dlink router and Static IP, just dies after a short while.

Based on other threads here's some info you might need:

00:00.0 Host bridge [0600]: nVidia Corporation nForce3 250Gb Host Bridge [10de:00e1] (rev a1)
00:01.0 ISA bridge [0601]: nVidia Corporation nForce3 250Gb LPC Bridge [10de:00e0] (rev a2)
00:01.1 SMBus [0c05]: nVidia Corporation nForce 250Gb PCI System Management [10de:00e4] (rev a1)
00:02.0 USB Controller [0c03]: nVidia Corporation CK8S USB Controller [10de:00e7] (rev a1)
00:02.1 USB Controller [0c03]: nVidia Corporation CK8S USB Controller [10de:00e7] (rev a1)
00:02.2 USB Controller [0c03]: nVidia Corporation nForce3 EHCI USB 2.0 Controller [10de:00e8] (rev a2)
00:08.0 IDE interface [0101]: nVidia Corporation CK8S Parallel ATA Controller (v2.5) [10de:00e5] (rev a2)
00:0a.0 IDE interface [0101]: nVidia Corporation CK8S Serial ATA Controller (v2.5) [10de:00e3] (rev a2)
00:0b.0 PCI bridge [0604]: nVidia Corporation nForce3 250Gb AGP Host to PCI Bridge [10de:00e2] (rev a2)
00:0e.0 PCI bridge [0604]: nVidia Corporation nForce3 250Gb PCI-to-PCI Bridge [10de:00ed] (rev a2)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV350 AQ [Radeon 9600] [1002:4151]
01:00.1 Display controller [0380]: ATI Technologies Inc RV350 AQ [Radeon 9600] (Secondary) [1002:4171]
02:08.0 Multimedia audio controller [0401]: Creative Labs SB Audigy [1102:0004] (rev 04)
02:08.1 Input device controller [0980]: Creative Labs SB Audigy Game Port [1102:7003] (rev 04)
02:08.2 FireWire (IEEE 1394) [0c00]: Creative Labs SB Audigy FireWire Port [1102:4001] (rev 04)
02:09.0 Ethernet controller [0200]: 3Com Corporation 3c905C-TX/TX-M [Tornado] [10b7:9200] (rev 74)

  *-network               
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: 9
       bus info: pci@0000:02:09.0
       logical name: eth0
       version: 74
       serial: 00:50:da:c9:cf:69
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=half ip=192.168.0.56 latency=32 link=yes maxlatency=10 mingnt=10 module=3c59x multicast=yes port=MII speed=10MB/s

Thanks,
redgum

---

