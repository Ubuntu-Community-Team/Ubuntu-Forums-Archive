---
title: "I can't connect my laptop with wireless"
date: 2008-06-29
forum: Networking &amp; Wireless
---

### Post by chanfle on 2008-06-29
Hi all,
Last week i can connect my laptop in wireless with ubuntu 7.10, but i upgrade mi system and after i can't connect.
This is my information:
```
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```
$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results


```

any comments...??

---

### Post by pytheas22 on 2008-06-29
Please post the output of:
```

lshw -C Network
```

Also did you have to do anything special to make the wireless work when you first installed Ubuntu, or did it "just work?"

---

### Post by untermensch on 2008-06-29
Also, What wireless card do you have?

---

### Post by chanfle on 2008-06-29
thanks for your replays....
```
lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 00:19:7e:88:a2:ff
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net5211 driverversion=1.52+,10/17/2006,5.1.1.7 latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:08:02.0
       logical name: eth0
       version: 10
       serial: 00:1b:24:3d:5f:62
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.67 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes

```

my wireless is:
Wireless ATHEROS AR5007EG

Also did you have to do anything special to make the wireless work when you first installed Ubuntu, or did it "just work?"
- non special connection, is normal my acces point....WEP, and password

thanks

---

### Post by pytheas22 on 2008-06-29
Thanks for the information.  I see that you are using ndiswrapper (you must have had to configure this when you first installed Ubuntu, right?).  To make sure everything is alright with this, please also post the output of:
```

ndiswrapper -l
cat /etc/modprobe.d/blacklist
lsmod | grep ath

```

Also, could you please describe in more detail your problem?  Are you able to see wireless networks but not connect?  Can you connect but not view web pages?  Can you not see any wireless networks at all?

---

### Post by chanfle on 2008-06-29
> **pytheas22 said:**
> Thanks for the information.  I see that you are using ndiswrapper (you must have had to configure this when you first installed Ubuntu, right?).  To make sure everything is alright with this, please also post the output of:
```

ndiswrapper -l
cat /etc/modprobe.d/blacklist
lsmod | grep ath

```

Also, could you please describe in more detail your problem?  Are you able to see wireless networks but not connect?  Can you connect but not view web pages?  Can you not see any wireless networks at all?


hi pytheas22,
yes i ise ndiswrapper and when install ubuntu 8.04 i can configure first time...
I can't see the wireless network...
but when configure "new wireless network" i type the acces point name and the password, not connect...
```
ndiswrapper -l
net5211 : driver installed
	device (168C:001C) present (alternate driver: ath_pci)

```

```
 more /etc/modprobe.d/blacklist
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

blacklist ath_pci

```

thanks

---

### Post by pytheas22 on 2008-06-29
I'm not positive what's wrong, but here are a few things to try.

1. Try opening a terminal and typing:
```

sudo gedit /etc/modprobe.d/blacklist
```

add to the bottom of the file these lines:
```

