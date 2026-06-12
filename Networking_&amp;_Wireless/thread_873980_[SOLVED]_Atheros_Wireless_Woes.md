---
title: "[SOLVED] Atheros Wireless Woes"
date: 2008-07-29
forum: Networking &amp; Wireless
---

### Post by epiphonygirl on 2008-07-29
So, I've been mucking around on the forums for the last few days and have come up with nothing. My wired connection worked out of the box, but my wireless has never worked in Ubuntu and I really would like it to.  I have tried madwifi both manually and automated from [[COLOR="RoyalBlue"]here[/COLOR]]("http://www.stchman.com/ath_drv.html") and I have tried ndsi wrapper to use the drivers I use in windows with no luck once again, it says that the hardware is not present. Today, I just did a fresh load of Ubuntu to make sure that there wasn't something there that should not have been that would cause issues then I tried madwifi again and I still have no wireless. I saw this information listed on other forums and I hope that it can help someone help me :D

melissa@melissa-laptop:~$ iwlist
Usage: iwlist [interface] scanning [essid NNN] [last]
              [interface] frequency 
              [interface] channel 
              [interface] bitrate 
              [interface] rate 
              [interface] encryption 
              [interface] keys 
              [interface] power 
              [interface] txpower 
              [interface] retry 
              [interface] ap 
              [interface] accesspoints 
              [interface] peers 
              [interface] event 
              [interface] auth 
              [interface] wpakeys 
              [interface] genie 
              [interface] modulation 
melissa@melissa-laptop:~$ 

melissa@melissa-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1c:25:90:e3:07  
          inet addr:192.168.1.38  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:25ff:fe90:e307/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1709 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1581 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2114264 (2.0 MB)  TX bytes:242328 (236.6 KB)
          Interrupt:21 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:866 errors:0 dropped:0 overruns:0 frame:0
          TX packets:866 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:43300 (42.2 KB)  TX bytes:43300 (42.2 KB)

melissa@melissa-laptop:~$ 

melissa@melissa-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
[COLOR="Red"]03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)[/COLOR]
04:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
15:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b6)
melissa@melissa-laptop:~$

