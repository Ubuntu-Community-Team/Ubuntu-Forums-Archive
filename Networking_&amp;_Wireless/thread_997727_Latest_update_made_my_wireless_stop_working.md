---
title: "Latest update made my wireless stop working"
date: 2008-11-30
forum: Networking &amp; Wireless
---

### Post by rwalker999 on 2008-11-30
I've been with Ibex for a while, and since I got it, the wireless has been spotty at best. It would work initially, then go out, forcing me to reconnect. I'd have to do so about 20x/day.
Anyways, after the most recent system update, my laptop won't even recognize that there is an active wireless card.

I'm running an HP dv6915nr (i686), Atheros 802.11, and 8.10 last updated sometime Thursday or Friday. My device manager is set on "Support for 5xxx series of Atheros 802.11..." I've set it on that and rebooted, and set it on "Support for Atheros 802.11..." and rebooted, neither made a difference.

If anyone can help me get my wireless going, I'd greatly appreciate it.  Need my laptop and wireless working for my law school exams in 1.5 weeks.

If I need to attach any terminal outputs, just let me know and I'll do so with the quickness.

Thanks so much (for this help and past help I've found here...) Any help may be rewarded in the future with some free legal services

---

### Post by impala79 on 2008-11-30
Do you know if the wireless adapter worked "out of the box" or did you have to manually install a driver for it. If you did have to manually install the driver, there's a chance you'll have to do it again since there was a kernel update in the latest system update. 

If it simply worked before and ubuntu just recognized without you having to install drivers, then i'm not sure what's going on!

---

### Post by rwalker999 on 2008-11-30
> **impala79 said:**
> Do you know if the wireless adapter worked "out of the box" or did you have to manually install a driver for it. If you did have to manually install the driver, there's a chance you'll have to do it again since there was a kernel update in the latest system update. 

If it simply worked before and ubuntu just recognized without you having to install drivers, then i'm not sure what's going on!

My wireless adapter worked when my laptop was running Vista, and it worked when I was running Hardy Heron, although it suddenly stopped one night, which prompted me to upgrade to Ibex, not realizing the problems that might involve.
Anyways, I've installed drivers to get it working with Ibex, but the last updates are keeping my lappie from even realizing that it can connect to any wireless networks.  I click on the network icon in the top bar, and all that come up are "Wired Network" and "VPN Connections".

I tried switching the drivers in Hardware drivers, but no dice.

---

### Post by impala79 on 2008-11-30
Mine did the same thing with the last update. I had to reinstall the driver from scratch. If your machine doesn't even realize it can see wireless networks it likely sees your adapter but doesn't know what to do with it! If you have whatever driver(s) you used when you first upgraded to Ibex to get it working, try installing them once again. Lame, I know, but it worked for me! Good Luck!

---

### Post by shafi on 2008-11-30
maybe try this , it works for most HP and Compaq laptops:

1. 
[HTML] sudo apt-get install ndisgtk[/HTML]
2. download the **xp32-6.0.3.85.zip** from
 [http://www.atheros.cz/download.php?atheros=AR5008&system=1](http://www.atheros.cz/download.php?atheros=AR5008&system=1) 

3. extract the download zip file and go to the xp direcotry and enter the following command:
[HTML]sudo ndiswrapper -i net5416.inf[/HTML]
4. Save ndiswrapper module configuration files by issuing the command: 
[HTML]sudo ndiswrapper -ma && sudo ndiswrapper -mi[/HTML]

5. Reboot and try. now you should see a wlan0 interfase when 
you excecute: 
[HTML]sudo ifconfig[/HTML]
if still doesn't work , download the madwifi-0.9.4.tar.gz from :
[http://sourceforge.net/project/showfiles.php?group_id=82936&package_id=85233](http://sourceforge.net/project/showfiles.php?group_id=82936&package_id=85233)
extract and Install ( read the README or INSTALL file )
and then do the above steps again.

---

### Post by rwalker999 on 2008-11-30
> **shafi said:**
> maybe try this , it works for most HP laptops:

]
2. download the **xp32-6.0.3.85.zip** from
 [http://www.atheros.cz/download.php?atheros=AR5008&system=1](http://www.atheros.cz/download.php?atheros=AR5008&system=1) 

3. extract the download zip file and go to the xp direcotry and enter the following command:
[HTML]sudo ndiswrapper -i net5416.inf[/HTML]


Ok, so I'm not very good with terminal yet... can you give me instructions on how to go about getting to the xp directory and then extracting?

---

### Post by shafi on 2008-11-30
> **rwalker999 said:**
> Ok, so I'm not very good with terminal yet... can you give me instructions on how to go about getting to the xp directory and then extracting?
Just right click on the folder then extract,
after that go to the extracted folder and read the INSTALL or README file
if there is no README or INSTALL file only execute the above command.

---

### Post by rwalker999 on 2008-11-30
> **shafi said:**
> Just right click on the folder then extract,
after that go to the extracted folder and read the INSTALL or README file
The atheros.cz file doesn't have an install or readme file, and sadly, the install file for madwifi skips over a few steps that I'm not familiar with.

---

### Post by rwalker999 on 2008-11-30
> **rwalker999 said:**
> The atheros.cz file doesn't have an install or readme file, and sadly, the install file for madwifi skips over a few steps that I'm not familiar with.
This is the output from entering "lshw -C network" : 
WARNING: you should run this program as super-user.
*-network
description: Ethernet interface
product: MCP67 Ethernet
vendor: nVidia Corporation
physical id: a
bus info: pci@0000:00:0a.0
logical name: eth0
version: a2
serial: 00:1e:68:7f:07:00
width: 32 bits
clock: 66MHz
capabilities: bus_master cap_list ethernet physical
configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=192.168.1.9 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
*-network UNCLAIMED
description: Ethernet controller
product: AR242x 802.11abg Wireless PCI Express Adapter
vendor: Atheros Communications Inc.
physical id: 0
bus info: pci@0000:03:00.0
version: 01
width: 64 bits
clock: 33MHz
capabilities: cap_list
configuration: latency=0
*-network DISABLED
description: Ethernet interface
physical id: 1
logical name: pan0
serial: 4e:71:c3:7d:f0:4a
capabilities: ethernet physical
configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by rwalker999 on 2008-11-30
> **shafi said:**
> maybe try this , it works for most HP and Compaq laptops:

1. 
[HTML] sudo apt-get install ndisgtk[/HTML]
2. download the **xp32-6.0.3.85.zip** from
 [http://www.atheros.cz/download.php?atheros=AR5008&system=1](http://www.atheros.cz/download.php?atheros=AR5008&system=1) 

3. extract the download zip file and go to the xp direcotry and enter the following command:
[HTML]sudo ndiswrapper -i net5416.inf[/HTML]
4. Save ndiswrapper module configuration files by issuing the command: 
[HTML]sudo ndiswrapper -ma && sudo ndiswrapper -mi[/HTML]

5. Reboot and try. now you should see a wlan0 interfase when 
you excecute: 
[HTML]sudo ifconfig[/HTML]
if still doesn't work , download the madwifi-0.9.4.tar.gz from :
[http://sourceforge.net/project/showfiles.php?group_id=82936&package_id=85233](http://sourceforge.net/project/showfiles.php?group_id=82936&package_id=85233)
extract and Install ( read the README or INSTALL file )
and then do the above steps again.
Ok, i figured out how to navigate around terminal, and I got to the xp directory, but I got an error message when i did the ndiswrapper -i 


it says "couldn't open net5416.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219

---

### Post by shafi on 2008-11-30
> **rwalker999 said:**
> Ok, i figured out how to navigate around terminal, and I got to the xp directory, but I got an error message when i did the ndiswrapper -i 


it says "couldn't open net5416.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219

I have update the post , read it carefully and try installing madwifi-0.9.4.tar.gz and read the README and INSTALL file carefully, 
exacure the dniswrapper -i net5416.inf  inside the xp direcotry,it should works.

---

### Post by rwalker999 on 2008-11-30
Done that already.  Installed madwifi and did the "$ make" process through terminal twice, and I still can't get the ndiswrapper command to do anything.

Rebooting after all of my attempts didn't do anything either :(

---

### Post by shafi on 2008-11-30
> **rwalker999 said:**
> Done that already.  Installed madwifi and did the "$ make" process through terminal twice, and I still can't get the ndiswrapper command to do anything.

Rebooting after all of my attempts didn't do anything either :(

did you execute the :
sudo apt-get install ndisgtk , and it was installed successfully?

---

### Post by rwalker999 on 2008-11-30
Yes, "ndisgtk is already the newest version" is the output I'm getting.

---

### Post by shafi on 2008-11-30
> **rwalker999 said:**
> Yes, "ndisgtk is already the newest version" is the output I'm getting.
Not working still?
can you post the result of this command?
[HTML]sudo lspci -v[/HTML]

and also can you post the out put of these two commands:
[HTML]
~$ pwd
~$ sudo ndiswrapper -i net5416.inf[/HTML]

---

### Post by rwalker999 on 2008-11-30
"sudo lspci -v" returned this:

00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
	Subsystem: Hewlett-Packard Company Device 30cf
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: [44] HyperTransport: Slave or Primary Interface
	Capabilities: [dc] HyperTransport: MSI Mapping Enable+ Fixed-

00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
	Subsystem: Hewlett-Packard Company Device 30cf
	Flags: bus master, 66MHz, fast devsel, latency 0

00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
	Subsystem: Hewlett-Packard Company Device 30cf
	Flags: 66MHz, fast devsel, IRQ 10
	I/O ports at 3080 [size=64]
	I/O ports at 3040 [size=64]
	I/O ports at 3000 [size=64]
	Capabilities: [44] Power Management version 2

00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
	Subsystem: Hewlett-Packard Company Device 30cf
	Flags: 66MHz, fast devsel

00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
	Subsystem: Hewlett-Packard Company Device 30cf
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 11
	Memory at f6200000 (32-bit, non-prefetchable) [size=512K]

00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2) (prog-if 10)
	Subsystem: Hewlett-Packard Company Device 30cf
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18
	Memory at f6486000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd

00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2) (prog-if 20)
	Subsystem: Hewlett-Packard Company Device 30cf
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	Memory at f6489000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [44] Debug port: BAR=1 offset=0098
	Capabilities: [80] Power Management version 2
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2) (prog-if 10)
	Subsystem: Hewlett-Packard Company Device 30cf
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18
	Memory at f6487000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd

00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2) (prog-if 20)
	Subsystem: Hewlett-Packard Company Device 30cf
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	Memory at f6489400 (32-bit, non-prefetchable) [size=256]
	Capabilities: [44] Debug port: BAR=1 offset=0098
	Capabilities: [80] Power Management version 2
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1) (prog-if 8a [Master SecP PriP])
	Subsystem: Device f03c:30cf
	Flags: bus master, 66MHz, fast devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at 30c0 [size=16]
	Capabilities: [44] Power Management version 2
	Kernel driver in use: pata_amd
	Kernel modules: pata_amd