blacklist ath_rate_sample
blacklist wlan
blacklist ath_hal
```

save the file, reboot and see if it helps.

2. if that doesn't work, you can wipe out ndiswrapper and do a fresh install using the ndiswrapper from Ubuntu 7.10, since you know it worked then (unless you compiled it from source; did you?):

```
sudo apt-get remove --purge ndiswrapper*
wget [http://ubuntu.secs.oakland.edu/pool/main/n/ndiswrapper/ndiswrapper-common_1.43-1ubuntu2_all.deb](http://ubuntu.secs.oakland.edu/pool/main/n/ndiswrapper/ndiswrapper-common_1.43-1ubuntu2_all.deb)
sudo dpkg --install ndiswrapper-common*
wget [http://ubuntu.secs.oakland.edu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.43-1ubuntu2_i386.deb](http://ubuntu.secs.oakland.edu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.43-1ubuntu2_i386.deb)
sudo dpkg --install ndiswrapper-utils*
wget [http://ubuntu.secs.oakland.edu/pool/universe/n/ndisgtk/ndisgtk_0.7.2-1ubuntu1_i386.deb](http://ubuntu.secs.oakland.edu/pool/universe/n/ndisgtk/ndisgtk_0.7.2-1ubuntu1_i386.deb)
sudo dpkg --install ndisgtk*
```

then reinstall your Windows drivers into ndiswrapper and reboot.

3. if it still doesn't work, please post the output of:
```

dmesg | grep -e wlan -e ndis
```

---

### Post by wabbalee on 2008-06-29
code:
ndiswrapper -l
net5211 : driver installed
	device (168C:001C) present (alternate driver: ath_pci)

just a question: (see this thread why [http://ubuntuforums.org/showthread.php?t=814117](http://ubuntuforums.org/showthread.php?t=814117) post #6) should the alternate driver be installed? i don't think alternate driver and windows driver through ndiswrapper can co-exist one the same system.

---

### Post by pytheas22 on 2008-06-29
> just a question: (see this thread why [http://ubuntuforums.org/showthread.php?t=814117](http://ubuntuforums.org/showthread.php?t=814117) post #6) should the alternate driver be installed? i don't think alternate driver and windows driver through ndiswrapper can co-exist one the same system.

You're essentially right; you can't have both drivers *active* at the same time.  But they can both be "installed" insofar as they can both be present on your hard drive.

As long as the native drivers are included in the file /etc/modprobe.d/blacklist, they will be ignored and will not interfere with ndiswrapper.  chanfle has ath_pci blacklisted, and I suggested in my last post that the other three modules related to the native Atheros driver also be blacklisted.  In principle it should suffice to only blacklist ath_pci, but it's possible that ath_hal, wlan or ath_rate_sample could still be interfering with ndiswrapper.

---

### Post by buccaneere on 2008-06-29
You might have already gotten a correct interface configuration in place, but the networking needed to be re-started. I've had 3 machines, 2 with Atheros, and 1 with Broadcom, that had to have networking restarted after configuring the interface. No tellin' how many times I had it right before I learned this.

Script courtesy of wieman01
> sudo /etc/init.d/networking restart

---

### Post by chanfle on 2008-07-04
hello...
I follow your comments but on this moment I can't connect my laptop with the wireless.....
any update?
thanks

---

### Post by pytheas22 on 2008-07-05
If you tried the suggestions above and still have no luck, I suspect that something weird is happening, because from all of the output you've given, things appear to be working normally.  The only other place to look is dmesg.  Please try to connect two or three times to your wireless network, then immediately run this command:
```

dmesg
```

and please post the output from it here.  It will be long, but it's useful.

---

### Post by chanfle on 2008-07-05
> **pytheas22 said:**
> If you tried the suggestions above and still have no luck, I suspect that something weird is happening, because from all of the output you've given, things appear to be working normally.  The only other place to look is dmesg.  Please try to connect two or three times to your wireless network, then immediately run this command:
```

dmesg
```

and please post the output from it here.  It will be long, but it's useful.

this is the output
```
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2200.097 MHz processor.
[   12.784616] Console: colour VGA+ 80x25
[   12.784619] console [tty0] enabled
[   12.784889] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   12.785195] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   12.795638] Memory: 765948k/784960k available (2177k kernel code, 18416k reserved, 1006k data, 368k init, 0k highmem)
[   12.795645] virtual kernel memory layout:
[   12.795646]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   12.795647]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   12.795648]     vmalloc : 0xf0800000 - 0xff7fe000   ( 239 MB)
[   12.795649]     lowmem  : 0xc0000000 - 0xefe90000   ( 766 MB)
[   12.795650]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[   12.795651]       .data : 0xc0320434 - 0xc041bdc4   (1006 kB)
[   12.795652]       .text : 0xc0100000 - 0xc0320434   (2177 kB)
[   12.795655] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   12.795681] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   12.875629] Calibrating delay using timer specific routine.. 4404.55 BogoMIPS (lpj=8809114)
[   12.875649] Security Framework initialized
[   12.875653] SELinux:  Disabled at boot.
[   12.875663] AppArmor: AppArmor initialized
[   12.875667] Failure registering capabilities with primary security module.
[   12.875673] Mount-cache hash table entries: 512
[   12.875754] Initializing cgroup subsys ns
[   12.875757] Initializing cgroup subsys cpuacct
[   12.875764] CPU: After generic identify, caps: 078bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000001d 00000000
[   12.875772] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   12.875774] CPU: L2 Cache: 512K (64 bytes/line)
[   12.875776] CPU: After all inits, caps: 078bfbff ebd3fbff 00000000 00000410 00002001 00000000 0000001d 00000000
[   12.875783] Compat vDSO mapped to ffffe000.
[   12.875791] Checking 'hlt' instruction... OK.
[   12.891831] SMP alternatives: switching to UP code
[   12.892721] Freeing SMP alternatives: 11k freed
[   12.892813] Early unpacking initramfs... done
[   13.167327] ACPI: Core revision 20070126
[   13.167398] ACPI: Looking for DSDT in initramfs... successfully read 25216 bytes from /DSDT.aml.
[   13.167424] ACPI: Table DSDT replaced by host OS
[   13.167427] ACPI: DSDT 00000000, 6280 (r1    ATI    SB460  6040000 INTL 20061109)
[   13.167431] ACPI: DSDT override uses original SSDTs unless "acpi_no_auto_ssdt"CPU0: AMD Turion(tm) 64 Mobile Technology MK-38 stepping 02
[   13.640535] Total of 1 processors activated (4404.55 BogoMIPS).
[   13.640698] ENABLING IO-APIC IRQs
[   13.640874] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[   13.786830] Brought up 1 CPUs
[   13.786846] CPU0 attaching sched-domain:
[   13.786849]  domain 0: span 01
[   13.786850]   groups: 01
[   13.786985] net_namespace: 64 bytes
[   13.786990] Booting paravirtualized kernel on bare hardware
[   13.787371] Time: 15:10:43  Date: 07/05/08
[   13.787390] NET: Registered protocol family 16
[   13.787529] EISA bus registered
[   13.787553] ACPI: bus type pci registered
[   13.803287] PCI: BIOS BUG #81[49435000] found
[   13.803329] PCI: Using configuration type 1
[   13.803334] Setting up standard PCI resources
[   13.804673] ACPI: EC: Look up EC in DSDT
[   13.806754] ACPI: Interpreter enabled
[   13.806756] ACPI: (supports S0 S3 S4 S5)
[   13.806765] ACPI: Using IOAPIC for interrupt routing
[   13.807093] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   13.829977] ACPI: EC: GPE = 0x14, I/O: command/status = 0x66, data = 0x62
[   13.829979] ACPI: EC: driver started in interrupt mode
[   13.830008] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   13.831789] PCI: Transparent bridge - 0000:00:14.4
[   13.831863] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   13.831992] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB4_._PRT]
[   13.832083] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB5_._PRT]
[   13.832172] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB6_._PRT]
[   13.832262] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB7_._PRT]
[   13.832356] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[   13.832456] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[   13.834515] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[   13.834611] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[   13.834709] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[   13.834810] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[   13.834908] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[   13.835007] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[   13.835105] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[   13.835203] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[   13.835300] ACPI: PCI Interrupt Link [LNKU] (IRQs 3 4 5 7) *0, disabled.
[   13.835393] Linux Plug and Play Support v0.97 (c) Adam Belay
[   13.835416] pnp: PnP ACPI init
[   13.835421] ACPI: bus type pnp registered
[   13.837085] pnp: PnP ACPI: found 10 devices
[   13.837087] ACPI: ACPI bus type pnp unregistered
[   13.837090] PnPBIOS: Disabled by ACPI PNP
[   13.837250] PCI: Using ACPI for IRQ routing
[   13.837252] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   13.837257] PCI: Cannot allocate resource region 7 of bridge 0000:00:05.0
[   13.837259] PCI: Cannot allocate resource region 8 of bridge 0000:00:05.0
[   13.837261] PCI: Cannot allocate resource region 7 of bridge 0000:00:06.0
[   13.837263] PCI: Cannot allocate resource region 8 of bridge 0000:00:06.0
[   13.837265] PCI: Cannot allocate resource region 7 of bridge 0000:00:07.0
[   13.837267] PCI: Cannot allocate resource region 8 of bridge 0000:00:07.0
[   13.838855] NET: Registered protocol family 8
[   13.838857] NET: Registered protocol family 20
[   13.838910] AppArmor: AppArmor Filesystem Enabled
[   13.842744] Time: tsc clocksource has been installed.
[   13.850765] system 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
[   13.850768] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
[   13.850770] system 00:01: iomem range 0xfee00000-0xfee00fff could not be reserved
[   13.850777] system 00:08: ioport range 0x1080-0x1080 has been reserved
[   13.850779] system 00:08: ioport range 0x220-0x22f has been reserved
[   13.850781] system 00:08: ioport range 0x40b-0x40b has been reserved
[   13.850784] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[   13.850786] system 00:08: ioport range 0x4d6-0x4d6 has been reserved
[   13.850788] system 00:08: ioport range 0x530-0x537 has been reserved
[   13.850790] system 00:08: ioport range 0xc00-0xc01 has been reserved
[   13.850793] system 00:08: ioport range 0xc14-0xc14 has been reserved
[   13.850795] system 00:08: ioport range 0xc50-0xc52 has been reserved
[   13.850797] system 00:08: ioport range 0xc6c-0xc6c has been reserved
[   13.850799] system 00:08: ioport range 0xc6f-0xc6f has been reserved
[   13.850804] system 00:08: ioport range 0xcd4-0xcd5 has been reserved
[   13.850806] system 00:08: ioport range 0xcd6-0xcd7 has been reserved
[   13.850808] system 00:08: ioport range 0xcd8-0xcdf has been reserved
[   13.850811] system 00:08: ioport range 0x8000-0x805f has been reserved
[   13.850813] system 00:08: ioport range 0xf40-0xf47 has been reserved
[   13.850815] system 00:08: ioport range 0x87f-0x87f has been reserved
[   13.850820] system 00:09: iomem range 0xe0000-0xfffff could not be reserved
[   13.850822] system 00:09: iomem range 0xfff00000-0xffffffff could not be reserved
[   13.850825] system 00:09: iomem range 0x0-0xfff could not be reserved
[   13.881114] PCI: Bridge: 0000:00:01.0
[   13.881116]   IO window: 9000-9fff
[   13.881119]   MEM window: b0100000-b01fffff
[   13.881121]   PREFETCH window: c0000000-cfffffff
[   13.881124] PCI: Bridge: 0000:00:04.0
[   13.881125]   IO window: disabled.
[   13.881127]   MEM window: b0200000-b02fffff
[   13.881129]   PREFETCH window: disabled.
[   13.881131] PCI: Bridge: 0000:00:05.0
[   13.881132]   IO window: disabled.
[   13.881134]   MEM window: disabled.
[   13.881136]   PREFETCH window: disabled.
[   13.881138] PCI: Bridge: 0000:00:06.0
[   13.881139]   IO window: disabled.
[   13.881141]   MEM window: disabled.
[   13.881143]   PREFETCH window: disabled.
[   13.881145] PCI: Bridge: 0000:00:07.0
[   13.881146]   IO window: disabled.
[   13.881148]   MEM window: disabled.
[   13.881149]   PREFETCH window: disabled.
[   13.881161] PCI: Bus 9, cardbus bridge: 0000:08:01.0
[   13.881163]   IO window: 0000a400-0000a4ff
[   13.881168]   IO window: 0000a800-0000a8ff
[   13.881174]   PREFETCH window: 54000000-57ffffff
[   13.881179]   MEM window: 58000000-5bffffff
[   13.881184] PCI: Bridge: 0000:00:14.4
[   13.881187]   IO window: a000-afff
[   13.881193]   MEM window: b0300000-b03fffff
[   13.881197]   PREFETCH window: disabled.
[   13.881214] PCI: Enabling device 0000:00:04.0 (0000 -> 0002)
[   13.881217] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   13.881224] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   13.881230] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   13.881237] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   13.881259] PCI: Enabling device 0000:08:01.0 (0000 -> 0003)
[   13.881265] ACPI: PCI Interrupt 0000:08:01.0[A] -> GSI 23 (level, low) -> IRQ 16
[   13.881281] NET: Registered protocol family 2
[   13.918733] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   13.918970] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   13.919572] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   13.919853] TCP: Hash tables configured (established 131072 bind 65536)
[   13.919855] TCP reno registered
[   13.930775] checking if image is initramfs... it is
[   14.382253] Switched to high resolution mode on CPU 0
[   14.460807] Freeing initrd memory: 7332k freed
[   14.460922] Simple Boot Flag at 0x36 set to 0x1
[   14.461276] audit: initializing netlink socket (disabled)
[   14.461287] audit(1215270643.092:1): initialized
[   14.462710] VFS: Disk quotas dquot_6.5.1
[   14.462762] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   14.462863] io scheduler noop registered
[   14.462865] io scheduler anticipatory registered
[   14.462866] io scheduler deadline registered
[   14.462874] io scheduler cfq registered (default)
[   14.462880] PCI: MSI quirk detected. MSI deactivated.
[   14.462923] Boot video device is 0000:01:05.0
[   14.463015] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   14.463033] assign_interrupt_mode Found MSI capability
[   14.463036] Allocate Port Service[0000:00:04.0:pcie00]
[   14.463062] Allocate Port Service[0000:00:04.0:pcie02]
[   14.463108] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   14.463125] assign_interrupt_mode Found MSI capability
[   14.463127] Allocate Port Service[0000:00:05.0:pcie00]
[   14.463178] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   14.463195] assign_interrupt_mode Found MSI capability
[   14.463197] Allocate Port Service[0000:00:06.0:pcie00]
[   14.463245] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   14.463262] assign_interrupt_mode Found MSI capability
[   14.463263] Allocate Port Service[0000:00:07.0:pcie00]
[   14.463428] isapnp: Scanning for PnP cards...
[   14.819583] isapnp: No Plug & Play device found
[   14.840732] Real Time Clock Driver v1.12ac
[   14.840805] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   14.841650] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   14.841708] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   14.842252] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[   14.844265] i8042.c: Detected active multiplexing controller, rev 1.1.
[   14.846232] serio: i8042 KBD port at 0x60,0x64 irq 1
[   14.846236] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   14.846238] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   14.846240] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   14.846242] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   14.861782] mice: PS/2 mouse device common for all mice
[   14.861870] EISA: Probing bus 0 at eisa.0
[   14.861879] Cannot allocate resource for EISA slot 1
[   14.861907] Cannot allocate resource for EISA slot 8
[   14.861908] EISA: Detected 0 cards.
[   14.861911] cpuidle: using governor ladder
[   14.861912] cpuidle: using governor menu
[   14.861979] NET: Registered protocol family 1
[   14.861999] Using IPI No-Shortcut mode
[   14.862022] registered taskstats version 1
[   14.862118]   Magic number: 0:587:183
[   14.862167]   hash matches device ttyr9
[   14.862265] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   14.862267] EDD information not available.
[   14.862470] Freeing unused kernel memory: 368k freed
[   14.901713] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   16.054739] fuse init (API version 7.9)
[   16.069531] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   16.072781] ACPI: Thermal Zone [THRM] (33 C)
[   16.592209] SCSI subsystem initialized
[   16.644017] libata version 3.00 loaded.
[   16.646904] usbcore: registered new interface driver usbfs
[   16.646922] usbcore: registered new interface driver hub
[   16.653633] PCI: Enabling device 0000:00:12.0 (0005 -> 0007)
[   16.653643] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 22 (level, low) -> IRQ 17
[   16.653687] ACPI: PCI interrupt for device 0000:00:12.0 disabled
[   16.653706] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 18
[   16.653724] PCI: Setting latency timer of device 0000:00:14.1 to 64
[   16.653732] ACPI: PCI interrupt for device 0000:00:14.1 disabled
[   16.666111] usbcore: registered new device driver usb
[   16.677244] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 18
[   16.691960] scsi0 : pata_atiixp
[   16.700722] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   16.715912] scsi1 : pata_atiixp
[   16.716028] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x8420 irq 14
[   16.716031] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x8428 irq 15
[   16.755926] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   17.036132] ata1.00: ATAPI: HL-DT-ST DVDRAM GSA-T20N, WP03, max UDMA/33
[   17.207921] ata1.00: configured for UDMA/33
[   17.366880] scsi 0:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-T20N  WP03 PQ: 0 ANSI: 5
[   17.368970] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 19
[   17.368982] ohci_hcd 0000:00:13.0: OHCI Host Controller
[   17.369208] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[   17.369226] ohci_hcd 0000:00:13.0: irq 19, io mem 0xb0005000
[   17.374681] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   17.374686] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   17.423320] usb usb1: configuration #1 chosen from 1 choice
[   17.423342] hub 1-0:1.0: USB hub found
[   17.423353] hub 1-0:1.0: 4 ports detected
[   17.527187] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 19
[   17.527200] ohci_hcd 0000:00:13.1: OHCI Host Controller
[   17.527217] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[   17.527232] ohci_hcd 0000:00:13.1: irq 19, io mem 0xb0006000
[   17.583155] usb usb2: configuration #1 chosen from 1 choice
[   17.583175] hub 2-0:1.0: USB hub found
[   17.583186] hub 2-0:1.0: 4 ports detected
[   17.687227] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 19
[   17.687239] ehci_hcd 0000:00:13.2: EHCI Host Controller
[   17.687259] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[   17.687303] ehci_hcd 0000:00:13.2: irq 19, io mem 0xb0007000
[   17.830801] usb 1-1: new low speed USB device using ohci_hcd and address 2
[   17.842793] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   17.842877] usb usb3: configuration #1 chosen from 1 choice
[   17.842894] hub 3-0:1.0: USB hub found
[   17.842899] hub 3-0:1.0: 8 ports detected
[   17.946942] 8139cp 0000:08:02.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[   17.946946] 8139cp 0000:08:02.0: Try the "8139too" driver instead.
[   17.948342] sata_sil 0000:00:12.0: version 2.3
[   17.948375] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 22 (level, low) -> IRQ 17
[   17.949028] 8139too Fast Ethernet driver 0.9.28
[   17.949421] scsi2 : sata_sil
[   17.949729] scsi3 : sata_sil
[   17.950008] ata3: SATA max UDMA/100 mmio m512@0xb0004000 tf 0xb0004080 irq 17
[   17.950012] ata4: SATA max UDMA/100 mmio m512@0xb0004000 tf 0xb00040c0 irq 17
[   18.414254] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   18.422810] ata3.00: ATA-7: ST980811AS, 3.ALD, max UDMA/133
[   18.422812] ata3.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   18.438788] ata3.00: configured for UDMA/100
[   18.530106] usb 1-1: new low speed USB device using ohci_hcd and address 3
[   18.731017] usb 1-1: configuration #1 chosen from 1 choice
[   18.747010] usbcore: registered new interface driver hiddev
[   18.749919] ata4: SATA link down (SStatus 0 SControl 310)
[   18.750018] scsi 2:0:0:0: Direct-Access     ATA      ST980811AS       3.AL PQ: 0 ANSI: 5
[   18.750235] ACPI: PCI Interrupt 0000:08:02.0[A] -> GSI 20 (level, low) -> IRQ 20
[   18.751359] eth0: RealTek RTL8139 at 0xa000, 00:1b:24:3d:5f:62, IRQ 20
[   18.751361] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   18.751856] input: HID 062a:0000 as /devices/pci0000:00/0000:00:13.0/usb1/1-1/1-1:1.0/input/input2
[   18.757585] Driver 'sr' needs updating - please use bus_type methods
[   18.762562] Driver 'sd' needs updating - please use bus_type methods
[   18.765938] input,hidraw0: USB HID v1.10 Mouse [HID 062a:0000] on usb-0000:00:13.0-1
[   18.765952] usbcore: registered new interface driver usbhid
[   18.765955] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   18.775721] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   18.775726] Uniform CD-ROM driver Revision: 3.20
[   18.775764] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   18.779720] sd 2:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   18.779732] sd 2:0:0:0: [sda] Write Protect is off
[   18.779734] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   18.779747] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   18.779784] sd 2:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   18.779791] sd 2:0:0:0: [sda] Write Protect is off
[   18.779793] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   18.779804] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   18.779807]  sda:<5>sr 0:0:0:0: Attached scsi generic sg0 type 5
[   18.781062] sd 2:0:0:0: Attached scsi generic sg1 type 0
[   18.797857]  sda1 sda2 < sda5 >
[   18.822524] sd 2:0:0:0: [sda] Attached SCSI disk
[   19.106581] Attempting manual resume
[   19.106584] swsusp: Resume From Partition 8:5
[   19.106586] PM: Checking swsusp image.
[   19.106734] PM: Resume from disk failed.
[   19.152405] kjournald starting.  Commit interval 5 seconds
[   19.152417] EXT3-fs: mounted filesystem with ordered data mode.
[   30.390389] Linux agpgart interface v0.102
[   30.502281] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   30.538290] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   30.774069] input: PC Speaker as /devices/platform/pcspkr/input/input3
[   30.833978] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[   30.885286] input: Power Button (FF) as /devices/virtual/input/input4
[   30.898079] ACPI: Power Button (FF) [PWRF]
[   30.898178] input: Power Button (CM) as /devices/virtual/input/input5
[   30.909853] ACPI: Power Button (CM) [PWRB]
[   30.909967] input: Lid Switch as /devices/virtual/input/input6
[   30.910837] ACPI: Lid Switch [LID]
[   30.910892] input: Sleep Button (CM) as /devices/virtual/input/input7
[   30.925833] ACPI: Sleep Button (CM) [SLPB]
[   31.056261] ACPI: AC Adapter [ACAD] (on-line)
[   31.162551] ACPI: Battery Slot [BAT1] (battery present)
[   31.397430] Yenta: CardBus bridge found at 0000:08:01.0 [1025:010f]
[   31.397457] Yenta: Using CSCINT to route CSC interrupts to PCI
[   31.397459] Yenta: Routing CardBus interrupts to PCI
[   31.397465] Yenta TI: socket 0000:08:01.0, mfunc 0x00001202, devctl 0x44
[   31.425431] ACPI: WMI-Acer: Mapper loaded
[   31.629900] Yenta: ISA IRQ mask 0x0cf8, PCI irq 16
[   31.629905] Socket status: 30000006
[   31.629908] Yenta: Raising subordinate bus# of parent bus (#08) from #09 to #0c
[   31.629913] pcmcia: parent PCI bridge I/O window: 0xa000 - 0xafff
[   31.629916] cs: IO port probe 0xa000-0xafff: clean.
[   31.630160] pcmcia: parent PCI bridge Memory window: 0xb0300000 - 0xb03fffff
[   31.652819] sdhci: Secure Digital Host Controller Interface driver
[   31.652823] sdhci: Copyright(c) Pierre Ossman
[   31.696650] sdhci: SDHCI controller found at 0000:08:01.2 [1524:0550] (rev 1)
[   31.696675] ACPI: PCI Interrupt 0000:08:01.2[B] -> GSI 22 (level, low) -> IRQ 17
[   31.696730] mmc0: SDHCI at 0xb0301400 irq 17 PIO
[   31.696737] sdhci: SDHCI controller found at 0000:08:01.4 [1524:0551] (rev 1)
[   31.696755] PCI: Enabling device 0000:08:01.4 (0000 -> 0002)
[   31.696759] ACPI: PCI Interrupt 0000:08:01.4[B] -> GSI 22 (level, low) -> IRQ 17
[   31.696792] mmc1: SDHCI at 0xb0301100 irq 17 PIO
[   32.335862] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1280b1, caps: 0xa04713/0x204000
[   32.380037] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input8
[   32.765420] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   32.902277] [fglrx] Maximum main memory to use for locked dma buffers: 678 MBytes.
[   32.902308] [fglrx] ASYNCIO init succeed!
[   32.902406] [fglrx] PAT is enabled successfully!
[   32.905861] [fglrx] module loaded - fglrx 8.47.3 [Feb 25 2008] on minor 0
[   33.004046] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 18
[   33.291130] acer_acpi: Acer Laptop ACPI Extras version 0.11.1
[   33.291137] acer_acpi: Detected Acer WMID interface
[   34.593739] cs: IO port probe 0x100-0x3af: clean.
[   34.596021] cs: IO port probe 0x3e0-0x4ff: clean.
[   34.596963] cs: IO port probe 0x820-0x8ff: clean.
[   34.597738] cs: IO port probe 0xc00-0xcf7: clean.
[   34.598549] cs: IO port probe 0xa00-0xaff: clean.
[   35.180154] lp: driver loaded but no devices found
[   35.221612] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   35.363305] ndiswrapper: driver net5211 (,10/17/2006,5.1.1.7) loaded
[   35.363495] PCI: Enabling device 0000:02:00.0 (0000 -> 0002)
[   35.363501] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 18
[   35.363544] ndiswrapper (ZwClose:2227): closing handle 0xee908b28 not implemented
[   35.363672] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   35.775648] ndiswrapper: using IRQ 18
[   35.979400] wlan0: ethernet device 00:19:7e:88:a2:ff using serialized NDIS driver: net5211, version: 0x50001, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 168C:001C.5.conf
[   35.984289] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   35.987143] usbcore: registered new interface driver ndiswrapper
[   36.079071] Adding 2265124k swap on /dev/sda5.  Priority:-1 extents:1 across:2265124k
[   36.614198] EXT3 FS on sda1, internal journal
[   37.866891] ip_tables: (C) 2000-2006 Netfilter Core Team
[   38.346265] No dock devices found.
[   38.653914] powernow-k8: Found 1 AMD Turion(tm) 64 Mobile Technology MK-38 processors (1 cpu cores) (version 2.20.00)
[   38.653953] powernow-k8:    0 : fid 0xe (2200 MHz), vid 0xd
[   38.653955] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0xf
[   38.653957] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0x11
[   38.653959] powernow-k8:    3 : fid 0x8 (1600 MHz), vid 0x13
[   38.653961] powernow-k8:    4 : fid 0x0 (800 MHz), vid 0x18
[   39.438591] apm: BIOS not found.
[   39.662046] ppdev: user-space parallel port driver
[   39.845141] audit(1215270669.773:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4970 profile="/usr/sbin/cupsd" namespace="default"
[   55.420128] Marking TSC unstable due to: cpufreq changes.
[   55.424675] Time: acpi_pm clocksource has been installed.
[   55.943868] Clocksource tsc unstable (delta = -136392567 ns)
[   56.010628] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   56.130814] Bluetooth: Core ver 2.11
[   56.131338] NET: Registered protocol family 31
[   56.131342] Bluetooth: HCI device and connection manager initialized
[   56.131346] Bluetooth: HCI socket layer initialized
[   56.171547] Bluetooth: L2CAP ver 2.9
[   56.171552] Bluetooth: L2CAP socket layer initialized
[   56.243695] Bluetooth: RFCOMM socket layer initialized
[   56.243923] Bluetooth: RFCOMM TTY layer initialized
[   56.243927] Bluetooth: RFCOMM ver 1.8
[  115.821608] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 17 (level, low) -> IRQ 21
[   43.482346] NET: Registered protocol family 17
[   43.671623] [fglrx] GART Table is not in FRAME_BUFFER range 
[   43.671632] [fglrx] Reserve Block - 0 offset =  0X0 length = 0X40000
[   43.671635] [fglrx] Reserve Block - 1 offset =  0Xfff5000 length = 0Xb000
[   43.860424] [fglrx] interrupt source 20008000 successfully enabled
[   43.860429] [fglrx] enable ID = 0x00000004
[   43.860679] [fglrx] Receive enable interrupt message with irqEnableMask: 20008000
[  127.315936] NET: Registered protocol family 10
[  127.316904] lo: Disabled Privacy Extensions
[  127.318671] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  132.082748] hda-intel: Invalid position buffer, using LPIB read method instead.
[  139.435722] eth0: no IPv6 routers present
[ 4623.807495] [fglrx:fireglAsyncioIntEnableMsgHandler] *ERROR* IRQMGR returned error 1 when trying to enable interrupt source 20008000
[ 4623.807502] [fglrx] Receive enable interrupt message with irqEnableMask: 20008000
[ 4832.983211] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:593: hda_intel: azx_get_response timeout, switching to polling mode: last cmd=0x106f000a
[ 4833.986158] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:600: hda_intel: azx_get_response timeout, switching to single_cmd mode: last cmd=0x106f000a
[ 7259.192383] ndiswrapper (iw_set_ap_address:575): setting AP mac address failed (00010003)