In my mucking around on the forums I found someone that has the same set up as I do on [[COLOR="RoyalBlue"]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=781382") thread, but they haven't solved the issue yet either. If you need any more information to help don't hesitate to ask and tell me how to get it, I'm still very new to Linux in general. Any help would be great.

Thank you!

---

### Post by Kevbert on 2008-07-29
Please take a look at [[COLOR="Red"]this[/COLOR]]("http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html").  Getting the Atheros AR242x wireless seems to be a bit hit or miss.

---

### Post by pytheas22 on 2008-07-29
I think you need to use ndiswrapper for that card, as some quick Google searches indicate that madwifi probably doesn't yet support your type of Atheros chipset (if madwifi did support it, it would "just work" out-of-the-box in Ubuntu, because madwifi is already preinstalled).

So you need to use ndiswrapper.  The reason that ndiswrapper may not have worked before is that you didn't blacklist madwifi--it will still try to control the card, and prevent ndiswrapper from working, even if it doesn't support it.  So open up the blacklist:
```

sudo gedit /etc/modprobe.d/blacklist
```

and add these lines to the bottom:
```

blacklist ath_pci
blacklist ath_rate_sample
blacklist ath_hal
```

then save the file.

Next, install ndiswrapper:
```

sudo apt-get install ndiswrapper* ndisgtk
```

When it's finished installing, open up the ndiswrapper GUI and use it to install the Windows drivers:
```

sudo ndisgtk
```

**if you're using 64-bit Ubuntu, the Windows drivers that you install also need to be built for a 64-bit system.  If you need win64 drivers and aren't sure where to find them or which .inf file to select, ask**

Now reboot and, in principle, your wireless should work.  If it doesn't, please post the output of these commands:
```

ndiswrapper -l
dmesg
```

(dmesg will be long, but please post it all).

---

### Post by chili555 on 2008-07-29
While the process is the same, I suggest this newer package instead: [http://snapshots.madwifi.org/madwifi-hal-0.10.5.6-current.tar.gz](http://snapshots.madwifi.org/madwifi-hal-0.10.5.6-current.tar.gz)

---

### Post by epiphonygirl on 2008-07-29
Thank you for all of the suggestions, I will give them all a try tomorrow afternoon and let everyone know what works and if my problem has been solved.

---

### Post by epiphonygirl on 2008-07-29
Yeah, that didn't work. Here are the outputs that you requested:

melissa@melissa-laptop:~$ ndiswrapper -l
net5416 : driver installed
melissa@melissa-laptop:~$ 

and 

[   19.023579] console [tty0] enabled
[   19.023920] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   19.024204] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   19.063154] Memory: 1538212k/1563456k available (2079k kernel code, 24108k reserved, 973k data, 364k init, 645952k highmem)
[   19.063160] virtual kernel memory layout:
[   19.063161]     fixmap  : 0xfffa6000 - 0xfffff000   ( 356 kB)
[   19.063162]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   19.063163]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   19.063164]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   19.063165]       .init : 0xc03fe000 - 0xc0459000   ( 364 kB)
[   19.063166]       .data : 0xc0307d94 - 0xc03fb3a4   ( 973 kB)
[   19.063167]       .text : 0xc0100000 - 0xc0307d94   (2079 kB)
[   19.063170] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   19.063214] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   19.063359] hpet clockevent registered
[   19.143231] Calibrating delay using timer specific routine.. 3729.76 BogoMIPS (lpj=7459529)
[   19.143252] Security Framework initialized
[   19.143259] SELinux:  Disabled at boot.
[   19.143270] AppArmor: AppArmor initialized
[   19.143274] Failure registering capabilities with primary security module.
[   19.143280] Mount-cache hash table entries: 512
[   19.143384] Initializing cgroup subsys ns
[   19.143390] Initializing cgroup subsys cpuacct
[   19.143399] CPU: After generic identify, caps: afebfbff 20100000 00000000 00000000 0000e31d 00000000 00000001 00000000
[   19.143404] monitor/mwait feature present.
[   19.143405] using mwait in idle threads.
[   19.143409] CPU: L1 I cache: 32K, L1 D cache: 32K
[   19.143411] CPU: L2 cache: 1024K
[   19.143413] CPU: After all inits, caps: afebfbff 20100000 00000000 00003940 0000e31d 00000000 00000001 00000000
[   19.143420] Compat vDSO mapped to ffffe000.
[   19.143430] CPU: Intel(R) Celeron(R) CPU          540  @ 1.86GHz stepping 01
[   19.143435] Checking 'hlt' instruction... OK.
[   19.160607] Freeing SMP alternatives: 0k freed
[   19.160698] Early unpacking initramfs... done
[   19.468697] ACPI: Core revision 20070126
[   19.468751] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   19.506263] ENABLING IO-APIC IRQs
[   19.506464] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   19.650456] net_namespace: 64 bytes
[   19.650463] Booting paravirtualized kernel on bare hardware
[   19.650871] Time: 22:46:47  Date: 07/29/08
[   19.650888] NET: Registered protocol family 16
[   19.651030] EISA bus registered
[   19.651034] ACPI: bus type pci registered
[   19.651548] PCI: PCI BIOS revision 3.00 entry at 0xfde37, last bus=24
[   19.651550] PCI: Using configuration type 1
[   19.651558] Setting up standard PCI resources
[   19.654798] ACPI: EC: EC description table is found, configuring boot EC
[   19.658644] ACPI: BIOS _OSI(Linux) query honored via DMI
[   19.659270] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   19.735394] ACPI: Interpreter enabled
[   19.735397] ACPI: (supports S0 S3 S4 S5)
[   19.735409] ACPI: Using IOAPIC for interrupt routing
[   19.740399] ACPI: EC: GPE = 0x12, I/O: command/status = 0x66, data = 0x62
[   19.740402] ACPI: EC: driver started in poll mode
[   19.740526] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   19.742522] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[   19.742529] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[   19.744500] PCI: Transparent bridge - 0000:00:1e.0
[   19.744660] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   19.744821] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP0._PRT]
[   19.744928] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
[   19.745034] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]
[   19.745142] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[   19.747750] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 *10 11)
[   19.747939] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11)
[   19.748123] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11)
[   19.748307] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11)
[   19.748491] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11)
[   19.748673] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11)
[   19.748857] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 *11)
[   19.749040] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11)
[   19.749207] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   19.749339] ACPI: Power Resource [PUBS] (on)
[   19.749386] Linux Plug and Play Support v0.97 (c) Adam Belay
[   19.749410] pnp: PnP ACPI init
[   19.749416] ACPI: bus type pnp registered
[   19.750490] pnpacpi: exceeded the max number of mem resources: 12
[   19.751479] pnp: PnP ACPI: found 10 devices
[   19.751481] ACPI: ACPI bus type pnp unregistered
[   19.751484] PnPBIOS: Disabled by ACPI PNP
[   19.751651] PCI: Using ACPI for IRQ routing
[   19.751653] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   19.981808] NET: Registered protocol family 8
[   19.981809] NET: Registered protocol family 20
[   19.981841] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   19.981844] hpet0: 3 64-bit timers, 14318180 Hz
[   19.982875] AppArmor: AppArmor Filesystem Enabled
[   19.985771] Time: tsc clocksource has been installed.
[   19.985780] Switched to high resolution mode on CPU 0
[   19.993760] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[   19.993762] system 00:00: iomem range 0xc0000-0xc3fff could not be reserved
[   19.993764] system 00:00: iomem range 0xc4000-0xc7fff could not be reserved
[   19.993767] system 00:00: iomem range 0xc8000-0xcbfff has been reserved
[   19.993769] system 00:00: iomem range 0xcc000-0xcffff has been reserved
[   19.993771] system 00:00: iomem range 0xd0000-0xd3fff could not be reserved
[   19.993773] system 00:00: iomem range 0x0-0x0 could not be reserved
[   19.993775] system 00:00: iomem range 0x0-0x0 could not be reserved
[   19.993777] system 00:00: iomem range 0x0-0x0 could not be reserved
[   19.993779] system 00:00: iomem range 0xe0000-0xe3fff has been reserved
[   19.993781] system 00:00: iomem range 0xe4000-0xe7fff has been reserved
[   19.993784] system 00:00: iomem range 0xe8000-0xebfff has been reserved
[   19.993789] system 00:02: ioport range 0x164e-0x164f has been reserved
[   19.993791] system 00:02: ioport range 0x1000-0x107f has been reserved
[   19.993793] system 00:02: ioport range 0x1180-0x11bf has been reserved
[   19.993795] system 00:02: ioport range 0x800-0x80f has been reserved
[   19.993798] system 00:02: ioport range 0x15e0-0x15ef has been reserved
[   19.993800] system 00:02: ioport range 0x1600-0x165f could not be reserved
[   19.993802] system 00:02: iomem range 0xf0000000-0xf3ffffff could not be reserved
[   19.993806] system 00:02: iomem range 0xfed1c000-0xfed1ffff could not be reserved
[   19.993808] system 00:02: iomem range 0xfed14000-0xfed17fff could not be reserved
[   19.993810] system 00:02: iomem range 0xfed18000-0xfed18fff could not be reserved
[   19.993813] system 00:02: iomem range 0xfed19000-0xfed19fff could not be reserved
[   19.993815] system 00:02: iomem range 0xfed45000-0xfed4bfff could not be reserved
[   19.993818] system 00:02: iomem range 0xfed40000-0xfed44fff could not be reserved
[   20.024119] PCI: Bridge: 0000:00:1c.0
[   20.024124]   IO window: 2000-2fff
[   20.024134]   MEM window: f4000000-f5ffffff
[   20.024143]   PREFETCH window: f8600000-f86fffff
[   20.024155] PCI: Bridge: 0000:00:1c.1
[   20.024160]   IO window: 3000-3fff
[   20.024170]   MEM window: f6000000-f7ffffff
[   20.024178]   PREFETCH window: f8700000-f87fffff
[   20.024190] PCI: Bridge: 0000:00:1c.2
[   20.024191]   IO window: disabled.
[   20.024199]   MEM window: f8200000-f82fffff
[   20.024207]   PREFETCH window: disabled.
[   20.024220] PCI: Bus 22, cardbus bridge: 0000:15:00.0
[   20.024222]   IO window: 00004000-000040ff
[   20.024229]   IO window: 00004400-000044ff
[   20.024238]   PREFETCH window: d8000000-dbffffff
[   20.024247]   MEM window: 70000000-73ffffff
[   20.024255] PCI: Bridge: 0000:00:1e.0
[   20.024260]   IO window: 4000-7fff
[   20.024270]   MEM window: d4000000-d7efffff
[   20.024278]   PREFETCH window: d8000000-dbffffff
[   20.024345] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 20 (level, low) -> IRQ 16
[   20.024355] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   20.024411] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 21 (level, low) -> IRQ 17
[   20.024418] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   20.024471] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 22 (level, low) -> IRQ 18
[   20.024479] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   20.024503] PCI: Enabling device 0000:00:1e.0 (0005 -> 0007)
[   20.024516] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   20.024547] ACPI: PCI Interrupt 0000:15:00.0[A] -> GSI 16 (level, low) -> IRQ 19
[   20.024555] PCI: Setting latency timer of device 0000:15:00.0 to 64
[   20.024566] NET: Registered protocol family 2
[   20.061655] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   20.061849] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   20.062340] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[   20.062512] TCP: Hash tables configured (established 131072 bind 65536)
[   20.062515] TCP reno registered
[   20.073723] checking if image is initramfs... it is
[   20.675373] Freeing initrd memory: 7230k freed
[   20.675526] Simple Boot Flag at 0x35 set to 0x1
[   20.675912] audit: initializing netlink socket (disabled)
[   20.675926] audit(1217371607.308:1): initialized
[   20.676064] highmem bounce pool size: 64 pages
[   20.677535] VFS: Disk quotas dquot_6.5.1
[   20.677553] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   20.677662] io scheduler noop registered
[   20.677664] io scheduler anticipatory registered
[   20.677665] io scheduler deadline registered
[   20.677674] io scheduler cfq registered (default)
[   20.677686] Boot video device is 0000:00:02.0
[   20.677961] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   20.678107] assign_interrupt_mode Found MSI capability
[   20.678220] Allocate Port Service[0000:00:1c.0:pcie00]
[   20.678248] Allocate Port Service[0000:00:1c.0:pcie02]
[   20.678437] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   20.678578] assign_interrupt_mode Found MSI capability
[   20.678687] Allocate Port Service[0000:00:1c.1:pcie00]
[   20.678712] Allocate Port Service[0000:00:1c.1:pcie02]
[   20.678901] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   20.679038] assign_interrupt_mode Found MSI capability
[   20.679146] Allocate Port Service[0000:00:1c.2:pcie00]
[   20.679171] Allocate Port Service[0000:00:1c.2:pcie02]
[   20.679446] isapnp: Scanning for PnP cards...
[   21.037242] isapnp: No Plug & Play device found
[   21.058208] hpet_resources: 0xfed00000 is busy
[   21.058235] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   21.059206] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   21.059263] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   21.059337] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[   21.070985] serio: i8042 KBD port at 0x60,0x64 irq 1
[   21.070988] serio: i8042 AUX port at 0x60,0x64 irq 12
[   21.071958] mice: PS/2 mouse device common for all mice
[   21.072042] EISA: Probing bus 0 at eisa.0
[   21.072051] Cannot allocate resource for EISA slot 1
[   21.072053] Cannot allocate resource for EISA slot 2
[   21.072054] Cannot allocate resource for EISA slot 3
[   21.072056] Cannot allocate resource for EISA slot 4
[   21.072057] Cannot allocate resource for EISA slot 5
[   21.072059] Cannot allocate resource for EISA slot 6
[   21.072060] Cannot allocate resource for EISA slot 7
[   21.072068] EISA: Detected 0 cards.
[   21.072071] cpuidle: using governor ladder
[   21.072177] NET: Registered protocol family 1
[   21.072203] Using IPI Shortcut mode
[   21.072229] registered taskstats version 1
[   21.072333]   Magic number: 0:756:806
[   21.072382]   hash matches device ptys0
[   21.072409] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   21.072410] EDD information not available.
[   21.072589] Freeing unused kernel memory: 364k freed
[   21.077642] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   22.263193] fuse init (API version 7.9)
[   22.282145] Monitor-Mwait will be used to enter C-1 state
[   22.282148] Monitor-Mwait will be used to enter C-2 state
[   22.282150] Monitor-Mwait will be used to enter C-3 state
[   22.282244] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   22.282247] ACPI: Processor [CPU0] (supports 8 throttling states)
[   22.284090] ACPI: Thermal Zone [THM0] (48 C)
[   22.285526] ACPI: Thermal Zone [THM1] (47 C)
[   22.824876] usbcore: registered new interface driver usbfs
[   22.824896] usbcore: registered new interface driver hub
[   22.830358] usbcore: registered new device driver usb
[   22.831294] USB Universal Host Controller Interface driver v3.0
[   22.831341] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 20 (level, low) -> IRQ 16
[   22.831355] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[   22.831360] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[   22.831586] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[   22.831630] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001820
[   22.831751] usb usb1: configuration #1 chosen from 1 choice
[   22.831770] hub 1-0:1.0: USB hub found
[   22.831773] hub 1-0:1.0: 2 ports detected
[   22.932734] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 17
[   22.932750] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[   22.932756] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[   22.932774] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[   22.932818] uhci_hcd 0000:00:1a.1: irq 17, io base 0x00001840
[   22.932918] usb usb2: configuration #1 chosen from 1 choice
[   22.932937] hub 2-0:1.0: USB hub found
[   22.932940] hub 2-0:1.0: 2 ports detected
[   22.963549] SCSI subsystem initialized
[   23.025682] libata version 3.00 loaded.
[   23.036542] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 19
[   23.036558] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   23.036564] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   23.036585] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 3
[   23.036626] uhci_hcd 0000:00:1d.0: irq 19, io base 0x00001860
[   23.036725] usb usb3: configuration #1 chosen from 1 choice
[   23.036743] hub 3-0:1.0: USB hub found
[   23.036747] hub 3-0:1.0: 2 ports detected
[   23.140369] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 20
[   23.140385] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   23.140390] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   23.140410] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 4
[   23.140452] uhci_hcd 0000:00:1d.1: irq 20, io base 0x00001880
[   23.140552] usb usb4: configuration #1 chosen from 1 choice
[   23.140570] hub 4-0:1.0: USB hub found
[   23.140575] hub 4-0:1.0: 2 ports detected
[   23.244191] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 21
[   23.244207] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   23.244212] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   23.244232] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 5
[   23.244272] uhci_hcd 0000:00:1d.2: irq 21, io base 0x000018a0
[   23.244372] usb usb5: configuration #1 chosen from 1 choice
[   23.244390] hub 5-0:1.0: USB hub found
[   23.244394] hub 5-0:1.0: 2 ports detected
[   23.349288] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 22 (level, low) -> IRQ 18
[   23.349303] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[   23.349307] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[   23.349339] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 6
[   23.353270] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
[   23.353281] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xf8504800
[   23.367873] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   23.367972] usb usb6: configuration #1 chosen from 1 choice
[   23.367992] hub 6-0:1.0: USB hub found
[   23.367997] hub 6-0:1.0: 4 ports detected
[   23.472020] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 19 (level, low) -> IRQ 22
[   23.472040] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   23.472046] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   23.472069] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
[   23.475984] ehci_hcd 0000:00:1d.7: debug port 1
[   23.475997] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   23.476007] ehci_hcd 0000:00:1d.7: irq 22, io mem 0xf8504c00
[   23.491663] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   23.491765] usb usb7: configuration #1 chosen from 1 choice
[   23.491785] hub 7-0:1.0: USB hub found
[   23.491790] hub 7-0:1.0: 6 ports detected
[   23.595656] tg3.c:v3.86 (November 9, 2007)
[   23.595741] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 18 (level, low) -> IRQ 21
[   23.595762] PCI: Setting latency timer of device 0000:04:00.0 to 64
[   23.859011] Clocksource tsc unstable (delta = -4585066002 ns)
[   23.863014] Time: hpet clocksource has been installed.
[   23.869819] eth0: Tigon3 [partno(BCM95751) rev b002 PHY(5787)] (PCI Express) 10/100/1000Base-T Ethernet 00:1c:25:90:e3:07
[   23.869824] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[1] TSOcap[1]
[   23.869827] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[   23.870063] ACPI: PCI Interrupt 0000:00:1f.1[C] -> GSI 16 (level, low) -> IRQ 19
[   23.870104] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   23.870121] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
[   23.875417] ata_piix 0000:00:1f.1: version 2.12
[   23.875435] ACPI: PCI Interrupt 0000:00:1f.1[C] -> GSI 16 (level, low) -> IRQ 19
[   23.875471] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   23.876207] scsi0 : ata_piix
[   23.876565] scsi1 : ata_piix
[   23.876925] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[   23.876927] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[   23.891373] ata1.00: ATAPI: HL-DT-STCD-RW/DVD DRIVE GCC-T10N, 1.04, max UDMA/33
[   23.898422] ata1.00: configured for UDMA/33
[   23.898492] ata2: port disabled. ignoring.
[   23.901581] scsi 0:0:0:0: CD-ROM            HL-DT-ST RW/DVD GCC-T10N  1.04 PQ: 0 ANSI: 5
[   23.901914] ahci 0000:00:1f.2: version 3.0
[   23.901962] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 16 (level, low) -> IRQ 19
[   23.902050] ahci 0000:00:1f.2: nr_ports (3) and implemented port map (0x1) don't match, using nr_ports
[   23.902052] ahci 0000:00:1f.2: forcing PORTS_IMPL to 0x7
[   23.907506] Driver 'sr' needs updating - please use bus_type methods
[   23.913880] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[   23.913883] Uniform CD-ROM driver Revision: 3.20
[   23.913925] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   23.917218] sr 0:0:0:0: Attached scsi generic sg0 type 5
[   23.975983] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 1.5 Gbps 0x7 impl SATA mode
[   23.975986] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part 
[   23.975996] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   23.976204] scsi2 : ahci
[   23.976415] scsi3 : ahci
[   23.976534] scsi4 : ahci
[   23.976599] ata3: SATA max UDMA/133 abar m2048@0xf8504000 port 0xf8504100 irq 220
[   23.976604] ata4: SATA max UDMA/133 abar m2048@0xf8504000 port 0xf8504180 irq 220
[   23.976609] ata5: SATA max UDMA/133 abar m2048@0xf8504000 port 0xf8504200 irq 220
[   23.994036] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   24.005753] ata3.00: ATA-7: WDC WD800BEVS-08RST2, 08.01G08, max UDMA/133
[   24.005756] ata3.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 31/32)
[   24.006116] ata3.00: configured for UDMA/133
[   24.017021] ata4: SATA link down (SStatus 0 SControl 0)
[   24.027957] ata5: SATA link down (SStatus 0 SControl 0)
[   24.028062] scsi 2:0:0:0: Direct-Access     ATA      WDC WD800BEVS-08 08.0 PQ: 0 ANSI: 5
[   24.028124] scsi 2:0:0:0: Attached scsi generic sg1 type 0
[   24.034963] Driver 'sd' needs updating - please use bus_type methods
[   24.037633] sd 2:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   24.037644] sd 2:0:0:0: [sda] Write Protect is off
[   24.037646] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   24.037659] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   24.037701] sd 2:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   24.037708] sd 2:0:0:0: [sda] Write Protect is off
[   24.037709] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   24.037721] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   24.037723]  sda: sda1 sda2
[   24.039151] sd 2:0:0:0: [sda] Attached SCSI disk
[   24.229425] loop: module loaded
[   24.247175] kjournald starting.  Commit interval 5 seconds
[   24.247190] EXT3-fs: mounted filesystem with ordered data mode.
[   28.323237] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   28.349186] Real Time Clock Driver v1.12ac
[   29.152296] Linux agpgart interface v0.102
[   29.192661] agpgart: Detected an Intel 965GM Chipset.
[   29.192963] agpgart: Detected 7676K stolen memory.
[   29.206962] agpgart: AGP aperture is 256M @ 0xe0000000
[   29.224491] Non-volatile memory driver v1.2
[   29.261580] thinkpad_acpi: ThinkPad ACPI Extras v0.17
[   29.261583] thinkpad_acpi: [http://ibm-acpi.sf.net/](http://ibm-acpi.sf.net/)
[   29.261584] thinkpad_acpi: ThinkPad BIOS 7PETB2WW (2.12 ), EC 7KHT24WW-1.08
[   29.261586] thinkpad_acpi: Lenovo ThinkPad R61e
[   29.262077] thinkpad_acpi: radio switch found; radios are enabled
[   29.267246] thinkpad_acpi: standard ACPI backlight interface available, not loading native one...
[   29.267521] input: ThinkPad Extra Buttons as /devices/virtual/input/input3
[   29.277349] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   29.281841] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   29.286457] iTCO_vendor_support: vendor-support=0
[   29.287826] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   29.287918] iTCO_wdt: Found a ICH8M TCO device (Version=2, TCOBASE=0x1060)
[   29.287961] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   29.480233] input: Power Button (FF) as /devices/virtual/input/input4
[   29.512027] ACPI: Power Button (FF) [PWRF]
[   29.512099] input: Lid Switch as /devices/virtual/input/input5
[   29.529874] ACPI: Lid Switch [LID]
[   29.529947] input: Sleep Button (CM) as /devices/virtual/input/input6
[   29.555985] ACPI: Sleep Button (CM) [SLPB]
[   29.865276] Yenta: CardBus bridge found at 0000:15:00.0 [17aa:20c4]
[   29.991980] Yenta: ISA IRQ mask 0x0cb8, PCI irq 19
[   29.991987] Socket status: 30000006
[   29.991990] pcmcia: parent PCI bridge I/O window: 0x4000 - 0x7fff
[   29.991992] cs: IO port probe 0x4000-0x7fff: clean.
[   29.992741] pcmcia: parent PCI bridge Memory window: 0xd4000000 - 0xd7efffff
[   29.992743] pcmcia: parent PCI bridge Memory window: 0xd8000000 - 0xdbffffff
[   30.196231] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input7
[   30.221110] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   30.222915] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:05/LNXVIDEO:01/input/input8
[   30.248607] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
[   30.479818] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   30.496550] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/input/input9
[   30.517336] ath_hal: module license 'Proprietary' taints kernel.
[   30.528068] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   30.686631] wlan: 0.9.4
[   30.712781] ath_pci: 0.9.4
[   30.712883] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 20
[   30.712927] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   30.761452] wifi%d: unable to attach hardware: 'Hardware revision not supported' (HAL status 13)
[   30.761468] ACPI: PCI interrupt for device 0000:03:00.0 disabled
[   30.886919] ACPI: AC Adapter [AC] (on-line)
[   31.046550] ACPI: Battery Slot [BAT0] (battery present)
[   32.734305] cs: IO port probe 0x100-0x3af: clean.
[   32.736683] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   32.737669] cs: IO port probe 0x820-0x8ff: clean.
[   32.738490] cs: IO port probe 0xc00-0xcf7: clean.
[   32.739458] cs: IO port probe 0xa00-0xaff: clean.
[   33.737789] lp: driver loaded but no devices found
[   33.971462] EXT3 FS on loop0, internal journal
[   42.510138] Adding 976552k swap on /host/ubuntu/disks/swap.disk.  Priority:-1 extents:1 across:976552k
[   42.748043] ip_tables: (C) 2000-2006 Netfilter Core Team
[   42.970148] No dock devices found.
[   43.547249] apm: BIOS not found.
[   43.598837] ppdev: user-space parallel port driver
[   43.639049] audit(1217389656.039:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4855 profile="/usr/sbin/cupsd" namespace="default"
[   43.720309] input: /usr/sbin/thinkpad-keys as /devices/virtual/input/input10
[   44.325355] Bluetooth: Core ver 2.11
[   44.326992] NET: Registered protocol family 31
[   44.326995] Bluetooth: HCI device and connection manager initialized
[   44.326998] Bluetooth: HCI socket layer initialized
[   44.334739] Bluetooth: L2CAP ver 2.9
[   44.334743] Bluetooth: L2CAP socket layer initialized
[   44.393602] Bluetooth: RFCOMM socket layer initialized
[   44.393615] Bluetooth: RFCOMM TTY layer initialized
[   44.393616] Bluetooth: RFCOMM ver 1.8
[   44.611274] tg3: eth0: Link is up at 100 Mbps, full duplex.
[   44.611277] tg3: eth0: Flow control is off for TX and off for RX.
[   45.643468] [drm] Initialized drm 1.1.0 20060810
[   45.647822] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 19
[   45.647829] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   45.647883] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   46.027665] NET: Registered protocol family 17
[   46.315728] NET: Registered protocol family 10
[   46.316095] lo: Disabled Privacy Extensions
[   48.773338] eth0: no IPv6 routers present
melissa@melissa-laptop:~$