00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
	Subsystem: Hewlett-Packard Company Device 30cf
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	Memory at f6480000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [44] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
	Capabilities: [6c] HyperTransport: MSI Mapping Enable+ Fixed+
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2) (prog-if 01)
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=64
	Memory behind bridge: f6100000-f61fffff
	Capabilities: [b8] Subsystem: nVidia Corporation Device cb84
	Capabilities: [8c] HyperTransport: MSI Mapping Enable+ Fixed-

00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2) (prog-if 85 [Master SecO PriO])
	Subsystem: Hewlett-Packard Company Device 30cf
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 221
	I/O ports at 30f0 [size=8]
	I/O ports at 30e4 [size=4]
	I/O ports at 30e8 [size=8]
	I/O ports at 30e0 [size=4]
	I/O ports at 30d0 [size=16]
	Memory at f6484000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: [44] Power Management version 2
	Capabilities: [8c] SATA HBA <?>
	Capabilities: [b0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/3 Enable+
	Capabilities: [cc] HyperTransport: MSI Mapping Enable+ Fixed+
	Kernel driver in use: ahci
	Kernel modules: ahci

00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
	Subsystem: Hewlett-Packard Company Device 30cf
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 220
	Memory at f6488000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at 30f8 [size=8]
	Memory at f6489c00 (32-bit, non-prefetchable) [size=256]
	Memory at f6489800 (32-bit, non-prefetchable) [size=16]
	Capabilities: [44] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/3 Enable+
	Capabilities: [6c] HyperTransport: MSI Mapping Enable+ Fixed+
	Kernel driver in use: forcedeth
	Kernel modules: forcedeth

00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=05, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: f2000000-f3ffffff
	Prefetchable memory behind bridge: 00000000f0000000-00000000f1ffffff
	Capabilities: [40] Subsystem: nVidia Corporation Device 0000
	Capabilities: [48] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
	Capabilities: [60] HyperTransport: MSI Mapping Enable+ Fixed-
	Capabilities: [80] Express Root Port (Slot+), MSI 00
	Capabilities: [100] Virtual Channel <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Memory behind bridge: f6000000-f60fffff
	Capabilities: [40] Subsystem: nVidia Corporation Device 0000
	Capabilities: [48] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
	Capabilities: [60] HyperTransport: MSI Mapping Enable+ Fixed-
	Capabilities: [80] Express Root Port (Slot+), MSI 00
	Capabilities: [100] Virtual Channel <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:12.0 VGA compatible controller: nVidia Corporation GeForce 7150M (rev a2)
	Subsystem: Hewlett-Packard Company Device 30cf
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
	Memory at f5000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at f4000000 (64-bit, non-prefetchable) [size=16M]
	[virtual] Expansion ROM at c2000000 [disabled] [size=128K]
	Capabilities: [48] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Kernel driver in use: nvidia
	Kernel modules: nvidiafb, nvidia

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
	Flags: fast devsel
	Capabilities: [80] HyperTransport: Host or Secondary Interface

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	Flags: fast devsel
	Capabilities: [f0] Secure device <?>
	Kernel driver in use: k8temp
	Kernel modules: k8temp

02:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) (prog-if 10)
	Subsystem: Hewlett-Packard Company Device 30cf
	Flags: bus master, medium devsel, latency 64, IRQ 5
	Memory at f6100000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [dc] Power Management version 2
	Kernel driver in use: ohci1394
	Kernel modules: ohci1394

02:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
	Subsystem: Hewlett-Packard Company Device 30cf
	Flags: bus master, medium devsel, latency 64, IRQ 7
	Memory at f6100800 (32-bit, non-prefetchable) [size=256]
	Capabilities: [80] Power Management version 2
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

02:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
	Subsystem: Hewlett-Packard Company Device 30cf
	Flags: bus master, medium devsel, latency 64, IRQ 11
	Memory at f6100c00 (32-bit, non-prefetchable) [size=256]
	Capabilities: [80] Power Management version 2
	Kernel driver in use: ricoh-mmc
	Kernel modules: ricoh_mmc

02:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
	Subsystem: Hewlett-Packard Company Device 30cf
	Flags: bus master, medium devsel, latency 64, IRQ 11
	Memory at f6101000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [80] Power Management version 2

02:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff) (prog-if ff)
	!!! Unknown header type 7f

03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
	Subsystem: Hewlett-Packard Company Device 137a
	Flags: fast devsel, IRQ 19
	Memory at f6000000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: [40] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [60] Express Legacy Endpoint, MSI 00
	Capabilities: [90] MSI-X: Enable- Mask- TabSize=1
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [140] Virtual Channel <?>
	Kernel modules: ath5k, ath_pci


then I got:
ross@ross-hp:~$ pwd
/home/ross
ross@ross-hp:~$ ~$ pwd
bash: ~$: command not found
ross@ross-hp:~$ 