```
any updates...???

regards...

---

### Post by pytheas22 on 2008-07-05
From the last line of dmesg is this error:
```

ndiswrapper (iw_set_ap_address:575): setting AP mac address failed
```

which indicates a bug in ndiswrapper.  You have a couple of options.  The easiest I think would be to compile ndiswrapper from source, where the bug will hopefully be fixed.  To do that:

First, download the ndiswrapper source package from [http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.46.tar.gz?modtime=1180919462&big_mirror=0](http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.46.tar.gz?modtime=1180919462&big_mirror=0) and save it to your desktop.  Then run:
```

sudo apt-get remove --purge ndiswrapper
sudo apt-get install build essential
cd ~/Desktop
tar -xzvf ndis*
cd ndis*
make
sudo make install
```

You then need to install your Windows drivers inside ndiswrapper again with this command:
```

sudo ndiswrapper -i /location/of/windows/.inf/file
```

then reboot and see if you have better luck.

Also, which version of Ubuntu are you currently using--7.10 or 8.04?

---

### Post by aimwin on 2008-07-05
Have you try this method

[http://ubuntuforums.org/showthread.php?p=5289197#post5289197](http://ubuntuforums.org/showthread.php?p=5289197#post5289197)

Change wpn111 to your card drivers

---

### Post by chanfle on 2008-07-05
> **pytheas22 said:**
> From the last line of dmesg is this error:
```