---

### Post by pytheas22 on 2008-07-30
Thanks for all of that information.  First of all, as you mentioned in your first post, ndiswrapper still doesn't seem to detect the presence of the hardware; otherwise ndiswrapper -l would yield:
```

driver installed, device present
```

You may want to try removing the Windows driver that you currently have installed and installing a different version instead--for instance, if you installed the Windows XP version, try using Windows 2000; or download a different release of the driver from the Internet.  Sometimes it's the case that certain versions of the Windows drivers don't work.

The second problem is that the system still seems to be loading the madwifi driver instead of ndiswrapper:
[B]
```
[ 30.712781] ath_pci: 0.9.4[/B]
```

Make sure the line "blacklist ath_pci" is in /etc/modprobe.d/blacklist.  If it is, try this:
```

sudo rmmod ath_pci
sudo modprobe ndiswrapper
```

does the system recognize your wireless card now (provided the issue with ndiswrapper not detecting the hardware has been resolved)?

Beyond all of the above, you may also want to try compiling madwifi again by following the instructions [here]("http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html") (which someone else already mentioned) under the section for i386 users (because you are on 32-bit, right?).  Apparently your card is supported by madwifi if you use the latest release.  If you do follow those instructions, remember that you'll need to remove the lines:
```

blacklist ath_pci
blacklist ath_hal
blacklist ath_rate_sample
```

from /etc/modprobe.d/blacklist and replace them with:
```

blacklist ndiswrapper
```

and restart your system for the blacklisting to take effect.

Please let us know if any of the above helps.

---

### Post by epiphonygirl on 2008-07-30
Ok, so I tried what you said to do with ndis wrapper and now it recognizes that the hardware is present, but in network there is no option for wireless and I have no idea where to go from there...shouldn't it have just appeared? Also in hardware drivers I now see that the wireless adapter says enabled but not in use. I think I'm going to give madwifi one more try in the mean time I'll post current readouts for ndiswrapper -l and dmesg:

melissa@melissa-laptop:~$ ndiswrapper -l
net5211 : driver installed
	device (168C:001C) present (alternate driver: ath_pci)
melissa@melissa-laptop:~$ 


