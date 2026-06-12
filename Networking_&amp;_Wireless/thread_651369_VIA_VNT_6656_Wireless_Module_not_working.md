---
title: "VIA VNT 6656 Wireless Module not working"
date: 2007-12-27
forum: Networking &amp; Wireless
---

### Post by Maricaibo on 2007-12-27
I have been all over trying to install drivers for this wireless module. Tried Logic Supply, VIA Arena, Sourceforge. Have run Make so many times I dunno what's installed anymore. Latest effort was "ndiswrapper-1.51" from [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/)

My CAT5 Ethernet connection works just fine but I need the wireless to work, too!

Running Gutsy 2.6.22-14-generic
VIA EN12000EG MB w/ 1GB RAM
VIA Networking VNT6656G6A40 54 MBps Wireless USB Module VIA Embedded

System log shows:
Dec 27 10:26:33 Ubuntu kernel: [  256.322747] ndiswrapper version 1.51 loaded (smp=yes, preempt=no)
Dec 27 10:26:33 Ubuntu loadndisdriver: loadndisdriver: load_device(426): couldn't chdir to /etc/ndiswrapper: No such file or directory 
Dec 27 10:26:34 Ubuntu last message repeated 8 times
Dec 27 10:26:34 Ubuntu kernel: [  256.367622] usbcore: registered new interface driver ndiswrapper


brass@Ubuntu:~$ sudo ndiswrapper -l
ls: /etc/ndiswrapper: No such file or directory

brass@Ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


brass@Ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: VT6120/VT6121/VT6122 Gigabit Ethernet Adapter
       vendor: VIA Technologies, Inc.
       physical id: e
       bus info: pci@0000:00:0e.0
       logical name: eth0
       version: 11
       serial: 00:40:63:ef:f6:18
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=via-velocity driverversion=1.14 ip=192.168.0.70 latency=32 maxlatency=8 mingnt=3 module=via_velocity multicast=yes


brass@Ubuntu:~$ lsusb
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 160a:3184  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  


brass@Ubuntu:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:0d.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
00:0e.0 Ethernet controller: VIA Technologies, Inc. VT6120/VT6121/VT6122 Gigabit Ethernet Adapter (rev 11)
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
01:00.0 VGA compatible controller: VIA Technologies, Inc. UniChrome Pro IGP (rev 01)


Device Manager lists the  VNT USB-802.11 Wireless LAN Adapter

Am quite at a loss on how to proceed from here. Hammering at this for three days now with no clear idea what I'm doing or why the many suggestions I find aren't working for me. Thinking I should Gutsy and try to start from scratch but am unsure where to begin.

:confused:

---