and finally:
ross@ross-hp:~$ sudo ndiswrapper -i net5416.inf
sudo: unable to resolve host ross-hp
couldn't open net5416.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219.

---

### Post by kevdog on 2008-11-30
I'm confused about why you compiled madwifi and then want to use ndiswrapper?  The two are different solutions.

Can you post the following:
lsmod | egrep '(ndis|ath)'
lshw -C network
lspci -nnm

Thanks

---

### Post by shafi on 2008-11-30
> **rwalker999 said:**
> "sudo lspci -v" returned this:

00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
	Subsystem:...

then I got:
ross@ross-hp:~$ pwd
/home/ross
ross@ross-hp:~$ ~$ pwd
bash: ~$: command not found
ross@ross-hp:~$ 

and finally:
ross@ross-hp:~$ sudo ndiswrapper -i net5416.inf
sudo: unable to resolve host ross-hp
couldn't open net5416.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219.
Hmmmmmm, you should execute the **sudo ndiswrapper -i net5416.inf**
inside the **xp32-6.0.3.85** directory !!!!!!
because the net5416.inf file is available inside that directory not your home!

---

### Post by rwalker999 on 2008-11-30
I don't really know this stuff very well, and I saw some contrasting things about madwifi and ndiswrapper... I don't know what either are, really... I'm just trying to get my wireless working.  Aaaaaaanyways...