[   19.906639] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   19.944807] ENABLING IO-APIC IRQs
[   19.945003] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   20.092510] net_namespace: 64 bytes
[   20.092517] Booting paravirtualized kernel on bare hardware
[   20.092923] Time: 17:59:44  Date: 07/30/08
[   20.092942] NET: Registered protocol family 16
[   20.093084] EISA bus registered
[   20.093088] ACPI: bus type pci registered
[   20.093602] PCI: PCI BIOS revision 3.00 entry at 0xfde37, last bus=24
[   20.093604] PCI: Using configuration type 1
[   20.093612] Setting up standard PCI resources
[   20.096879] ACPI: EC: EC description table is found, configuring boot EC
[   20.100731] ACPI: BIOS _OSI(Linux) query honored via DMI
[   20.101344] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   20.177635] ACPI: Interpreter enabled
[   20.177638] ACPI: (supports S0 S3 S4 S5)
[   20.177650] ACPI: Using IOAPIC for interrupt routing
[   20.182598] ACPI: EC: GPE = 0x12, I/O: command/status = 0x66, data = 0x62
[   20.182600] ACPI: EC: driver started in poll mode
[   20.182724] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   20.184728] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[   20.184735] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[   20.186556] PCI: Transparent bridge - 0000:00:1e.0
[   20.186711] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   20.186872] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP0._PRT]
[   20.186979] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
[   20.187085] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]
[   20.187193] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[   20.189801] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 *10 11)
[   20.189990] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11)
[   20.190174] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11)
[   20.190358] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11)
[   20.190542] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11)
[   20.190725] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11)
[   20.190908] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 *11)
[   20.191091] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11)
[   20.191246] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   20.191345] ACPI: Power Resource [PUBS] (on)
[   20.191393] Linux Plug and Play Support v0.97 (c) Adam Belay
[   20.191417] pnp: PnP ACPI init
[   20.191423] ACPI: bus type pnp registered
[   20.192499] pnpacpi: exceeded the max number of mem resources: 12
[   20.193481] pnp: PnP ACPI: found 10 devices
[   20.193484] ACPI: ACPI bus type pnp unregistered
[   20.193487] PnPBIOS: Disabled by ACPI PNP
[   20.193657] PCI: Using ACPI for IRQ routing
[   20.193659] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   20.423872] NET: Registered protocol family 8
[   20.423874] NET: Registered protocol family 20
[   20.423905] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   20.423909] hpet0: 3 64-bit timers, 14318180 Hz
[   20.424940] AppArmor: AppArmor Filesystem Enabled
[   20.427836] Time: tsc clocksource has been installed.
[   20.427855] Switched to high resolution mode on CPU 0
[   20.435827] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[   20.435829] system 00:00: iomem range 0xc0000-0xc3fff could not be reserved
[   20.435831] system 00:00: iomem range 0xc4000-0xc7fff could not be reserved
[   20.435834] system 00:00: iomem range 0xc8000-0xcbfff has been reserved
[   20.435836] system 00:00: iomem range 0xcc000-0xcffff has been reserved
[   20.435838] system 00:00: iomem range 0xd0000-0xd3fff could not be reserved
[   20.435840] system 00:00: iomem range 0x0-0x0 could not be reserved
[   20.435842] system 00:00: iomem range 0x0-0x0 could not be reserved
[   20.435844] system 00:00: iomem range 0x0-0x0 could not be reserved
[   20.435846] system 00:00: iomem range 0xe0000-0xe3fff has been reserved
[   20.435848] system 00:00: iomem range 0xe4000-0xe7fff has been reserved
[   20.435851] system 00:00: iomem range 0xe8000-0xebfff has been reserved
[   20.435856] system 00:02: ioport range 0x164e-0x164f has been reserved
[   20.435858] system 00:02: ioport range 0x1000-0x107f has been reserved
[   20.435860] system 00:02: ioport range 0x1180-0x11bf has been reserved
[   20.435862] system 00:02: ioport range 0x800-0x80f has been reserved
[   20.435864] system 00:02: ioport range 0x15e0-0x15ef has been reserved
[   20.435867] system 00:02: ioport range 0x1600-0x165f could not be reserved
[   20.435869] system 00:02: iomem range 0xf0000000-0xf3ffffff could not be reserved
[   20.435872] system 00:02: iomem range 0xfed1c000-0xfed1ffff could not be reserved
[   20.435874] system 00:02: iomem range 0xfed14000-0xfed17fff could not be reserved
[   20.435877] system 00:02: iomem range 0xfed18000-0xfed18fff could not be reserved
[   20.435879] system 00:02: iomem range 0xfed19000-0xfed19fff could not be reserved
[   20.435882] system 00:02: iomem range 0xfed45000-0xfed4bfff could not be reserved
[   20.435884] system 00:02: iomem range 0xfed40000-0xfed44fff could not be reserved
[   20.466181] PCI: Bridge: 0000:00:1c.0
[   20.466186]   IO window: 2000-2fff
[   20.466198]   MEM window: f4000000-f5ffffff
[   20.466207]   PREFETCH window: f8600000-f86fffff
[   20.466219] PCI: Bridge: 0000:00:1c.1
[   20.466224]   IO window: 3000-3fff
[   20.466232]   MEM window: f6000000-f7ffffff
[   20.466240]   PREFETCH window: f8700000-f87fffff
[   20.466252] PCI: Bridge: 0000:00:1c.2
[   20.466253]   IO window: disabled.
[   20.466265]   MEM window: f8200000-f82fffff
[   20.466274]   PREFETCH window: disabled.
[   20.466288] PCI: Bus 22, cardbus bridge: 0000:15:00.0
[   20.466290]   IO window: 00004000-000040ff
[   20.466299]   IO window: 00004400-000044ff
[   20.466308]   PREFETCH window: d8000000-dbffffff
[   20.466315]   MEM window: 70000000-73ffffff
[   20.466323] PCI: Bridge: 0000:00:1e.0
[   20.466327]   IO window: 4000-7fff
[   20.466337]   MEM window: d4000000-d7efffff
[   20.466346]   PREFETCH window: d8000000-dbffffff
[   20.466412] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 20 (level, low) -> IRQ 16
[   20.466423] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   20.466476] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 21 (level, low) -> IRQ 17
[   20.466481] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   20.466529] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 22 (level, low) -> IRQ 18
[   20.466536] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   20.466561] PCI: Enabling device 0000:00:1e.0 (0005 -> 0007)
[   20.466573] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   20.466605] ACPI: PCI Interrupt 0000:15:00.0[A] -> GSI 16 (level, low) -> IRQ 19
[   20.466613] PCI: Setting latency timer of device 0000:15:00.0 to 64
[   20.466624] NET: Registered protocol family 2
[   20.503715] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   20.503908] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   20.504405] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[   20.504578] TCP: Hash tables configured (established 131072 bind 65536)
[   20.504580] TCP reno registered
[   20.515785] checking if image is initramfs... it is
[   21.117390] Freeing initrd memory: 7230k freed
[   21.117544] Simple Boot Flag at 0x35 set to 0x1
[   21.117929] audit: initializing netlink socket (disabled)
[   21.117942] audit(1217440784.308:1): initialized
[   21.118080] highmem bounce pool size: 64 pages
[   21.119555] VFS: Disk quotas dquot_6.5.1
[   21.119574] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   21.119682] io scheduler noop registered
[   21.119684] io scheduler anticipatory registered
[   21.119685] io scheduler deadline registered
[   21.119694] io scheduler cfq registered (default)
[   21.119706] Boot video device is 0000:00:02.0
[   21.119983] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   21.120120] assign_interrupt_mode Found MSI capability
[   21.120229] Allocate Port Service[0000:00:1c.0:pcie00]
[   21.120257] Allocate Port Service[0000:00:1c.0:pcie02]
[   21.120436] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   21.120578] assign_interrupt_mode Found MSI capability
[   21.120685] Allocate Port Service[0000:00:1c.1:pcie00]
[   21.120710] Allocate Port Service[0000:00:1c.1:pcie02]
[   21.120883] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   21.121020] assign_interrupt_mode Found MSI capability
[   21.121129] Allocate Port Service[0000:00:1c.2:pcie00]
[   21.121153] Allocate Port Service[0000:00:1c.2:pcie02]
[   21.121430] isapnp: Scanning for PnP cards...
[   21.479108] isapnp: No Plug & Play device found
[   21.500715] hpet_resources: 0xfed00000 is busy
[   21.500742] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   21.501722] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   21.501778] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   21.501853] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[   21.512499] serio: i8042 KBD port at 0x60,0x64 irq 1
[   21.512503] serio: i8042 AUX port at 0x60,0x64 irq 12
[   21.521921] mice: PS/2 mouse device common for all mice
[   21.522008] EISA: Probing bus 0 at eisa.0
[   21.522016] Cannot allocate resource for EISA slot 1
[   21.522018] Cannot allocate resource for EISA slot 2
[   21.522020] Cannot allocate resource for EISA slot 3
[   21.522021] Cannot allocate resource for EISA slot 4
[   21.522023] Cannot allocate resource for EISA slot 5
[   21.522024] Cannot allocate resource for EISA slot 6
[   21.522026] Cannot allocate resource for EISA slot 7
[   21.522034] EISA: Detected 0 cards.
[   21.522036] cpuidle: using governor ladder
[   21.522145] NET: Registered protocol family 1
[   21.522170] Using IPI Shortcut mode
[   21.522195] registered taskstats version 1
[   21.522298]   Magic number: 0:507:998
[   21.522306]   hash matches device ttyae
[   21.522365]   hash matches device 00:00
[   21.522376] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   21.522377] EDD information not available.
[   21.522556] Freeing unused kernel memory: 364k freed
[   21.527304] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   22.713131] fuse init (API version 7.9)
[   22.732580] Monitor-Mwait will be used to enter C-1 state
[   22.732583] Monitor-Mwait will be used to enter C-2 state
[   22.732585] Monitor-Mwait will be used to enter C-3 state
[   22.732702] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   22.732706] ACPI: Processor [CPU0] (supports 8 throttling states)
[   22.734620] ACPI: Thermal Zone [THM0] (48 C)
[   22.736078] ACPI: Thermal Zone [THM1] (47 C)
[   23.230931] usbcore: registered new interface driver usbfs
[   23.230952] usbcore: registered new interface driver hub
[   23.234903] usbcore: registered new device driver usb
[   23.235839] USB Universal Host Controller Interface driver v3.0
[   23.235885] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 20 (level, low) -> IRQ 16
[   23.235899] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[   23.235904] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[   23.236126] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[   23.236171] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001820
[   23.236292] usb usb1: configuration #1 chosen from 1 choice
[   23.236311] hub 1-0:1.0: USB hub found
[   23.236315] hub 1-0:1.0: 2 ports detected
[   23.338781] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 17
[   23.338797] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[   23.338803] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[   23.338823] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[   23.338866] uhci_hcd 0000:00:1a.1: irq 17, io base 0x00001840
[   23.338963] usb usb2: configuration #1 chosen from 1 choice
[   23.338981] hub 2-0:1.0: USB hub found
[   23.338985] hub 2-0:1.0: 2 ports detected
[   23.440858] SCSI subsystem initialized
[   23.447461] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 19
[   23.447476] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   23.447482] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   23.447504] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 3
[   23.447547] uhci_hcd 0000:00:1d.0: irq 19, io base 0x00001860
[   23.447646] usb usb3: configuration #1 chosen from 1 choice
[   23.447663] hub 3-0:1.0: USB hub found
[   23.447667] hub 3-0:1.0: 2 ports detected
[   23.480565] libata version 3.00 loaded.
[   23.550405] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 20
[   23.550422] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   23.550427] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   23.550446] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 4
[   23.550489] uhci_hcd 0000:00:1d.1: irq 20, io base 0x00001880
[   23.550591] usb usb4: configuration #1 chosen from 1 choice
[   23.550609] hub 4-0:1.0: USB hub found
[   23.550613] hub 4-0:1.0: 2 ports detected
[   23.654221] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 21
[   23.654237] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   23.654243] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   23.654262] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 5
[   23.654306] uhci_hcd 0000:00:1d.2: irq 21, io base 0x000018a0
[   23.654407] usb usb5: configuration #1 chosen from 1 choice
[   23.654426] hub 5-0:1.0: USB hub found
[   23.654430] hub 5-0:1.0: 2 ports detected
[   23.759229] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 22 (level, low) -> IRQ 18
[   23.759245] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[   23.759249] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[   23.759278] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 6
[   23.763209] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
[   23.763220] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xf8504800
[   23.789884] usb 3-2: new full speed USB device using uhci_hcd and address 2
[   23.801877] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   23.801979] usb usb6: configuration #1 chosen from 1 choice
[   23.802000] hub 6-0:1.0: USB hub found
[   23.802005] hub 6-0:1.0: 4 ports detected
[   23.906035] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 19 (level, low) -> IRQ 22
[   23.906056] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   23.906062] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   23.906084] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
[   23.910017] ehci_hcd 0000:00:1d.7: debug port 1
[   23.910030] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   23.910040] ehci_hcd 0000:00:1d.7: irq 22, io mem 0xf8504c00
[   23.925656] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   23.925768] usb usb7: configuration #1 chosen from 1 choice
[   23.925788] hub 7-0:1.0: USB hub found
[   23.925793] hub 7-0:1.0: 6 ports detected
[   24.029604] tg3.c:v3.86 (November 9, 2007)
[   24.029688] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 18 (level, low) -> IRQ 21
[   24.029709] PCI: Setting latency timer of device 0000:04:00.0 to 64
[   24.300969] Clocksource tsc unstable (delta = -2898384637 ns)
[   24.304958] Time: hpet clocksource has been installed.
[   24.306181] usb 3-2: device not accepting address 2, error -71
[   24.318980] eth0: Tigon3 [partno(BCM95751) rev b002 PHY(5787)] (PCI Express) 10/100/1000Base-T Ethernet 00:1c:25:90:e3:07
[   24.318986] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[1] TSOcap[1]
[   24.318988] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[   24.319218] ACPI: PCI Interrupt 0000:00:1f.1[C] -> GSI 16 (level, low) -> IRQ 19
[   24.319256] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   24.319269] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
[   24.324579] ata_piix 0000:00:1f.1: version 2.12
[   24.324597] ACPI: PCI Interrupt 0000:00:1f.1[C] -> GSI 16 (level, low) -> IRQ 19
[   24.324634] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   24.325392] scsi0 : ata_piix
[   24.325752] scsi1 : ata_piix
[   24.326109] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[   24.326112] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[   24.343189] usb 7-2: new high speed USB device using ehci_hcd and address 2
[   24.455448] ata1.00: ATAPI: HL-DT-STCD-RW/DVD DRIVE GCC-T10N, 1.04, max UDMA/33
[   24.475822] usb 7-2: configuration #1 chosen from 1 choice
[   24.488802] usbcore: registered new interface driver libusual
[   24.492865] Initializing USB Mass Storage driver...
[   24.494132] scsi2 : SCSI emulation for USB Mass Storage devices
[   24.494505] usbcore: registered new interface driver usb-storage
[   24.494509] USB Mass Storage support registered.
[   24.494576] usb-storage: device found at 2
[   24.494578] usb-storage: waiting for device to settle before scanning
[   24.623741] ata1.00: configured for UDMA/33
[   24.623819] ata2: port disabled. ignoring.
[   24.626421] scsi 0:0:0:0: CD-ROM            HL-DT-ST RW/DVD GCC-T10N  1.04 PQ: 0 ANSI: 5
[   24.626755] ahci 0000:00:1f.2: version 3.0
[   24.626803] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 16 (level, low) -> IRQ 19
[   24.626895] ahci 0000:00:1f.2: nr_ports (3) and implemented port map (0x1) don't match, using nr_ports
[   24.626897] ahci 0000:00:1f.2: forcing PORTS_IMPL to 0x7
[   24.632465] Driver 'sr' needs updating - please use bus_type methods
[   24.639628] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[   24.639632] Uniform CD-ROM driver Revision: 3.20
[   24.639676] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   24.643035] sr 0:0:0:0: Attached scsi generic sg0 type 5
[   24.701748] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 1.5 Gbps 0x7 impl SATA mode
[   24.701752] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part 
[   24.701762] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   24.701965] scsi3 : ahci
[   24.702166] scsi4 : ahci
[   24.702286] scsi5 : ahci
[   24.702344] ata3: SATA max UDMA/133 abar m2048@0xf8504000 port 0xf8504100 irq 220
[   24.702349] ata4: SATA max UDMA/133 abar m2048@0xf8504000 port 0xf8504180 irq 220
[   24.702354] ata5: SATA max UDMA/133 abar m2048@0xf8504000 port 0xf8504200 irq 220
[   24.719067] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   24.721165] ata3.00: ATA-7: WDC WD800BEVS-08RST2, 08.01G08, max UDMA/133
[   24.721167] ata3.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 31/32)
[   24.721528] ata3.00: configured for UDMA/133
[   24.732489] ata4: SATA link down (SStatus 0 SControl 0)
[   24.743325] ata5: SATA link down (SStatus 0 SControl 0)
[   24.743429] scsi 3:0:0:0: Direct-Access     ATA      WDC WD800BEVS-08 08.0 PQ: 0 ANSI: 5
[   24.743491] scsi 3:0:0:0: Attached scsi generic sg1 type 0
[   24.750446] Driver 'sd' needs updating - please use bus_type methods
[   24.752235] sd 3:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   24.752245] sd 3:0:0:0: [sda] Write Protect is off
[   24.752248] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   24.752260] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   24.752300] sd 3:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   24.752307] sd 3:0:0:0: [sda] Write Protect is off
[   24.752308] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   24.752319] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   24.752322]  sda: sda1 sda2
[   24.755131] sd 3:0:0:0: [sda] Attached SCSI disk
[   24.923481] loop: module loaded
[   24.941201] kjournald starting.  Commit interval 5 seconds
[   24.941213] EXT3-fs: mounted filesystem with ordered data mode.
[   25.243286] usb-storage: device scan complete
[   25.243776] scsi 2:0:0:0: Direct-Access     Lexar    JumpDrive        1.00 PQ: 0 ANSI: 1 CCS
[   25.245007] sd 2:0:0:0: [sdb] 503808 512-byte hardware sectors (258 MB)
[   25.245540] sd 2:0:0:0: [sdb] Write Protect is off
[   25.245542] sd 2:0:0:0: [sdb] Mode Sense: 23 00 00 00
[   25.245544] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   25.248041] sd 2:0:0:0: [sdb] 503808 512-byte hardware sectors (258 MB)
[   25.248569] sd 2:0:0:0: [sdb] Write Protect is off
[   25.248571] sd 2:0:0:0: [sdb] Mode Sense: 23 00 00 00
[   25.248572] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   25.248576]  sdb: sdb1
[   25.249382] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[   25.249411] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   29.718954] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   29.740113] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   29.776413] Linux agpgart interface v0.102
[   29.790700] agpgart: Detected an Intel 965GM Chipset.
[   29.791052] agpgart: Detected 7676K stolen memory.
[   29.874782] agpgart: AGP aperture is 256M @ 0xe0000000
[   29.877493] iTCO_vendor_support: vendor-support=0
[   29.878897] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   29.879328] iTCO_wdt: Found a ICH8M TCO device (Version=2, TCOBASE=0x1060)
[   29.879382] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   30.116548] input: Power Button (FF) as /devices/virtual/input/input2
[   30.130637] ACPI: Power Button (FF) [PWRF]
[   30.130713] input: Lid Switch as /devices/virtual/input/input3
[   30.132470] ACPI: Lid Switch [LID]
[   30.132537] input: Sleep Button (CM) as /devices/virtual/input/input4
[   30.142623] ACPI: Sleep Button (CM) [SLPB]
[   30.698949] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   30.931103] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input6
[   30.941195] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   30.953453] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:05/LNXVIDEO:01/input/input7
[   30.970794] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
[   31.496319] Yenta: CardBus bridge found at 0000:15:00.0 [17aa:20c4]
[   31.576948] ACPI: AC Adapter [AC] (on-line)
[   31.624840] Yenta: ISA IRQ mask 0x0cb8, PCI irq 19
[   31.624846] Socket status: 30000006
[   31.624850] pcmcia: parent PCI bridge I/O window: 0x4000 - 0x7fff
[   31.624852] cs: IO port probe 0x4000-0x7fff: clean.
[   31.625624] pcmcia: parent PCI bridge Memory window: 0xd4000000 - 0xd7efffff
[   31.625626] pcmcia: parent PCI bridge Memory window: 0xd8000000 - 0xdbffffff
[   31.733299] ACPI: Battery Slot [BAT0] (battery present)
[   32.238584] Real Time Clock Driver v1.12ac
[   32.408019] Non-volatile memory driver v1.2
[   32.521502] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   32.540257] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/input/input8
[   32.559847] thinkpad_acpi: ThinkPad ACPI Extras v0.17
[   32.559850] thinkpad_acpi: [http://ibm-acpi.sf.net/](http://ibm-acpi.sf.net/)
[   32.559852] thinkpad_acpi: ThinkPad BIOS 7PETB2WW (2.12 ), EC 7KHT24WW-1.08
[   32.559854] thinkpad_acpi: Lenovo ThinkPad R61e
[   32.560443] thinkpad_acpi: radio switch found; radios are enabled
[   32.565217] thinkpad_acpi: standard ACPI backlight interface available, not loading native one...
[   32.565546] input: ThinkPad Extra Buttons as /devices/virtual/input/input9
[   33.697097] cs: IO port probe 0x100-0x3af: clean.
[   33.699493] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   33.700543] cs: IO port probe 0x820-0x8ff: clean.
[   33.701362] cs: IO port probe 0xc00-0xcf7: clean.
[   33.702342] cs: IO port probe 0xa00-0xaff: clean.
[   34.921593] lp: driver loaded but no devices found
[   34.935796] ath_hal: module license 'Proprietary' taints kernel.
[   34.936459] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   35.035678] wlan: 0.9.4
[   35.061561] ath_pci: 0.9.4
[   35.061636] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 20
[   35.061684] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   35.110180] wifi%d: unable to attach hardware: 'Hardware revision not supported' (HAL status 13)
[   35.110197] ACPI: PCI interrupt for device 0000:03:00.0 disabled
[   35.246877] EXT3 FS on loop0, internal journal
[   43.831968] Adding 976552k swap on /host/ubuntu/disks/swap.disk.  Priority:-1 extents:1 across:976552k
[   44.059741] ip_tables: (C) 2000-2006 Netfilter Core Team
[   44.279799] No dock devices found.
[   44.862191] apm: BIOS not found.
[   44.914638] ppdev: user-space parallel port driver
[   44.948586] audit(1217458831.502:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4894 profile="/usr/sbin/cupsd" namespace="default"
[   45.016982] input: /usr/sbin/thinkpad-keys as /devices/virtual/input/input10
[   45.684655] Bluetooth: Core ver 2.11
[   45.686428] NET: Registered protocol family 31
[   45.686432] Bluetooth: HCI device and connection manager initialized
[   45.686435] Bluetooth: HCI socket layer initialized
[   45.694553] Bluetooth: L2CAP ver 2.9
[   45.694557] Bluetooth: L2CAP socket layer initialized
[   45.755604] Bluetooth: RFCOMM socket layer initialized
[   45.755617] Bluetooth: RFCOMM TTY layer initialized
[   45.755618] Bluetooth: RFCOMM ver 1.8
[   46.992600] [drm] Initialized drm 1.1.0 20060810
[   46.996958] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 19
[   46.996966] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   46.997014] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   50.899953] NET: Registered protocol family 10
[   50.900326] lo: Disabled Privacy Extensions
[   50.900739] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   97.837014] tg3: eth0: Link is up at 100 Mbps, full duplex.
[   97.837019] tg3: eth0: Flow control is off for TX and off for RX.
[   97.837459] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   98.128979] NET: Registered protocol family 17
[   99.518419] eth0: no IPv6 routers present
[  188.697397] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  188.971550] tg3: eth0: Link is up at 100 Mbps, full duplex.
[  188.971555] tg3: eth0: Flow control is off for TX and off for RX.
[  188.971978] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  191.598144] eth0: no IPv6 routers present
[  220.936765] ath_pci: driver unloaded
[  272.804373] tg3: eth0: Link is down.
[  272.989461] tg3: eth0: Link is up at 100 Mbps, full duplex.
[  272.989465] tg3: eth0: Flow control is off for TX and off for RX.
[  286.279323] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  286.369770] tg3: eth0: Link is up at 100 Mbps, full duplex.
[  286.369774] tg3: eth0: Flow control is off for TX and off for RX.
[  286.370505] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  288.978220] eth0: no IPv6 routers present
melissa@melissa-laptop:~$ 


thanks again :D

---

### Post by epiphonygirl on 2008-07-30
ok, i think i've tried everything that was listed to the letter and still no wireless no matter what I do! Lol anybody have any other ideas? Thanks

---

### Post by pytheas22 on 2008-07-30
> Ok, so I tried what you said to do with ndis wrapper and now it recognizes that the hardware is present

That's really good that it recognized the hardware at least.  From dmesg, it still doesn't look like the system is trying to load ndiswrapper at all; it still looks like ath_pci (the madwifi driver) is in control.  Try running:
```

sudo -s
sed 's/ndiswrapper//' /etc/modprobe.d/blacklist
echo 'ndiswrapper' >> /etc/modules
echo 'blacklist ath_pci' >> /etc/modprobe.d/blacklist
echo 'blacklist ath_rate_sample' >> /etc/modprobe.d/blacklist
echo 'blacklist ath_hal' >> /etc/modprobe.d/blacklist
```

Now reboot.  After reboot, if your wireless is still not recognized, run:
```

sudo rmmod ndiswrapper
sudo rmmod ath_pci
sudo modprobe ndiswrapper
sudo ifconfig wlan0 up
```

does it work now?  It really should, unless ndiswrapper is lying about detecting the hardware.  Does:
```

dmesg | grep -e ndiswrapper -e wlan
```

return anything?


> 
Also in hardware drivers I now see that the wireless adapter says enabled but not in use.

That's alright; it's supposed to be this way if you're trying to use ndiswrapper.

> I think I'm going to give madwifi one more try in the mean time I'll post current readouts for ndiswrapper -l and dmesg:


If you followed that guide to the letter for compiling the latest madwifi, then I don't know what else to do to make madwifi work better.  Are you sure you're using a 32-bit kernel?  madwifi will only work with your particular wireless card if you're on 32-bit.  The command:
```

uname -m
```