ndiswrapper (iw_set_ap_address:575): setting AP mac address failed
```

which indicates a bug in ndiswrapper.  You have a couple of options.  The easiest I think would be to compile ndiswrapper from source, where the bug will hopefully be fixed.  To do that:

First, download the ndiswrapper source package from [http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.46.tar.gz?modtime=1180919462&big_mirror=0](http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.46.tar.gz?modtime=1180919462&big_mirror=0) and save it to your desktop.  Then run:
```

sudo apt-get remove --purge ndiswrapper
sudo apt-get install build essential
cd ~/Desktop
tar -xzvf ndis*
cd ndis*
make
sudo make install
```

You then need to install your Windows drivers inside ndiswrapper again with this command:
```

sudo ndiswrapper -i /location/of/windows/.inf/file
```

then reboot and see if you have better luck.

Also, which version of Ubuntu are you currently using--7.10 or 8.04?

when I got install ndiswrapper appear this message:
```
sudo make
make -C driver
make[1]: Entering directory `/home/chanfle/Desktop/ndiswrapper-1.47/driver'
make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/home/chanfle/Desktop/ndiswrapper-1.47/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/home/chanfle/Desktop/ndiswrapper-1.47/driver/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[2]: *** [_module_/home/chanfle/Desktop/ndiswrapper-1.47/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/chanfle/Desktop/ndiswrapper-1.47/driver'
make: *** [all] Error 2

```