lsmod gave me this:
ath5k                 106496  0 
lbm_cw_mac80211       210728  1 ath5k
lbm_cw_cfg80211        39696  2 ath5k,lbm_cw_mac80211
led_class              12164  1 ath5k
ath_pci                99096  0 
wlan                  211952  1 ath_pci
ath_hal               198864  1 ath_pci

lshw gave me this:
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1e:68:7f:07:00
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=192.168.1.9 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 8e:3c:c7:12:a2:32
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

and last, lspci -nnm returned this:
00:00.0 "RAM memory [0500]" "nVidia Corporation [10de]" "MCP67 Memory Controller [0547]" -ra2 "Hewlett-Packard Company [103c]" "Device [30cf]"
00:01.0 "ISA bridge [0601]" "nVidia Corporation [10de]" "MCP67 ISA Bridge [0548]" -ra2 "Hewlett-Packard Company [103c]" "Device [30cf]"
00:01.1 "SMBus [0c05]" "nVidia Corporation [10de]" "MCP67 SMBus [0542]" -ra2 "Hewlett-Packard Company [103c]" "Device [30cf]"
00:01.2 "RAM memory [0500]" "nVidia Corporation [10de]" "MCP67 Memory Controller [0541]" -ra2 "Hewlett-Packard Company [103c]" "Device [30cf]"
00:01.3 "Co-processor [0b40]" "nVidia Corporation [10de]" "MCP67 Co-processor [0543]" -ra2 "Hewlett-Packard Company [103c]" "Device [30cf]"
00:02.0 "USB Controller [0c03]" "nVidia Corporation [10de]" "MCP67 OHCI USB 1.1 Controller [055e]" -ra2 -p10 "Hewlett-Packard Company [103c]" "Device [30cf]"
00:02.1 "USB Controller [0c03]" "nVidia Corporation [10de]" "MCP67 EHCI USB 2.0 Controller [055f]" -ra2 -p20 "Hewlett-Packard Company [103c]" "Device [30cf]"
00:04.0 "USB Controller [0c03]" "nVidia Corporation [10de]" "MCP67 OHCI USB 1.1 Controller [055e]" -ra2 -p10 "Hewlett-Packard Company [103c]" "Device [30cf]"
00:04.1 "USB Controller [0c03]" "nVidia Corporation [10de]" "MCP67 EHCI USB 2.0 Controller [055f]" -ra2 -p20 "Hewlett-Packard Company [103c]" "Device [30cf]"
00:06.0 "IDE interface [0101]" "nVidia Corporation [10de]" "MCP67 IDE Controller [0560]" -ra1 -p8a "Unknown vendor [f03c]" "Device [30cf]"
00:07.0 "Audio device [0403]" "nVidia Corporation [10de]" "MCP67 High Definition Audio [055c]" -ra1 "Hewlett-Packard Company [103c]" "Device [30cf]"
00:08.0 "PCI bridge [0604]" "nVidia Corporation [10de]" "MCP67 PCI Bridge [0561]" -ra2 -p01 "" ""
00:09.0 "IDE interface [0101]" "nVidia Corporation [10de]" "MCP67 AHCI Controller [0550]" -ra2 -p85 "Hewlett-Packard Company [103c]" "Device [30cf]"
00:0a.0 "Ethernet controller [0200]" "nVidia Corporation [10de]" "MCP67 Ethernet [054c]" -ra2 "Hewlett-Packard Company [103c]" "Device [30cf]"
00:0c.0 "PCI bridge [0604]" "nVidia Corporation [10de]" "MCP67 PCI Express Bridge [0563]" -ra2 "" ""
00:0d.0 "PCI bridge [0604]" "nVidia Corporation [10de]" "MCP67 PCI Express Bridge [0563]" -ra2 "" ""
00:12.0 "VGA compatible controller [0300]" "nVidia Corporation [10de]" "GeForce 7150M [0531]" -ra2 "Hewlett-Packard Company [103c]" "Device [30cf]"
00:18.0 "Host bridge [0600]" "Advanced Micro Devices [AMD] [1022]" "K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1100]" "" ""
00:18.1 "Host bridge [0600]" "Advanced Micro Devices [AMD] [1022]" "K8 [Athlon64/Opteron] Address Map [1101]" "" ""
00:18.2 "Host bridge [0600]" "Advanced Micro Devices [AMD] [1022]" "K8 [Athlon64/Opteron] DRAM Controller [1102]" "" ""
00:18.3 "Host bridge [0600]" "Advanced Micro Devices [AMD] [1022]" "K8 [Athlon64/Opteron] Miscellaneous Control [1103]" "" ""
02:05.0 "FireWire (IEEE 1394) [0c00]" "Ricoh Co Ltd [1180]" "R5C832 IEEE 1394 Controller [0832]" -r05 -p10 "Hewlett-Packard Company [103c]" "Device [30cf]"
02:05.1 "SD Host controller [0805]" "Ricoh Co Ltd [1180]" "R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [0822]" -r22 "Hewlett-Packard Company [103c]" "Device [30cf]"
02:05.2 "System peripheral [0880]" "Ricoh Co Ltd [1180]" "R5C843 MMC Host Controller [0843]" -r12 "Hewlett-Packard Company [103c]" "Device [30cf]"
02:05.3 "System peripheral [0880]" "Ricoh Co Ltd [1180]" "R5C592 Memory Stick Bus Host Adapter [0592]" -r12 "Hewlett-Packard Company [103c]" "Device [30cf]"
02:05.4 "System peripheral [0880]" "Ricoh Co Ltd [1180]" "xD-Picture Card Controller [0852]" -rff -pff "" ""
03:00.0 "Ethernet controller [0200]" "Atheros Communications Inc. [168c]" "AR242x 802.11abg Wireless PCI Express Adapter [001c]" -r01 "Hewlett-Packard Company [103c]" "Device [137a]"