tells you which kernel you have installed; if it says 'i386' or 'i686,' you're using 32-bit.

---

### Post by epiphonygirl on 2008-07-30
Ok so I ran:

```
sudo -s
sed 's/ndiswrapper//' /etc/modprobe.d/blacklist
echo 'ndiswrapper' >> /etc/modules
echo 'blacklist ath_pci' >> /etc/modprobe.d/blacklist
echo 'blacklist ath_rate_sample' >> /etc/modprobe.d/blacklist
echo 'blacklist ath_hal' >> /etc/modprobe.d/blacklist
```

and it went great rebooted and in network tools I see that I have a new interface: eth0:avahi, but when I go to configure it it says that the interface doesn't exist! haha. So, I decided to continue on with what you posted thinking it may help so I ran

```
sudo rmmod ndiswrapper
sudo rmmod ath_pci
sudo modprobe ndiswrapper
sudo ifconfig wlan0 up
```

and I got some nice error messages after I ran anything with ndiswrapper or wireless in it:

```
melissa@melissa-laptop:~$ sudo rmmod ndiswrapper
ERROR: Module ndiswrapper does not exist in /proc/modules
melissa@melissa-laptop:~$ sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found.
melissa@melissa-laptop:~$ sudo ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device
melissa@melissa-laptop:~$ 

```

What I'm wondering is if all those installations of madwifi are messing up the ndiswrapper because a total of three different versions have been installed over the course of a few days non of which I could get to work.  Finally the output of dmesg | grep -e wlan

```
melissa@melissa-laptop:~$ dmesg | grep -e wlan
[   43.025187] wlan: 0.9.4
melissa@melissa-laptop:~$ 

```

I guess I'll also post the fresh output of dmesg so that you can see if madwifi is still going crazy lol:

```
[   19.363068] monitor/mwait feature present.
[   19.363069] using mwait in idle threads.
[   19.363073] CPU: L1 I cache: 32K, L1 D cache: 32K
[   19.363075] CPU: L2 cache: 1024K
[   19.363077] CPU: After all inits, caps: afebfbff 20100000 00000000 00003940 0000e31d 00000000 00000001 00000000
[   19.363084] Compat vDSO mapped to ffffe000.
[   19.363095] CPU: Intel(R) Celeron(R) CPU          540  @ 1.86GHz stepping 01
[   19.363100] Checking 'hlt' instruction... OK.
[   19.380272] Freeing SMP alternatives: 0k freed
[   19.380362] Early unpacking initramfs... done
[   19.688260] ACPI: Core revision 20070126
[   19.688316] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   19.726499] ENABLING IO-APIC IRQs
[   19.726695] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   19.874115] net_namespace: 64 bytes
[   19.874121] Booting paravirtualized kernel on bare hardware
[   19.874528] Time: 21:50:00  Date: 07/30/08
[   19.874548] NET: Registered protocol family 16
[   19.874690] EISA bus registered
[   19.874694] ACPI: bus type pci registered
[   19.875208] PCI: PCI BIOS revision 3.00 entry at 0xfde37, last bus=24
[   19.875210] PCI: Using configuration type 1
[   19.875217] Setting up standard PCI resources
[   19.878478] ACPI: EC: EC description table is found, configuring boot EC
[   19.882326] ACPI: BIOS _OSI(Linux) query honored via DMI
[   19.882947] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   19.959199] ACPI: Interpreter enabled
[   19.959201] ACPI: (supports S0 S3 S4 S5)
[   19.959214] ACPI: Using IOAPIC for interrupt routing
[   19.964191] ACPI: EC: GPE = 0x12, I/O: command/status = 0x66, data = 0x62
[   19.964194] ACPI: EC: driver started in poll mode
[   19.964317] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   19.966340] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[   19.966346] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[   19.968263] PCI: Transparent bridge - 0000:00:1e.0
[   19.968425] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   19.968586] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP0._PRT]
[   19.968693] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
[   19.968798] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]
[   19.968906] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[   19.971515] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 *10 11)
[   19.971705] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11)
[   19.971888] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11)
[   19.972071] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11)
[   19.972253] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11)
[   19.972437] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11)
[   19.972620] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 *11)
[   19.972802] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11)
[   19.972960] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   19.973048] ACPI: Power Resource [PUBS] (on)
[   19.973098] Linux Plug and Play Support v0.97 (c) Adam Belay
[   19.973122] pnp: PnP ACPI init
[   19.973128] ACPI: bus type pnp registered
[   19.974204] pnpacpi: exceeded the max number of mem resources: 12
[   19.975186] pnp: PnP ACPI: found 10 devices
[   19.975188] ACPI: ACPI bus type pnp unregistered
[   19.975191] PnPBIOS: Disabled by ACPI PNP
[   19.975360] PCI: Using ACPI for IRQ routing
[   19.975362] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   20.205467] NET: Registered protocol family 8
[   20.205469] NET: Registered protocol family 20
[   20.205500] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   20.205503] hpet0: 3 64-bit timers, 14318180 Hz
[   20.206535] AppArmor: AppArmor Filesystem Enabled
[   20.209429] Time: tsc clocksource has been installed.
[   20.209438] Switched to high resolution mode on CPU 0
[   20.217418] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[   20.217421] system 00:00: iomem range 0xc0000-0xc3fff could not be reserved
[   20.217423] system 00:00: iomem range 0xc4000-0xc7fff could not be reserved
[   20.217425] system 00:00: iomem range 0xc8000-0xcbfff has been reserved
[   20.217428] system 00:00: iomem range 0xcc000-0xcffff has been reserved
[   20.217430] system 00:00: iomem range 0xd0000-0xd3fff could not be reserved
[   20.217432] system 00:00: iomem range 0x0-0x0 could not be reserved
[   20.217434] system 00:00: iomem range 0x0-0x0 could not be reserved
[   20.217436] system 00:00: iomem range 0x0-0x0 could not be reserved
[   20.217438] system 00:00: iomem range 0xe0000-0xe3fff has been reserved
[   20.217440] system 00:00: iomem range 0xe4000-0xe7fff has been reserved
[   20.217442] system 00:00: iomem range 0xe8000-0xebfff has been reserved
[   20.217448] system 00:02: ioport range 0x164e-0x164f has been reserved
[   20.217450] system 00:02: ioport range 0x1000-0x107f has been reserved
[   20.217452] system 00:02: ioport range 0x1180-0x11bf has been reserved
[   20.217454] system 00:02: ioport range 0x800-0x80f has been reserved
[   20.217457] system 00:02: ioport range 0x15e0-0x15ef has been reserved
[   20.217459] system 00:02: ioport range 0x1600-0x165f could not be reserved
[   20.217461] system 00:02: iomem range 0xf0000000-0xf3ffffff could not be reserved
[   20.217465] system 00:02: iomem range 0xfed1c000-0xfed1ffff could not be reserved
[   20.217467] system 00:02: iomem range 0xfed14000-0xfed17fff could not be reserved
[   20.217469] system 00:02: iomem range 0xfed18000-0xfed18fff could not be reserved
[   20.217472] system 00:02: iomem range 0xfed19000-0xfed19fff could not be reserved
[   20.217474] system 00:02: iomem range 0xfed45000-0xfed4bfff could not be reserved
[   20.217477] system 00:02: iomem range 0xfed40000-0xfed44fff could not be reserved
[   20.247775] PCI: Bridge: 0000:00:1c.0
[   20.247780]   IO window: 2000-2fff
[   20.247791]   MEM window: f4000000-f5ffffff
[   20.247797]   PREFETCH window: f8600000-f86fffff
[   20.247810] PCI: Bridge: 0000:00:1c.1
[   20.247814]   IO window: 3000-3fff
[   20.247825]   MEM window: f6000000-f7ffffff
[   20.247833]   PREFETCH window: f8700000-f87fffff
[   20.247845] PCI: Bridge: 0000:00:1c.2
[   20.247846]   IO window: disabled.
[   20.247854]   MEM window: f8200000-f82fffff
[   20.247862]   PREFETCH window: disabled.
[   20.247877] PCI: Bus 22, cardbus bridge: 0000:15:00.0
[   20.247879]   IO window: 00004000-000040ff
[   20.247888]   IO window: 00004400-000044ff
[   20.247897]   PREFETCH window: d8000000-dbffffff
[   20.247906]   MEM window: 70000000-73ffffff
[   20.247914] PCI: Bridge: 0000:00:1e.0
[   20.247919]   IO window: 4000-7fff
[   20.247929]   MEM window: d4000000-d7efffff
[   20.247938]   PREFETCH window: d8000000-dbffffff
[   20.248002] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 20 (level, low) -> IRQ 16
[   20.248013] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   20.248067] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 21 (level, low) -> IRQ 17
[   20.248074] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   20.248127] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 22 (level, low) -> IRQ 18
[   20.248134] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   20.248159] PCI: Enabling device 0000:00:1e.0 (0005 -> 0007)
[   20.248172] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   20.248205] ACPI: PCI Interrupt 0000:15:00.0[A] -> GSI 16 (level, low) -> IRQ 19
[   20.248213] PCI: Setting latency timer of device 0000:15:00.0 to 64
[   20.248224] NET: Registered protocol family 2
[   20.285313] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   20.285506] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   20.286007] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[   20.286180] TCP: Hash tables configured (established 131072 bind 65536)
[   20.286182] TCP reno registered
[   20.297383] checking if image is initramfs... it is
[   20.898974] Freeing initrd memory: 7230k freed
[   20.899128] Simple Boot Flag at 0x35 set to 0x1
[   20.899511] audit: initializing netlink socket (disabled)
[   20.899525] audit(1217454600.308:1): initialized
[   20.899663] highmem bounce pool size: 64 pages
[   20.901136] VFS: Disk quotas dquot_6.5.1
[   20.901153] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   20.901262] io scheduler noop registered
[   20.901263] io scheduler anticipatory registered
[   20.901265] io scheduler deadline registered
[   20.901274] io scheduler cfq registered (default)
[   20.901286] Boot video device is 0000:00:02.0
[   20.901561] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   20.901707] assign_interrupt_mode Found MSI capability
[   20.901817] Allocate Port Service[0000:00:1c.0:pcie00]
[   20.901845] Allocate Port Service[0000:00:1c.0:pcie02]
[   20.902034] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   20.902164] assign_interrupt_mode Found MSI capability
[   20.902273] Allocate Port Service[0000:00:1c.1:pcie00]
[   20.902298] Allocate Port Service[0000:00:1c.1:pcie02]
[   20.902480] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   20.902623] assign_interrupt_mode Found MSI capability
[   20.902730] Allocate Port Service[0000:00:1c.2:pcie00]
[   20.902755] Allocate Port Service[0000:00:1c.2:pcie02]
[   20.903025] isapnp: Scanning for PnP cards...
[   21.260781] isapnp: No Plug & Play device found
[   21.281804] hpet_resources: 0xfed00000 is busy
[   21.281831] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   21.282807] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   21.282864] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   21.282937] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[   21.292873] serio: i8042 KBD port at 0x60,0x64 irq 1
[   21.292876] serio: i8042 AUX port at 0x60,0x64 irq 12
[   21.295612] mice: PS/2 mouse device common for all mice
[   21.295698] EISA: Probing bus 0 at eisa.0
[   21.295706] Cannot allocate resource for EISA slot 1
[   21.295709] Cannot allocate resource for EISA slot 2
[   21.295710] Cannot allocate resource for EISA slot 3
[   21.295712] Cannot allocate resource for EISA slot 4
[   21.295713] Cannot allocate resource for EISA slot 5
[   21.295715] Cannot allocate resource for EISA slot 6
[   21.295716] Cannot allocate resource for EISA slot 7
[   21.295724] EISA: Detected 0 cards.
[   21.295727] cpuidle: using governor ladder
[   21.295832] NET: Registered protocol family 1
[   21.295857] Using IPI Shortcut mode
[   21.295882] registered taskstats version 1
[   21.295984]   Magic number: 0:278:855
[   21.296029]   hash matches device ptyv7
[   21.296035]   hash matches device ptysa
[   21.296064] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   21.296066] EDD information not available.
[   21.296258] Freeing unused kernel memory: 364k freed
[   21.301004] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   22.488353] fuse init (API version 7.9)
[   22.507388] Monitor-Mwait will be used to enter C-1 state
[   22.507391] Monitor-Mwait will be used to enter C-2 state
[   22.507393] Monitor-Mwait will be used to enter C-3 state
[   22.507486] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   22.507490] ACPI: Processor [CPU0] (supports 8 throttling states)
[   22.509358] ACPI: Thermal Zone [THM0] (48 C)
[   22.510812] ACPI: Thermal Zone [THM1] (47 C)
[   23.004236] usbcore: registered new interface driver usbfs
[   23.004256] usbcore: registered new interface driver hub
[   23.009805] usbcore: registered new device driver usb
[   23.010739] USB Universal Host Controller Interface driver v3.0
[   23.010785] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 20 (level, low) -> IRQ 16
[   23.010799] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[   23.010804] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[   23.011030] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[   23.011075] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001820
[   23.011195] usb usb1: configuration #1 chosen from 1 choice
[   23.011213] hub 1-0:1.0: USB hub found
[   23.011217] hub 1-0:1.0: 2 ports detected
[   23.112455] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 17
[   23.112469] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[   23.112475] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[   23.112495] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[   23.112538] uhci_hcd 0000:00:1a.1: irq 17, io base 0x00001840
[   23.112634] usb usb2: configuration #1 chosen from 1 choice
[   23.112652] hub 2-0:1.0: USB hub found
[   23.112656] hub 2-0:1.0: 2 ports detected
[   23.216287] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 19
[   23.216304] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   23.216310] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   23.216333] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 3
[   23.216376] uhci_hcd 0000:00:1d.0: irq 19, io base 0x00001860
[   23.216478] usb usb3: configuration #1 chosen from 1 choice
[   23.216500] hub 3-0:1.0: USB hub found
[   23.216504] hub 3-0:1.0: 2 ports detected
[   23.218425] SCSI subsystem initialized
[   23.264093] libata version 3.00 loaded.
[   23.320082] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 20
[   23.320098] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   23.320104] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   23.320124] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 4
[   23.320166] uhci_hcd 0000:00:1d.1: irq 20, io base 0x00001880
[   23.320268] usb usb4: configuration #1 chosen from 1 choice
[   23.320287] hub 4-0:1.0: USB hub found
[   23.320291] hub 4-0:1.0: 2 ports detected
[   23.423903] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 21
[   23.423920] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   23.423926] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   23.423945] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 5
[   23.423985] uhci_hcd 0000:00:1d.2: irq 21, io base 0x000018a0
[   23.424086] usb usb5: configuration #1 chosen from 1 choice
[   23.424105] hub 5-0:1.0: USB hub found
[   23.424109] hub 5-0:1.0: 2 ports detected
[   23.528970] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 22 (level, low) -> IRQ 18
[   23.528990] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[   23.528996] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[   23.529026] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 6
[   23.532958] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
[   23.532970] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xf8504800
[   23.559577] usb 3-2: new full speed USB device using uhci_hcd and address 2
[   23.571548] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   23.571647] usb usb6: configuration #1 chosen from 1 choice
[   23.571667] hub 6-0:1.0: USB hub found
[   23.571673] hub 6-0:1.0: 4 ports detected
[   23.675680] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 19 (level, low) -> IRQ 22
[   23.675700] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   23.675706] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   23.675728] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
[   23.679678] ehci_hcd 0000:00:1d.7: debug port 1
[   23.679691] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   23.679702] ehci_hcd 0000:00:1d.7: irq 22, io mem 0xf8504c00
[   23.695343] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   23.695457] usb usb7: configuration #1 chosen from 1 choice
[   23.695477] hub 7-0:1.0: USB hub found
[   23.695482] hub 7-0:1.0: 6 ports detected
[   23.799284] tg3.c:v3.86 (November 9, 2007)
[   23.799369] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 18 (level, low) -> IRQ 21
[   23.799390] PCI: Setting latency timer of device 0000:04:00.0 to 64
[   24.082645] Clocksource tsc unstable (delta = -3596260183 ns)
[   24.086635] Time: hpet clocksource has been installed.
[   24.094632] usb 3-2: device not accepting address 2, error -71
[   24.101087] eth0: Tigon3 [partno(BCM95751) rev b002 PHY(5787)] (PCI Express) 10/100/1000Base-T Ethernet 00:1c:25:90:e3:07
[   24.101092] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[1] TSOcap[1]
[   24.101095] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[   24.101331] ACPI: PCI Interrupt 0000:00:1f.1[C] -> GSI 16 (level, low) -> IRQ 19
[   24.101373] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   24.101391] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
[   24.106689] ata_piix 0000:00:1f.1: version 2.12
[   24.106707] ACPI: PCI Interrupt 0000:00:1f.1[C] -> GSI 16 (level, low) -> IRQ 19
[   24.106746] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   24.107486] scsi0 : ata_piix
[   24.107849] scsi1 : ata_piix
[   24.108209] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[   24.108211] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[   24.132391] usb 7-2: new high speed USB device using ehci_hcd and address 2
[   24.265141] usb 7-2: configuration #1 chosen from 1 choice
[   24.268619] ata1.00: ATAPI: HL-DT-STCD-RW/DVD DRIVE GCC-T10N, 1.04, max UDMA/33
[   24.278288] usbcore: registered new interface driver libusual
[   24.282337] Initializing USB Mass Storage driver...
[   24.283618] scsi2 : SCSI emulation for USB Mass Storage devices
[   24.283993] usbcore: registered new interface driver usb-storage
[   24.283996] USB Mass Storage support registered.
[   24.284061] usb-storage: device found at 2
[   24.284062] usb-storage: waiting for device to settle before scanning
[   24.414130] ata1.00: configured for UDMA/33
[   24.414205] ata2: port disabled. ignoring.
[   24.416781] scsi 0:0:0:0: CD-ROM            HL-DT-ST RW/DVD GCC-T10N  1.04 PQ: 0 ANSI: 5
[   24.417120] ahci 0000:00:1f.2: version 3.0
[   24.417168] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 16 (level, low) -> IRQ 19
[   24.417261] ahci 0000:00:1f.2: nr_ports (3) and implemented port map (0x1) don't match, using nr_ports
[   24.417263] ahci 0000:00:1f.2: forcing PORTS_IMPL to 0x7
[   24.422763] Driver 'sr' needs updating - please use bus_type methods
[   24.429712] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[   24.429716] Uniform CD-ROM driver Revision: 3.20
[   24.429759] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   24.433080] sr 0:0:0:0: Attached scsi generic sg0 type 5
[   24.497748] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 1.5 Gbps 0x7 impl SATA mode
[   24.497752] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part 
[   24.497762] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   24.497963] scsi3 : ahci
[   24.498171] scsi4 : ahci
[   24.498289] scsi5 : ahci
[   24.498347] ata3: SATA max UDMA/133 abar m2048@0xf8504000 port 0xf8504100 irq 220
[   24.498352] ata4: SATA max UDMA/133 abar m2048@0xf8504000 port 0xf8504180 irq 220
[   24.498357] ata5: SATA max UDMA/133 abar m2048@0xf8504000 port 0xf8504200 irq 220
[   24.514964] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   24.527778] ata3.00: ATA-7: WDC WD800BEVS-08RST2, 08.01G08, max UDMA/133
[   24.527781] ata3.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 31/32)
[   24.528141] ata3.00: configured for UDMA/133
[   24.538955] ata4: SATA link down (SStatus 0 SControl 0)
[   24.549824] ata5: SATA link down (SStatus 0 SControl 0)
[   24.549931] scsi 3:0:0:0: Direct-Access     ATA      WDC WD800BEVS-08 08.0 PQ: 0 ANSI: 5
[   24.549991] scsi 3:0:0:0: Attached scsi generic sg1 type 0
[   24.556850] Driver 'sd' needs updating - please use bus_type methods
[   24.558667] sd 3:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   24.558678] sd 3:0:0:0: [sda] Write Protect is off
[   24.558680] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   24.558691] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   24.558733] sd 3:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   24.558740] sd 3:0:0:0: [sda] Write Protect is off
[   24.558741] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   24.558752] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   24.558755]  sda: sda1 sda2
[   24.561036] sd 3:0:0:0: [sda] Attached SCSI disk
[   24.738892] loop: module loaded
[   24.756653] kjournald starting.  Commit interval 5 seconds
[   24.756665] EXT3-fs: mounted filesystem with ordered data mode.
[   25.031809] usb-storage: device scan complete
[   25.032302] scsi 2:0:0:0: Direct-Access     Lexar    JumpDrive        1.00 PQ: 0 ANSI: 1 CCS
[   25.033532] sd 2:0:0:0: [sdb] 503808 512-byte hardware sectors (258 MB)
[   25.034062] sd 2:0:0:0: [sdb] Write Protect is off
[   25.034064] sd 2:0:0:0: [sdb] Mode Sense: 23 00 00 00
[   25.034066] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   25.036561] sd 2:0:0:0: [sdb] 503808 512-byte hardware sectors (258 MB)
[   25.037191] sd 2:0:0:0: [sdb] Write Protect is off
[   25.037193] sd 2:0:0:0: [sdb] Mode Sense: 23 00 00 00
[   25.037195] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   25.037198]  sdb: sdb1
[   25.038361] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[   25.038390] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   29.187163] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   29.202895] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   29.230162] Linux agpgart interface v0.102
[   29.242202] agpgart: Detected an Intel 965GM Chipset.
[   29.242508] agpgart: Detected 7676K stolen memory.
[   29.342974] agpgart: AGP aperture is 256M @ 0xe0000000
[   29.356720] iTCO_vendor_support: vendor-support=0
[   29.369282] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   29.369559] iTCO_wdt: Found a ICH8M TCO device (Version=2, TCOBASE=0x1060)
[   29.369895] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   29.587088] input: Power Button (FF) as /devices/virtual/input/input2
[   29.598447] ACPI: Power Button (FF) [PWRF]
[   29.598524] input: Lid Switch as /devices/virtual/input/input3
[   29.602630] ACPI: Lid Switch [LID]
[   29.602700] input: Sleep Button (CM) as /devices/virtual/input/input4
[   29.622417] ACPI: Sleep Button (CM) [SLPB]
[   30.156055] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   30.391501] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input6
[   30.401026] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   30.402738] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:05/LNXVIDEO:01/input/input7
[   30.415805] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
[   30.944124] Yenta: CardBus bridge found at 0000:15:00.0 [17aa:20c4]
[   31.020038] ACPI: AC Adapter [AC] (on-line)
[   31.076680] Yenta: ISA IRQ mask 0x0cb8, PCI irq 19
[   31.076686] Socket status: 30000006
[   31.076692] pcmcia: parent PCI bridge I/O window: 0x4000 - 0x7fff
[   31.076695] cs: IO port probe 0x4000-0x7fff: clean.
[   31.077438] pcmcia: parent PCI bridge Memory window: 0xd4000000 - 0xd7efffff
[   31.077440] pcmcia: parent PCI bridge Memory window: 0xd8000000 - 0xdbffffff
[   31.175273] ACPI: Battery Slot [BAT0] (battery present)
[   31.784100] Real Time Clock Driver v1.12ac
[   31.974476] Non-volatile memory driver v1.2
[   32.049733] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   32.066036] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/input/input8
[   32.095287] thinkpad_acpi: ThinkPad ACPI Extras v0.17
[   32.095290] thinkpad_acpi: http://ibm-acpi.sf.net/
[   32.095292] thinkpad_acpi: ThinkPad BIOS 7PETB2WW (2.12 ), EC 7KHT24WW-1.08
[   32.095293] thinkpad_acpi: Lenovo ThinkPad R61e
[   32.095837] thinkpad_acpi: radio switch found; radios are enabled
[   32.100627] thinkpad_acpi: standard ACPI backlight interface available, not loading native one...
[   32.100952] input: ThinkPad Extra Buttons as /devices/virtual/input/input9
[   33.326614] NET: Registered protocol family 17
[   33.342795] cs: IO port probe 0x100-0x3af: clean.
[   33.345219] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   33.346221] cs: IO port probe 0x820-0x8ff: clean.
[   33.347040] cs: IO port probe 0xc00-0xcf7: clean.
[   33.348028] cs: IO port probe 0xa00-0xaff: clean.
[   42.911049] lp: driver loaded but no devices found
[   42.925221] ath_hal: module license 'Proprietary' taints kernel.
[   42.925872] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   43.025187] wlan: 0.9.4
[   43.051111] ath_pci: 0.9.4
[   43.051199] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 20
[   43.051257] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   43.099788] wifi%d: unable to attach hardware: 'Hardware revision not supported' (HAL status 13)
[   43.099804] ACPI: PCI interrupt for device 0000:03:00.0 disabled
[   43.714996] EXT3 FS on loop0, internal journal
[   52.957020] Adding 976552k swap on /host/ubuntu/disks/swap.disk.  Priority:-1 extents:1 across:976552k
[   53.395771] ip_tables: (C) 2000-2006 Netfilter Core Team
[   53.742699] No dock devices found.
[   54.855129] apm: BIOS not found.
[   55.027618] ppdev: user-space parallel port driver
[   55.194145] audit(1217472648.628:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4927 profile="/usr/sbin/cupsd" namespace="default"
[   55.370886] input: /usr/sbin/thinkpad-keys as /devices/virtual/input/input10
[   56.511513] Bluetooth: Core ver 2.11
[   56.513203] NET: Registered protocol family 31
[   56.513206] Bluetooth: HCI device and connection manager initialized
[   56.513209] Bluetooth: HCI socket layer initialized
[   56.521351] Bluetooth: L2CAP ver 2.9
[   56.521355] Bluetooth: L2CAP socket layer initialized
[   56.603555] Bluetooth: RFCOMM socket layer initialized
[   56.603569] Bluetooth: RFCOMM TTY layer initialized
[   56.603571] Bluetooth: RFCOMM ver 1.8
[   59.668317] [drm] Initialized drm 1.1.0 20060810
[   59.672680] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 19
[   59.672688] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   59.672736] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   78.333203] NET: Registered protocol family 10
[   78.333572] lo: Disabled Privacy Extensions
[   78.333954] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  521.816152] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  751.224273] ath_pci: driver unloaded
[ 1092.384280] tg3: eth0: Link is up at 100 Mbps, full duplex.
[ 1092.384284] tg3: eth0: Flow control is off for TX and off for RX.
[ 1092.384715] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1102.407257] eth0: no IPv6 routers present
melissa@melissa-laptop:~$ 

```