why?   and I use 8.04

---

### Post by pytheas22 on 2008-07-06
sorry sorry sorry...I made a typographical mistake in my directions (I wrote "build essential" instead of "build**-**essential").  These are the correct ones:

First, download the ndiswrapper source package from [http://downloads.sourceforge.net/ndi...2&big_mirror=0](http://downloads.sourceforge.net/ndi...2&big_mirror=0) and save it to your desktop. Then run:
Code:
```

sudo apt-get remove --purge ndiswrapper
sudo apt-get install build-essential
cd ~/Desktop
tar -xzvf ndis*
cd ndis*
make
sudo make install
```

You then need to install your Windows drivers inside ndiswrapper again with this command:
Code:
```

sudo ndiswrapper -i /location/of/windows/.inf/file
```

then reboot and see if you have better luck.

I'm really sorry for that and the time it wasted.  The directions above should work.

---

### Post by chanfle on 2008-07-07
> **pytheas22 said:**
> sorry sorry sorry...I made a typographical mistake in my directions (I wrote "build essential" instead of "build**-**essential").  These are the correct ones:

First, download the ndiswrapper source package from [http://downloads.sourceforge.net/ndi...2&big_mirror=0](http://downloads.sourceforge.net/ndi...2&big_mirror=0) and save it to your desktop. Then run:
Code:
```

sudo apt-get remove --purge ndiswrapper
sudo apt-get install build-essential
cd ~/Desktop
tar -xzvf ndis*
cd ndis*
make
sudo make install
```

You then need to install your Windows drivers inside ndiswrapper again with this command:
Code:
```

sudo ndiswrapper -i /location/of/windows/.inf/file
```

then reboot and see if you have better luck.

I'm really sorry for that and the time it wasted.  The directions above should work.

ok no problem...jajaja
let me check this process and later confirm my result....
regards...

---