Thank you so much for helping me thus far, I greatly appreciate it

---

### Post by rwalker999 on 2008-11-30
> **shafi said:**
> Hmmmmmm, you should execute the **sudo ndiswrapper -i net5416.inf**
inside the **xp32-6.0.3.85** directory !!!!!!
because the net5416.inf file is available inside that directory not your home!
doing so returned this:

ross@ross-hp:~/Desktop/xp32-7.6.0.239-whql$ sudo ndiswrapper -i net5416.inf
sudo: unable to resolve host ross-hp
couldn't open net5416.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219.

---

### Post by shafi on 2008-11-30
> **rwalker999 said:**
> doing so returned this:

ross@ross-hp:~/Desktop/xp32-7.6.0.239-whql$ sudo ndiswrapper -i net5416.inf
sudo: unable to resolve host ross-hp
couldn't open net5416.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219.

Then post the result of commands that **kevdog** wrote :
> 
kevdog  	
Re: Latest update made my wireless stop working
I'm confused about why you compiled madwifi and then want to use ndiswrapper? The two are different solutions.

Can you post the following:
lsmod | egrep '(ndis|ath)'
lshw -C network
lspci -nnm


---

### Post by rwalker999 on 2008-11-30
> **shafi said:**
> Then post the result of commands that **kevdog** wrote :
lsmod gave me this:
ath5k 106496 0
lbm_cw_mac80211 210728 1 ath5k
lbm_cw_cfg80211 39696 2 ath5k,lbm_cw_mac80211
led_class 12164 1 ath5k
ath_pci 99096 0
wlan 211952 1 ath_pci
ath_hal 198864 1 ath_pci


lshw gave me this:
WARNING: you should run this program as super-user.
*-network
description: Ethernet interface
product: MCP67 Ethernet
vendor: nVidia Corporation
physical id: a
bus info: pci@0000:00:0a.0
logical name: eth0
version: a2
serial: 00:1e:68:7f:07:00
width: 32 bits
clock: 66MHz
capabilities: bus_master cap_list ethernet physical
configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=192.168.1.9 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
*-network UNCLAIMED
description: Ethernet controller
product: AR242x 802.11abg Wireless PCI Express Adapter
vendor: Atheros Communications Inc.
physical id: 0
bus info: pci@0000:03:00.0
version: 01
width: 64 bits
clock: 33MHz
capabilities: cap_list
configuration: latency=0
*-network DISABLED
description: Ethernet interface
physical id: 1
logical name: pan0
serial: 8e:3c:c7:12:a2:32
capabilities: ethernet physical
configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes


and last, lspci -nnm returned this:
00:00.0 "RAM memory [0500]" "nVidia Corporation [10de]" "MCP67 Memory Controller [0547]" -ra2 "Hewlett-Packard Company [103c]" "Device [30cf]"
00:01.0 "ISA bridge [0601]" "nVidia Corporation [10de]" "MCP67 ISA Bridge [0548]" -ra2 "Hewlett-Packard Company [103c]" "Device [30cf]"
00:01.1 "SMBus [0c05]" "nVidia Corporation [10de]" "MCP67 SMBus [0542]" -ra2 "Hewlett-Packard Company [103c]" "Device [30cf]"
00:01.2 "RAM memory [0500]" "nVidia Corporation [10de]" "MCP67 Memory Controller [0541]" -ra2 "Hewlett-Packard Company [103c]" "Device [30cf]"
00:01.3 "Co-processor [0b40]" "nVidia Corporation [10de]" "MCP67 Co-processor [0543]" -ra2 "Hewlett-Packard Company [103c]" "Device [30cf]"
00:02.0 "USB Controller [0c03]" "nVidia Corporation [10de]" "MCP67 OHCI USB 1.1 Controller [055e]" -ra2 -p10 "Hewlett-Packard Company [103c]" "Device [30cf]"
00:02.1 "USB Controller [0c03]" "nVidia Corporation [10de]" "MCP67 EHCI USB 2.0 Controller [055f]" -ra2 -p20 "Hewlett-Packard Company [103c]" "Device [30cf]"
00:04.0 "USB Controller [0c03]" "nVidia Corporation [10de]" "MCP67 OHCI USB 1.1 Controller [055e]" -ra2 -p10 "Hewlett-Packard Company [103c]" "Device [30cf]"
00:04.1 "USB Controller [0c03]" "nVidia Corporation [10de]" "MCP67 EHCI USB 2.0 Controller [055f]" -ra2 -p20 "Hewlett-Packard Company [103c]" "Device [30cf]"
00:06.0 "IDE interface [0101]" "nVidia Corporation [10de]" "MCP67 IDE Controller [0560]" -ra1 -p8a "Unknown vendor [f03c]" "Device [30cf]"
00:07.0 "Audio device [0403]" "nVidia Corporation [10de]" "MCP67 High Definition Audio [055c]" -ra1 "Hewlett-Packard Company [103c]" "Device [30cf]"
00:08.0 "PCI bridge [0604]" "nVidia Corporation [10de]" "MCP67 PCI Bridge [0561]" -ra2 -p01 "" ""
00:09.0 "IDE interface [0101]" "nVidia Corporation [10de]" "MCP67 AHCI Controller [0550]" -ra2 -p85 "Hewlett-Packard Company [103c]" "Device [30cf]"
00:0a.0 "Ethernet controller [0200]" "nVidia Corporation [10de]" "MCP67 Ethernet [054c]" -ra2 "Hewlett-Packard Company [103c]" "Device [30cf]"
00:0c.0 "PCI bridge [0604]" "nVidia Corporation [10de]" "MCP67 PCI Express Bridge [0563]" -ra2 "" ""
00:0d.0 "PCI bridge [0604]" "nVidia Corporation [10de]" "MCP67 PCI Express Bridge [0563]" -ra2 "" ""
00:12.0 "VGA compatible controller [0300]" "nVidia Corporation [10de]" "GeForce 7150M [0531]" -ra2 "Hewlett-Packard Company [103c]" "Device [30cf]"
00:18.0 "Host bridge [0600]" "Advanced Micro Devices [AMD] [1022]" "K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1100]" "" ""
00:18.1 "Host bridge [0600]" "Advanced Micro Devices [AMD] [1022]" "K8 [Athlon64/Opteron] Address Map [1101]" "" ""
00:18.2 "Host bridge [0600]" "Advanced Micro Devices [AMD] [1022]" "K8 [Athlon64/Opteron] DRAM Controller [1102]" "" ""
00:18.3 "Host bridge [0600]" "Advanced Micro Devices [AMD] [1022]" "K8 [Athlon64/Opteron] Miscellaneous Control [1103]" "" ""
02:05.0 "FireWire (IEEE 1394) [0c00]" "Ricoh Co Ltd [1180]" "R5C832 IEEE 1394 Controller [0832]" -r05 -p10 "Hewlett-Packard Company [103c]" "Device [30cf]"
02:05.1 "SD Host controller [0805]" "Ricoh Co Ltd [1180]" "R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [0822]" -r22 "Hewlett-Packard Company [103c]" "Device [30cf]"
02:05.2 "System peripheral [0880]" "Ricoh Co Ltd [1180]" "R5C843 MMC Host Controller [0843]" -r12 "Hewlett-Packard Company [103c]" "Device [30cf]"
02:05.3 "System peripheral [0880]" "Ricoh Co Ltd [1180]" "R5C592 Memory Stick Bus Host Adapter [0592]" -r12 "Hewlett-Packard Company [103c]" "Device [30cf]"
02:05.4 "System peripheral [0880]" "Ricoh Co Ltd [1180]" "xD-Picture Card Controller [0852]" -rff -pff "" ""
03:00.0 "Ethernet controller [0200]" "Atheros Communications Inc. [168c]" "AR242x 802.11abg Wireless PCI Express Adapter [001c]" -r01 "Hewlett-Packard Company [103c]" "Device [137a]"