And now after running these scripts in network tools  eth0:avahi is gone. All I really have to say is just wow, I'm thinking about just formatting this partition again and starting fresh with ndiswrapper and seeing what happens now that I think I know what driver to use for it. What do you think?

(and yes I finally realized how to wrap the code lol)

---

### Post by dmizer on 2008-07-30
post the output of:
```
cat /etc/modprob.d/blacklist | grep ndiswrapper
```

if it returns positive results, please edit /etc/modprob.d/blacklist and remove the blacklist line referring to ndiswrapper.  reboot, and post the output of this command:
```
lshw -C network
```

---

### Post by epiphonygirl on 2008-07-31
ndiswrapper was not blacklisted or at least not in /etc/modprob.d/blacklist and the outputs of each of the codes you listed are here:

```
melissa@melissa-laptop:~$ cat /etc/modprob.d/blacklist | grep ndiswrapper
cat: /etc/modprob.d/blacklist: No such file or directory
melissa@melissa-laptop:~$ sudo 1shw -C network
sudo: 1shw: command not found
melissa@melissa-laptop:~$ sudo lshw -C network
  *-network UNCLAIMED     
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:25:90:e3:07
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 duplex=full ip=192.168.1.31 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s
melissa@melissa-laptop:~$ 

```

I hope this helps.

---

### Post by dmizer on 2008-07-31
try this:
```
sudo aptitude install ndiswrapper-common ndiswrapper-utils-1.9
sudo modprobe ndiswrapper
```

---

### Post by epiphonygirl on 2008-07-31
> **dmizer said:**
> try this:
```
sudo modprobe ndiswrapper
```
The other one ran, but when I ran this one I got a fatal error once again:
```
melissa@melissa-laptop:~$ sudo modprobe ndiswrapper
[sudo] password for melissa: 
FATAL: Module ndiswrapper not found.
melissa@melissa-laptop:~$ 

```

So, where do we go from here? oh yeah, by the way I'm cursed...whenever I have a computer issue of my own it turns out to be this massive production to get it to work, just as this is turning out to be lol.

---

### Post by dmizer on 2008-07-31
what version of ndiswrapper do you have?
```
ndiswrapper -v
```

did you install ndiswrapper from source by chance?

