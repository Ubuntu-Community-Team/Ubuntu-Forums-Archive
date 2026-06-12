---
title: "FS AMILO Pro v3405 kill switch"
date: 2008-07-13
forum: Networking &amp; Wireless
---

### Post by Tatjanaen on 2008-07-13
After browsing the forums I finally made my Intel Pro/wireless 3945ABG sort of work in 8.04. The wireless card i visible in the Network Manager, but I can't see networks on scan.

Besides, I have to type "modprobe ndiswrapper" after each boot as I could only make the card visible by using the windows driver via ndiswrapper. This is probably a silly question, but can I make it do it by itself when I boot? 

In a thread on similar problems on another Amilo machine ( [http://ubuntuforums.org/showthread.php?t=822456&highlight=3945abg+radio](http://ubuntuforums.org/showthread.php?t=822456&highlight=3945abg+radio) )
someone mentioned checking for a kill switch error by doing the following command: sudo cat /var/log/messages | grep switch

Which gives me the following output:
tatjana@tatjana-laptop:~$ sudo cat /var/log/messages | grep switch
Jul 12 17:43:10 tatjana-laptop kernel: [   12.018696] SMP alternatives: switching to UP code
Jul 12 17:43:10 tatjana-laptop kernel: [   12.434511] SMP alternatives: switching to SMP code
Jul 12 17:43:10 tatjana-laptop kernel: [   12.702943] ACPI: EC: non-query interrupt received, switching to interrupt mode
Jul 12 17:43:10 tatjana-laptop kernel: [   31.290086] Kill switch must be turned off for wireless networking to work.
Jul 13 12:01:41 tatjana-laptop kernel: [   12.856094] SMP alternatives: switching to UP code
Jul 13 12:01:41 tatjana-laptop kernel: [   13.281116] SMP alternatives: switching to SMP code
Jul 13 12:01:41 tatjana-laptop kernel: [   13.548384] ACPI: EC: non-query interrupt received, switching to interrupt mode
Jul 13 12:01:41 tatjana-laptop kernel: [   32.663175] Kill switch must be turned off for wireless networking to work.
Jul 13 15:11:03 tatjana-laptop kernel: [   12.569483] SMP alternatives: switching to UP code
Jul 13 15:11:03 tatjana-laptop kernel: [   12.994707] SMP alternatives: switching to SMP code
Jul 13 15:11:03 tatjana-laptop kernel: [   13.261737] ACPI: EC: non-query interrupt received, switching to interrupt mode
Jul 13 15:11:03 tatjana-laptop kernel: [   32.689935] Kill switch must be turned off for wireless networking to work.
Jul 13 16:34:11 tatjana-laptop kernel: [   76.806943] SMP alternatives: switching to UP code
Jul 13 16:34:11 tatjana-laptop kernel: [   77.230158] SMP alternatives: switching to SMP code
Jul 13 16:34:11 tatjana-laptop kernel: [   77.495960] ACPI: EC: non-query interrupt received, switching to interrupt mode
Jul 13 16:34:11 tatjana-laptop kernel: [   96.845560] Kill switch must be turned off for wireless networking to work.
Jul 13 16:36:48 tatjana-laptop kernel: [  180.460701] SMP alternatives: switching to UP code
Jul 13 16:36:48 tatjana-laptop kernel: [    2.483201] SMP alternatives: switching to SMP code
Jul 13 16:59:29 tatjana-laptop kernel: [   12.158895] SMP alternatives: switching to UP code
Jul 13 16:59:29 tatjana-laptop kernel: [   12.593545] SMP alternatives: switching to SMP code
Jul 13 16:59:29 tatjana-laptop kernel: [   12.859101] ACPI: EC: non-query interrupt received, switching to interrupt mode
Jul 13 17:32:11 tatjana-laptop kernel: [   83.625563] SMP alternatives: switching to UP code
Jul 13 17:32:11 tatjana-laptop kernel: [   84.052273] SMP alternatives: switching to SMP code
Jul 13 17:32:11 tatjana-laptop kernel: [   84.318184] ACPI: EC: non-query interrupt received, switching to interrupt mode

Which could make it seem that the problem is indeed the kill switch, but neither doing the keyboard combination to turn wireless on/off, the actual wireless key nor BIOS editing changes that my LED is off and, apparently, my wireless as well. I simply can't seem to turn it on, and I am hoping someone know what to do?

I've used the common diagnostic codes that I know to give more info on my system:

tatjana@tatjana-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
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
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
0a:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
tatjana@tatjana-laptop:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 02
       serial: 00:13:02:7d:74:43
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+netw4x32 driverversion=1.52+Intel,03/13/2008,11.5.1.15 latency=0 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:0a:07.0
       logical name: eth0
       version: 10
       serial: 00:0a:e4:b8:61:09
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.53 latency=32 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
tatjana@tatjana-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          RTS thr=1600 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

tatjana@tatjana-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

---

### Post by Tatjanaen on 2008-07-31
No one knows how to deal with stubborn kill switches?...

---

### Post by beschu on 2008-11-25
> **Tatjanaen said:**
> No one knows how to deal with stubborn kill switches?...

Hey, just try to install acerhk- the wireless works fine on my FS Amilo Pro V3405 and Debian. ;)

---