---

### Post by rwalker999 on 2008-11-30
Whoops, too many replies.  Sorry.

---

### Post by shafi on 2008-11-30
> **rwalker999 said:**
> lsmod gave me this:
ath5k 106496 0
lbm_cw_mac80211 210728 1 ath5k
..."

Ok try the links below, it should solve your problem :

[http://www.linuxquestions.org/questions/linux-hardware-18/atheros-ag5007ag-ubuntu-8.10-682038/](http://www.linuxquestions.org/questions/linux-hardware-18/atheros-ag5007ag-ubuntu-8.10-682038/)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/210900](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/210900)

[http://ubuntuforums.org/showthread.php?t=957697](http://ubuntuforums.org/showthread.php?t=957697)

---

### Post by rwalker999 on 2008-11-30
> **shafi said:**
> Ok try the links below, it should solve your problem :

[http://www.linuxquestions.org/questions/linux-hardware-18/atheros-ag5007ag-ubuntu-8.10-682038/](http://www.linuxquestions.org/questions/linux-hardware-18/atheros-ag5007ag-ubuntu-8.10-682038/)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/210900](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/210900)

[http://ubuntuforums.org/showthread.php?t=957697](http://ubuntuforums.org/showthread.php?t=957697)
linuxquestions.com - their suggestions gave me this:
ross@ross-hp:~$ sudo apt-get install linux-backports-drivers-intrepid
sudo: unable to resolve host ross-hp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-backports-drivers-intrepid

also, i was unable to add "ath5k" to my etc/modules file.
it said this: 
You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.  

Upon going to the properties of etc/modules, I'm told I'm not the owner, so I cannot change the permissions of the file.  Which means I can't save any changes to it.

The third link got me this reply from terminal:
ross@ross-hp:~$ sudo apt-get install linux-backports-modules-intrepid
sudo: unable to resolve host ross-hp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-backports-modules-intrepid is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


I'm going to try a reboot, hopefully something works....

Thanks again for all your help thus far.

---

### Post by rwalker999 on 2008-11-30
Got it working, thanks so much.

:-D

---

### Post by shafi on 2008-11-30
> **rwalker999 said:**
> linuxquestions.com - their suggestions gave me this:
ross@ross-hp:~$ sudo apt-get install linux-backports-drivers-intrepid
....

Uh,
You need to update once 

[HTML]sudo apt-get update[/HTML]
and if you get the update icon on your task bar, install all updates

after that you can install packages,

also check the System->admistration->Software sources

and check all the check boxes, then try the commands again.

---

### Post by shafi on 2008-11-30
> **rwalker999 said:**
> Got it working, thanks so much.

:-D

Vewwwwwwww , Finally !

Have fun ;)

---

### Post by kevdog on 2008-11-30
I found this website and it seems helpful:
[http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/](http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/)

Just remember -- the ath5k is a custom kernel module -- hence any time you upgrade, this custom kernel module is not going to be included in the new kernel -- and its your responsibility to add it back to the kernel.  The same would go for other custom kernel modules such as ndiswrapper.

---

### Post by HunterSBuntu on 2008-12-01
As stated above I believe this is because ath5k drivers are not included in the Ibex release and you have to install a backport driver package to add those modules to the kernel.

The problem is when you upgrade the kernel, it reverts to the default modules (which do not include ath5k)

This guide helped me get my Atheros 5XXX card working:
[https://help.ubuntu.com/community/AspireOne110L](https://help.ubuntu.com/community/AspireOne110L)

See the 'Wlan' section, the rest is specific to the Aspire One laptop.

Also, please mark the thread as Solved if your problem is now fixed.

---