also, post the output of:
```
ls /lib/modules/`uname -r`/ubuntu/misc/ndiswrapper
```

---

### Post by epiphonygirl on 2008-07-31
I installed via add/remove under applications. Apparently my module version is too old? lol.```
melissa@melissa-laptop:~$ ndiswrapper -v
modinfo: could not find module ndiswrapper
module version is too old!
utils version: '1.9', utils version needed by module: '0'
module details:
modinfo: could not find module ndiswrapper

You may need to upgrade driver and/or utils to latest versions available at
http://ndiswrapper.sourceforge.net
melissa@melissa-laptop:~$ 

```

and

```
melissa@melissa-laptop:~$ ls /lib/modules/`uname -r`/ubuntu/misc/ndiswrapper
ls: cannot access /lib/modules/2.6.24-19-386/ubuntu/misc/ndiswrapper: No such file or directory
melissa@melissa-laptop:~$ 

```

maybe this can shed some light.

---

### Post by dmizer on 2008-07-31
Okay, try this:
```
sudo aptitude install ndiswrapper-common
```
then:
```
sudo modprobe ndiswrapper
```

edit:
Sorry, I had to update the first command.

---

### Post by epiphonygirl on 2008-07-31
I still get the exact same error about the module not being found.

---

### Post by dmizer on 2008-07-31
Okay, let's start over from scratch.

Remove the driver from the ndiswrapper module:
```
sudo ndiswrapper -r net5416
```

Uninstall ndiswrapper:
```
sudo aptitude purge ndiswrapper-common ndiswrapper-utils-1.9
```

Reboot, and post the output of:
```
lsmod
ndiswrapper -v
```

---

### Post by epiphonygirl on 2008-07-31
I think I'm just going to wipe out and start fresh again with ubuntu because I think all of the madwifi installations might be causing some of my issues. I'll follow the steps for how to install ndiswrapper from the howto [here]("http://ubuntuforums.org/showthread.php?t=112526") because i installed madwifi first and that may have been what has messed everything up. I will get back to everyone after I've completed it and if it worked or if I had problems with it.  Thanks for all of your hard work.

---

### Post by dmizer on 2008-07-31
> **epiphonygirl said:**
> I'll follow the steps for how to install ndiswrapper from the howto [here]("http://ubuntuforums.org/showthread.php?t=112526") 
Do not follow that howto.  It explains how to install ndiswrapper from source.  If you install ndiswrapper from source, you'll have to reinstall every time you have a kernel update (sometimes as often as once a week).

Instead, just use this command to install ndiswrapper:
```
sudo aptitude install ndiswrapper-common ndiswrapper-utils-1.9
```

---

### Post by epiphonygirl on 2008-07-31
> **dmizer said:**
> Do not follow that howto.  It explains how to install ndiswrapper from source.  If you install ndiswrapper from source, you'll have to reinstall every time you have a kernel update (sometimes once a week).

Instead, just use this command to install ndiswrapper:
```
sudo aptitude install ndiswrapper-common ndiswrapper-utils-1.9
```

now it is supposed to be 
```
sudo aptitude install ndiswrapper-common ndiswrapper-utils-1.9
```

because you told me to just use 

```
sudo aptitude install ndiswrapper-common
``` 

because you had to update the code that you had sent so I should use the one that goes ...utils-1.9 right?

---

### Post by dmizer on 2008-07-31
> **epiphonygirl said:**
> now it is supposed to be 
```
sudo aptitude install ndiswrapper-common ndiswrapper-utils-1.9
```

because you told me to just use 

```
sudo aptitude install ndiswrapper-common
``` 

because you had to update the code that you had sent so I should use the one that goes ...utils-1.9 right?

No, the first command I gave you in [post 14](http://ubuntuforums.org/showpost.php?p=5493711&postcount=14) was the same as I just gave.  You need both ndiswrapper-common and ndiswrapper-utils-1.9 in order for ndiswrapper to work.

In [post 18](http://ubuntuforums.org/showpost.php?p=5495253&postcount=18), I was just trying to confirm that ndiswrapper-common was in fact installed.  We know that ndiswrapper-utils-1.9 was installed because without it, you would not have been able to load a windows driver with "sudo ndiswrapper -i *.inf".  I apologize for not making my intentions clear.

---

### Post by epiphonygirl on 2008-07-31
Ok thanks, i was just double checking :D

---

### Post by buzzmandt on 2008-07-31
I had nothing but no trouble with ndiswrapper and atheros.  Here's my take:

If you've done this already ignore it, but i have atheros working great with madwifi

download the latest madwifi source
[http://downloads.sourceforge.net/madwifi/madwifi-0.9.4.tar.gz](http://downloads.sourceforge.net/madwifi/madwifi-0.9.4.tar.gz)
unzip it
terminal to folder (cd /madwifi_folder for example)
do the following commands
```
make
```
```
sudo make install
```
```
sudo modprobe ath_pci
```
```
sudo gedit /etc/modules
```
insert the following two lines
```
ath_hal
ath_pci
```

save/close this file
reboot

works everytime for me and is just as simple as this.  Hope it works for you
edit/ btw, when new linux headers are updated i usually have to return to the folder, do the make, and sudo make install again and that's all, reboot and everything is working again, so hold on to that madwifi folder.

---

### Post by epiphonygirl on 2008-07-31
Oh yeah, I also found (through looking in windows that Ubuntu misidentified the wirelesscard driver. Its actually AR5211. Just ahhh lol, I'm updating ubuntu now so hopefully I'll be able to try ndiswrapper again soon.

---

### Post by dmizer on 2008-07-31
> **epiphonygirl said:**
> Oh yeah, I also found (through looking in windows that Ubuntu misidentified the wirelesscard driver. Its actually AR5211. Just ahhh lol, I'm updating ubuntu now so hopefully I'll be able to try ndiswrapper again soon.

Even if that is the case, you still should have been able to modprobe ndiswrapper, but you couldn't.

Windows can misidentify cards too, but if it turns out that your card really is an AR5211 instead of an AR242x, then you should file a bug report once this is all said and done.

---

### Post by epiphonygirl on 2008-08-01
Ok, I'm back to square one now...my system is up to date and I have tried installing ndiswrapper according to your directions.```
sudo aptitude install ndiswrapper-common ndiswrapper-utils-1.9
```
However, I don't see ndiswrapper I don't see what I saw before in system>administration> that I used to install windows wireless drivers and I don't know/remember how to make it show up there.

---

### Post by dmizer on 2008-08-01
It's okay ... just do it via command line.

Open a terminal and use the 'cd' command to change into the directory where you've saved your driver files.  Then use this command to install the driver:
```
sudo ndiswrapper -i *.inf
```
Your inf file may be all caps (INF) or all lowercase (inf), when you type the above command, the case must match the file name.

Then, type:
```
ndiswrapper -l
```
to see if the driver has loaded correctly.

Don't forget to blacklist the native drivers.

---

### Post by pytheas22 on 2008-08-01
> However, I don't see ndiswrapper I don't see what I saw before in system>administration> that I used to install windows wireless drivers and I don't know/remember how to make it show up there.

The program you're thinking of is called ndisgtk and can be installed with:
```

sudo apt-get install ndisgtk
```

You can use ndisgtk or the command-line (as per the instructions above) to install the Windows .inf file; they both do the same thing.

Also, I'm sorry if you've already mentioned this, but you are using a 32-bit kernel, right?  If you don't know, post the output of:
```

uname -m
```

I think from some of the dmesg output that you posted earlier that you're using a 64-bit system, and if that's the case you need to do a few things differently, so please confirm either way.

---

### Post by epiphonygirl on 2008-08-02
yeah, its a 32 bit kernel..I haven't had a lot of time to try stuff at the moment, probably tomorrow I'll get to it..Life sometimes gets in the way haha.

---

### Post by dmizer on 2008-08-03
I suggest that you not install ndisgtk.  It is a gui interface, but it has been known to cause problems in the past, and there have been bugs open against it.  It's not much more difficult to install your driver via command line anyway.

---

### Post by epiphonygirl on 2008-08-03
Ok, As per your instructions, dmizer, I installed the ndiswrapper driver. However, I'm not sure how to determine what the native linux drivers are that I need to blacklist. I know how to get into the blacklist, but what to put in there is my source of confusion.

---

### Post by dmizer on 2008-08-03
Well, the quickest way I can think of is just to take a look at the entire list of modules and pick them out.  You can take a look at the modules with this command:
```
lsmod
```
You'll find the modules for your Atheros card on one line.  Most of them will probably be prefixed by ath_something.

---

### Post by pytheas22 on 2008-08-03
> I'm not sure how to determine what the native linux drivers are that I need to blacklist

I'm pretty sure that "ath_pci" is the only native driver for Atheros.  If the code: 
```

lsmod | grep ath_pci
```

returns anything, then ath_pci is what you want to blacklist.

You can also blacklist these modules (shouldn't be necessary but it might help):
```

ath_hal
ath_rate_sample
```

---

### Post by epiphonygirl on 2008-08-03
Ok, so I blacklisted the drivers and now it says that they're neither enabled nor in use in system administration hardware drivers. However, I still have no wireless... since windows says that my card is pci-e i used that .inf file, but when I got the file installed with ndiswrapper before I used the pci .inf file and that was the one that was recognized...I'm thinking that I should try that .inf file instead, but I need instructions on how to uninstall the other driver in the terminal because I don't know how to do that and I do not want those drivers to conflict.

---

### Post by dmizer on 2008-08-03
it shouldn't hurt anything if you have them both installed.

```
sudo ndiswrapper -i filename.inf
```
to insall your driver (replace "filename" with the actual name of the .inf file)

```
sudo ndiswrapper -r filename
```
to remove a driver ("filename" needs to be the same as the inf file name without the .inf ending)

---

### Post by epiphonygirl on 2008-08-04
Once again still nothing in network or networking tools even tho
```
ndiswrapper -l
```
says that the correct driver is installed.

---

### Post by dmizer on 2008-08-04
okay ... please post the output of:
```
lshw -C network
```
again, and we'll make sure that ndiswrapper is driving your card and if there is any more information it can provide.

---

### Post by epiphonygirl on 2008-08-04
here's the output of lshw -C network
```
  *-network UNCLAIMED     
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:25:90:e3:07
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 duplex=full ip=192.168.1.41 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s
melissafrench@melissafrench-laptop:~$ 

```

---

### Post by pytheas22 on 2008-08-04
ndiswrapper still won't claim the device.  But you're using the same driver that made ndiswrapper at least recognize the interface before?  If these drivers are online, could you provide a link please?

Also, could you post the output of:
```

ndiswrapper -l
```

It will show exactly which driver you're using and the bus ID of your card, which may be useful.

---

### Post by epiphonygirl on 2008-08-04
Here is the exact [[COLOR="Blue"]url[/COLOR]]("http://www-307.ibm.com/pc/support/site.wss/MIGR-52527.html"), but there were some other options that I could choose from as well listed [[COLOR="Blue"]here[/COLOR]]("http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-68232") I chose the one that fit my system best R61e thinkpad with a b/g wireless LAN mini PCI adapter, I had tried the pci-e adapter which is what windows says my notebook uses, but ndiswrapper didn't recognize that earlier, it was the pci driver that it recognized.

and the code for ndiswrapper -l
```
net5211 : driver installed
	device (168C:001C) present (alternate driver: ath_pci)
melissafrench@melissafrench-laptop:~$ 

```

---

### Post by pytheas22 on 2008-08-04
Try removing the current driver and using the one from [here]("ftp://ftp.work.acer-euro.com/notebook/aspire_4710/driver/Wireless_Atheros.zip") instead--load net5211.inf.  According to the [ndiswrapper database]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_a/"), this driver works for your chipset, according to its device ID (168C:001C).

If it still doesn't work with this new driver after a reboot, please post:
```

dmesg | grep -e ndiswrapper -e wlan -e net5211
lsmod | grep ndis
```

---

### Post by epiphonygirl on 2008-08-04
neither of those commands yield anything...not even an error. naturally my wireless still doesn't work. lol

---

### Post by pytheas22 on 2008-08-04
Alright, please post this then:

```
sudo modprobe -v ndiswrapper
lsmod | grep ndis
sleep 5; dmesg | grep -e ndiswrapper -e wlan -e net5211
```

I think I know what's going on; hopefully this will confirm it and we'll be at a solution.

---

### Post by epiphonygirl on 2008-08-04
```
melissafrench@melissafrench-laptop:~$ sudo modprobe -v ndiswrapper
[sudo] password for melissafrench: 
insmod /lib/modules/2.6.24-19-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko 
melissafrench@melissafrench-laptop:~$ lsmod | grep ndis
ndiswrapper           192920  0 
usbcore               146028  6 ndiswrapper,usb_storage,libusual,ehci_hcd,uhci_hcd
melissafrench@melissafrench-laptop:~$ sleep 5; dmesg | grep -e ndiswrapper -e wlan -e net5211
[  507.517874] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[  507.555668] ndiswrapper: driver net5211 (,05/02/2007,5.3.0.45) loaded
[  507.556248] ndiswrapper (ZwClose:2227): closing handle 0xc7ac1828 not implemented
[  507.969072] ndiswrapper: using IRQ 20
[  508.055020] wlan0: ethernet device 00:1f:3a:8f:13:96 using serialized NDIS driver: net5211, version: 0x50003, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 168C:001C.5.conf
[  508.060224] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[  508.060642] usbcore: registered new interface driver ndiswrapper
[  508.139154] ADDRCONF(NETDEV_UP): wlan0: link is not ready
melissafrench@melissafrench-laptop:~$ 

```

---

### Post by epiphonygirl on 2008-08-04
ooo I was just looking in my device manager and now i see that an ethernet controller preciously marked as networking interface is now marked as WLAN interface :D if that means anything.

---

### Post by epiphonygirl on 2008-08-04
OOO I have a wireless connection listed in my network settings...but I'm having trouble connecting. It is a WEP connection.

---

### Post by epiphonygirl on 2008-08-04
hmm, I can't configure it in network tools...i get an error that says that "the interface does not exist check that it is correctly typed and that it is correctly supported by your system"

---

### Post by pytheas22 on 2008-08-04
> OOO I have a wireless connection listed in my network settings...but I'm having trouble connecting. It is a WEP connection.

Yes, that makes sense--it wasn't working before because the ndiswrapper module wasn't getting loaded for whatever reason.  So running:
```

sudo modprobe ndiswrapper
```

loads ndiswrapper and makes the wireless interface recognized (if you restart your system, you will have to manually load ndiswrapper again for now, but we can apply the fix permanently later).

I'm not sure why you can't connect, though.  What happens exactly when you try?

Also, if you post the output of:
```

iwlist scan
```

and tell us the name of your wireless network, we can give you commands to try connecting manually, via the command-line, which may help.  It could also be useful to turn off encryption on your router if possible to see if you get connected then.

Finally, it would be useful if you tried to connect a few times, then immediately ran this command and posted the output:
```

dmesg | grep -e ndiswrapper -e wlan -e net5211
```

Sorry this is turning out to be so complicated, but I think we're close to a solution; thanks for sticking with it so far.

---

### Post by dmizer on 2008-08-04
Also, try entering your wep key in HEX format instead of using the passphrase.

---

### Post by epiphonygirl on 2008-08-04
Ok, so I go into system>administration>network then I choose my wireless connection with my ethernet cable unplugged and my hardware switch in the on or off position I select Wireless connection and select my WEP protected network and enter in my password for that network I have tried the static IP, IPV4 and DHCP settings none of which seem to get me on. It does its little busy sign with the mouse (what is that called?) and then there is a check mark next to the wireless connection. However when I try to go to a webpage like google firefox just times out and says that a connection could not be established. and here are the outputs you requested (I tried to connect a few times before I ran the dmesg... one and the name of the network is 10134. I put the commands in red so you can determine easily where one ends and the other begins.

```
[COLOR="Red"]melissafrench@melissafrench-laptop:~$ sudo iwlist scan[/COLOR]
[sudo] password for melissafrench:
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1F:33:32:96:EA
                    ESSID:"1-800-GEEKSQUAD"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:7/100  Signal level:-91 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 00:1E:E5:58:A3:93
                    ESSID:"Roomie Network"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:43/100  Signal level:-68 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 03 - Address: 00:12:0E:8B:4D:61
                    ESSID:"10134"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:73/100  Signal level:-49 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=200
                    Extra:atim=0
          Cell 04 - Address: 00:1C:DF:A9:2C:FB
                    ESSID:"Belkin_N_Wireless_A92CFB"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:45/100  Signal level:-67 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 12 Mb/s
                              24 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: 00:16:B6:02:8E:1D
                    ESSID:"shalog"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:4/100  Signal level:-93 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 06 - Address: 00:1E:2A:D9:B6:BA
                    ESSID:"Pickle"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:14/100  Signal level:-87 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 07 - Address: 00:1C:10:04:39:BA
                    ESSID:"Tough Guys"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:26/100  Signal level:-79 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: 00:09:5B:DD:65:08
                    ESSID:"NETGEAR"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:21/100  Signal level:-82 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 09 - Address: 00:1F:C6:29:3B:4D
                    ESSID:"1009 state #5"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:54/100  Signal level:-61 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 10 - Address: 00:1A:92:98:E1:C3
                    ESSID:"House of power"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:32/100  Signal level:-75 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 11 - Address: 00:1B:2F:5E:2C:78
                    ESSID:"NETGEAR"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:29/100  Signal level:-77 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: 00:18:39:C3:CC:7A
                    ESSID:"linksys_SES_48626"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:7/100  Signal level:-91 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 13 - Address: 00:18:39:EF:AB:C2
                    ESSID:"The Millyway"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:12/100  Signal level:-88 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 14 - Address: 00:1E:8C:2E:A8:F2
                    ESSID:"guy"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:12/100  Signal level:-88 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 15 - Address: 00:11:D8:D1:AC:33
                    ESSID:"greis"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.452 GHz (Channel 9)
                    Quality:7/100  Signal level:-91 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 16 - Address: 00:1C:10:28:C7:84
                    ESSID:"VictorEchoNovember"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:26/100  Signal level:-79 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 17 - Address: 00:14:BF:10:9D:60
                    ESSID:"LAX Tennis"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:1/100  Signal level:-95 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s

[COLOR="Red"]melissafrench@melissafrench-laptop:~$ dmesg | grep -e ndiswrapper -e wlan -e net5211[/COLOR]
[  507.517874] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[  507.555668] ndiswrapper: driver net5211 (,05/02/2007,5.3.0.45) loaded
[  507.556248] ndiswrapper (ZwClose:2227): closing handle 0xc7ac1828 not implemented
[  507.969072] ndiswrapper: using IRQ 20
[  508.055020] wlan0: ethernet device 00:1f:3a:8f:13:96 using serialized NDIS driver: net5211, version: 0x50003, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 168C:001C.5.conf
[  508.060224] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[  508.060642] usbcore: registered new interface driver ndiswrapper
[  508.139154] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2570.048700] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2646.279024] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2779.418846] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2957.669283] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2959.951899] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3065.496675] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3370.952671] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3371.022849] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3381.862346] wlan0: no IPv6 routers present
[ 3589.507624] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3589.609720] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3599.893891] wlan0: no IPv6 routers present
[ 3644.703681] wlan0: no IPv6 routers present
[ 3816.296475] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3818.529123] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3822.126967] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3833.038768] wlan0: no IPv6 routers present
[ 3880.032849] wlan0: no IPv6 routers present
[ 4083.279292] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4083.307998] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 4093.746409] wlan0: no IPv6 routers present
melissafrench@melissafrench-laptop:~$ 

