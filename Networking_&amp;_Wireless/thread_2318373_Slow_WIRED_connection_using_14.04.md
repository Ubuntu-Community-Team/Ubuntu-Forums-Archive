---
title: "Slow WIRED connection using 14.04"
date: 2016-03-25
forum: Networking &amp; Wireless
---

### Post by oldsoundguy on 2016-03-25
Recently, my ISP (Comcast) opened up to 1gb in speed.  I have 3 machines that I use on my home network .. two wired and one wireless.  The OLD WinXP machine went to 90+mb immediately.  The Win 7 laptop never got above 30 mb on the wireless until I purchased Tweak Bit Internet Optimizer from Auslogic. Laptop runs at 80+mb when hard wired into the net.

My 14.04 is struggling to get above 30mb.
Is there some tweaks I can use or should I hope that the issue is fixed when 16.04 lands? 

Thanks a bunch.

---

### Post by praseodym on 2016-03-26
Hardware?
```

lspci -nnk
```

---

### Post by oldsoundguy on 2016-03-26
00:00.0 Host bridge [0600]: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub [8086:2580] (rev 04)
	Subsystem: Hewlett-Packard Company Device [103c:3005]
	Kernel driver in use: agpgart-intel
00:02.0 VGA compatible controller [0300]: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller [8086:2582] (rev 04)
	Subsystem: Hewlett-Packard Company Device [103c:3005]
	Kernel driver in use: i915
00:1c.0 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 [8086:2660] (rev 03)
	Kernel driver in use: pcieport
00:1c.1 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 [8086:2662] (rev 03)
	Kernel driver in use: pcieport
00:1d.0 USB controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [8086:2658] (rev 03)
	Subsystem: Hewlett-Packard Company Device [103c:3005]
	Kernel driver in use: uhci_hcd
00:1d.1 USB controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [8086:2659] (rev 03)
	Subsystem: Hewlett-Packard Company Device [103c:3005]
	Kernel driver in use: uhci_hcd
00:1d.2 USB controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [8086:265a] (rev 03)
	Subsystem: Hewlett-Packard Company Device [103c:3005]
	Kernel driver in use: uhci_hcd
00:1d.3 USB controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 [8086:265b] (rev 03)
	Subsystem: Hewlett-Packard Company Device [103c:3005]
	Kernel driver in use: uhci_hcd
00:1d.7 USB controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [8086:265c] (rev 03)
	Subsystem: Hewlett-Packard Company Device [103c:3005]
	Kernel driver in use: ehci-pci
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev d3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge [8086:2640] (rev 03)
	Kernel driver in use: lpc_ich
00:1f.1 IDE interface [0101]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller [8086:266f] (rev 03)
	Subsystem: Hewlett-Packard Company Device [103c:3005]
	Kernel driver in use: ata_piix
00:1f.2 IDE interface [0101]: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller [8086:2651] (rev 03)
	Subsystem: Hewlett-Packard Company Device [103c:3005]
	Kernel driver in use: ata_piix
05:04.0 Multimedia audio controller [0401]: Creative Labs SB Live! EMU10k1 [1102:0002] (rev 07)
	Subsystem: Creative Labs Device [1102:806b]
	Kernel driver in use: snd_emu10k1
05:04.1 Input device controller [0980]: Creative Labs SB Live! Game Port [1102:7002] (rev 07)
	Subsystem: Creative Labs Gameport Joystick [1102:0020]
	Kernel driver in use: Emu10k1_gameport
40:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express [14e4:1677] (rev 01)
	Subsystem: Hewlett-Packard Company Device [103c:3005]
	Kernel driver in use: tg3

---

### Post by praseodym on 2016-03-27
Ok, the driver "tg3" is there. Lets check
```

sudo apt-get install ethtool
sudo ethtool eth0
ifconfig -a
route -n
cat /etc/resolv.conf
```

---

### Post by oldsoundguy on 2016-03-27
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ethtool is already the newest version.
ethtool set to manually installed.
The following packages were automatically installed and are no longer required:
  compiz-plugins-main gnome-dictionary gnome-search-tool libmpdec2
  libquvi-scripts libquvi7 libreoffice-emailmerge linux-headers-3.13.0-61
  linux-headers-3.13.0-61-generic linux-image-3.13.0-61-generic
  linux-image-extra-3.13.0-61-generic printer-driver-hpijs
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.

---

### Post by praseodym on 2016-03-27
And the other commands?

---

### Post by oldsoundguy on 2016-03-27
eth1      Link encap:Ethernet  HWaddr 00:13:21:00:1f:f3  
          inet addr:10.0.0.4  Bcast:10.0.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1621949 errors:0 dropped:0 overruns:0 frame:0
          TX packets:796660 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1176423510 (1.1 GB)  TX bytes:518170966 (518.1 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:75576 errors:0 dropped:0 overruns:0 frame:0
          TX packets:75576 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8425310 (8.4 MB)  TX bytes:8425310 (8.4 MB)

dave@dave-desktop-mediaroom:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.0.0.1        0.0.0.0         UG    0      0        0 eth1
10.0.0.0        0.0.0.0         255.255.255.0   U     1      0        0 eth1
dave@dave-desktop-mediaroom:~$ cat /etc/resolv.conf

---

### Post by oldsoundguy on 2016-03-27
And that boosted speed to about 40!

---

### Post by oldsoundguy on 2016-03-31
Anybody else have some suggestions?  This HELPED, but would really like to speed this pup up!  
IF NOT, guess will hang in there until 16.4 gets shaken out and HOPE that they have discovered the issue and addressed that issue.

---

### Post by oldsoundguy on 2016-04-07
Just to bump this up .. still looking for a bit more speed.

---