```

---

### Post by dmizer on 2008-08-04
Try this:
```
sudo iwlist wlan0 scan&& sudo iwconfig wlan0 channel 6 essid 10134 mode Managed key open XXXXXXXXXXXXXXXX&& sudo ifup wlan0
```

Replace "XXXXXXXXXXXXXXXX" with your wep key in HEX.

Check to see if you get an IP address with this command:
```
sudo ifconfig
```

---

### Post by epiphonygirl on 2008-08-04
Yeah, I don't exactly know HEX at all if you could give me an example that would be great...the key is 10 digits long, so how would I enter that in hex

---

### Post by pytheas22 on 2008-08-04
Thanks for all that information.

First of all, please try enabling roaming mode and see if you can connect that way by going to Network Manager (the applet in the top-right corner of the screen) and clicking on your network (left-click on the NM applet to see the list of networks).  Sometimes things work better in roaming mode.

If that doesn't help, please run these commands, which should connect you manually:
```

sudo iwconfig wlan0 mode managed rate 11M channel 6 essid "10134" key "your hex key, including colons, all in quotes"
sudo dhclient wlan0
```

Note that I'm assuming that your WEP key is hexadecimal, i.e., it looks like "AB:CD:EF:..."  If it's ASCII (a word), let me know.

Please post the output of that stuff.  Hopefully it will get you an IP!

---

### Post by pytheas22 on 2008-08-04
> Yeah, I don't exactly know HEX at all if you could give me an example that would be great...the key is 10 digits long, so how would I enter that in hex

You don't have to convert your key to hex or anything; you just enter it as it is.  It could be the case that your key isn't actually in hex form; it's not so common, but some WEP keys are in ASCII form.  If it's hex, it should include only the digits 0-9 and letters A-G (I think).  If yours is all digits, you probably write it something like:
```

01:23:45:67:89:01
```

So does it seem to make sense to you that it's hex?  If you're still not sure, you could private-message the key to dmizer or me, if you're comfortable with that, so we can tell you.

---

### Post by epiphonygirl on 2008-08-04
It Worked!! to enable roaming and then select wireless networks from that and put in the name and the wepkey. I will look back through the thread and outline what we had to do to make it work.

---

### Post by epiphonygirl on 2008-08-04
ok, so how do we make ndiswrapper load the driver at startup? since it doesn't do that yet.

---

### Post by dmizer on 2008-08-04
You should be able to look at your router's configuration page for the wep key entry, and you should see the HEX format for your key.  It will look something like this:
```
2c7c5221662b2476684a3e3231
```
The above is a 128 bit hex WEP key.

---

### Post by dmizer on 2008-08-04
> **epiphonygirl said:**
> ok, so how do we make ndiswrapper load the driver at startup? since it doesn't do that yet.

That is absolutely fantastic!

Run this command and ndiswrapper will load on boot:
```
echo "ndiswrapper" | sudo tee -a /etc/modules
```

---

### Post by pytheas22 on 2008-08-04
> It Worked!! to enable roaming and then select wireless networks from that and put in the name and the wepkey. I will look back through the thread and outline what we had to do to make it work.

Good to hear.  I think the problem for quite a while may have been failure to load the ndiswrapper module at boot.  You obviously did a lot of stuff here before getting it to work, but I think that the last time you installed ndiswrapper, it probably would have worked even with the first Windows driver that you loaded into there; the one that I told you to install may not have been necessary (but at least you know that that one works).

So basically, I think the steps are:

1. blacklist ath_pci
2. install ndiswrapper
3. load the Windows driver from the acer website
4. run dmizer's command to be sure that ndiswrapper gets loaded at boot
5. connect!

---

### Post by epiphonygirl on 2008-08-04
yeah, something just broke when I ran > ```
echo "ndiswrapper" | sudo tee -a /etc/modules
``` my network monitor disappeared from by the clock after I tried to connect to my wireless and it timed out. Now I can't get the wireless or the wired connection to use roaming mode either...the checkbox is just gone and has been replaced with enable blah blah connection :confused:

---

### Post by epiphonygirl on 2008-08-04
dmitzer after I ran your command and rebooted I tried to connect to the wireless the same way I just did and it timed out and I tried again and then I tried one more time then I clicked cancel and it deleted the network monitor from by my clock! Also, in network I only have an option to enable my wireless and my wired connection and there is no roaming option available. Help! lol

---

### Post by dmizer on 2008-08-04
That shouldn't have broken anything.

Please post the results of:
```
cat /etc/modules
```

---

### Post by epiphonygirl on 2008-08-04
Yeah, I know it shouldn't have and now all that I can use for interfaces according to network monitor is "wlan0:avahi" "eth0:avahi" and "lo" all of which have 169.XXXX.XXXX.XXXX IP addresses when all of mine should be 192.168.XXXX.XXXX As a result I cannot even access the net wired or wirelessly. here is the output...yay for flash drives.

```
melissafrench@melissafrench-laptop:~$ cat /etc/modules 
# /etc/modules: kernel modules to load at boot time. 
# 
# This file contains the names of kernel modules that should be loaded 
# at boot time, one per line. Lines beginning with "#" are ignored. 

fuse 
lp 
ndiswrapper* 
ndiswrapper 
melissafrench@melissafrench-laptop:~$ 
```
I see ndiswrapper twice...would that have something to do with the odd configurations possibly?

---

### Post by dmizer on 2008-08-04
Indeed it would seem so.

Open the file with this command:
```
gksudo gedit /etc/modules
```
delete the "ndiswrapper*" line, save the file, and reboot.

---

### Post by epiphonygirl on 2008-08-04
ok so i got rid of the extra ndiswrapper module and now it all seems fine except I can't seem to connect to my network. I checked my router and I have a 64bit hex wepkey. All it does is seem to sit there.

---

### Post by Hyper Tails on 2008-08-04
I hope this topic helps you 
[http://ubuntuforums.org/showthread.php?t=815467](http://ubuntuforums.org/showthread.php?t=815467)
good luck ;)

---

### Post by epiphonygirl on 2008-08-04
When I run sudo iwlist scan

```
melissafrench@melissafrench-laptop:~$ sudo iwlist scan 
[sudo] password for melissafrench: 
lo        Interface doesn't support scanning. 

eth0      Interface doesn't support scanning. 

wlan0     No scan results 

melissafrench@melissafrench-laptop:~$ dmesg | grep -ewlan -e net5211 
[   33.720267] ndiswrapper: driver net5211 (,05/02/2007,5.3.0.45) loaded 
[   34.140616] wlan0: ethernet device 00:1f:3a:8f:13:96 using serialized NDIS driver: net5211, version: 0x50003, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 168C:001C.5.conf 
[   34.146872] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK 
[   45.456936] ADDRCONF(NETDEV_UP): wlan0: link is not ready 
[   73.071938] ADDRCONF(NETDEV_UP): wlan0: link is not ready 
[   79.199843] ADDRCONF(NETDEV_UP): wlan0: link is not ready 
melissafrench@melissafrench-laptop:~$ 
```

---

### Post by epiphonygirl on 2008-08-04
I'm conducting an experiment...will I be able to get on the wireless if I leave the hardware switch on and tell it to reboot? That and the extra module of ndis wrapper seems to be the issue...

and the verdict: no, the switch must be off and then only be turned on after ubuntu has loaded and the user has logged in. 

Now everything works!!

Thanks, I really appreciated how you both stuck with me through all of this. I guess perseverance pays off in the end.

---

### Post by dmizer on 2008-08-04
I glad YOU stuck to it.  Congratulations!

---

### Post by epiphonygirl on 2008-08-04
Ok so here is my comprehensive guide to getting wireless to work on an R61e Thinkpad. Firstly, I would like to thank my mentors dmizer and pytheas22 otherwise this guide would not have been written. This is a first draft so if there are any large errors please feel free to message me so that I can fix them. 

Open the attachment using either open office writer or msword (the file was too large to upload as an open office writer file so I, sadly, had to go to word. All the same I hope that this solves some problems :D

---

### Post by stevenpusser on 2008-08-16
Hmm, I use Mepis, another debian based distro, and a lappy with the evil 242x (ar5007eg) chipset.  I have got a native madwifi module built rather easily--even a sharable .deb!  This should also work in Ubuntu.

Install your kernel headers and build-essentials, also module-assistant.

Go to packages.debian.org and grab the .deb from unstable (sid) of the madwifi-source package.  This will only install a source package in /usr/src, so you can use it in both 32 and 64 bit.  Install it.  Uninstall ndiswrapper.

open a terminal

sudo m-a prepare   (checks to see if everything's set up OK)
sudo m-a update
sudo m-a a-i madwifi-source

The last command will build and install the madwifi-modules.  

As a bonus, you will have some debs in the /usr/source folder that you can share with people using the same kernel.  You'll get some kudos!  I get a ghost wifi0 interface and a real ath0 using this driver, this is normal--but I have to tell my network monitoring applets to use the wifi0, otherwise ath0 reports twice the real speed!

---

### Post by Mäx on 2008-08-18
Well done epiphonygirl.
Worked for my Fujitsu Siemens ESPRIMO Mobile V5535 too.
I used a different source to get the driver: [http://support.fujitsu-siemens.de/de/support/downloads.html](http://support.fujitsu-siemens.de/de/support/downloads.html) 
but it turned out to be the same *.inf file in the end.
Thanks very much!
Mäx

---

