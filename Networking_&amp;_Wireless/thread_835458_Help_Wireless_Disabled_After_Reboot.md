---
title: "Help: Wireless Disabled After Reboot"
date: 2008-06-20
forum: Networking &amp; Wireless
---

### Post by waltcoleman on 2008-06-20
First off, thank you all for the immeasurable help in getting my wireless working.  I have the Broadcom BCM94311MCG (rev 1) wireless card in a HP DV6000.  Following instructions posted throughout these forums, I was able to get the wireless working.  I have one remaining wireless issue.

After each reboot, when I start Ubuntu 8.04, the wireless driver is disabled.  I must manually go into System -> Administration -> Hardware Drivers.  The driver is checked, but is listed as "Not in Use".  I manually uncheck the driver to disable it, then check it again the enable it.  At that point, the blue light on the laptop comes on and the wireless card starts functioning and all is well until the next reboot.

Any ideas on why the wireless is not working after reboot?

Any help would be greatly appreciated.

---

### Post by pytheas22 on 2008-06-20
Reboot and before doing anything else, run these commands:

```
modprobe -l | grep bcm43xx
modprobe -l | grep b43
modprobe -l | grep ndiswrapper
```

and please post the output, if any, here.  Then check the box in hardware drivers and run those same commands again, and post the output.  This will help diagnose the problem.  I suspect that there's just a module that's not being automatically loaded when it should.

Also do you remember where the instructions were that you followed to make the card work?

---

### Post by waltcoleman on 2008-06-20
Thanks for the quick response!  Ok, the results before enabling the driver:

localadmin@localadmin-laptop:~$ modprobe -l | grep bcm43xx
/lib/modules/2.6.24-19-generic/kernel/drivers/net/wireless/bcm43xx/bcm43xx.ko

localadmin@localadmin-laptop:~$ modprobe -l | grep b43
/lib/modules/2.6.24-19-generic/kernel/drivers/net/wireless/b43legacy/b43legacy.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/net/wireless/b43/b43.ko

localadmin@localadmin-laptop:~$ modprobe -l | grep ndiswrapper
/lib/modules/2.6.24-19-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko


And the results after enabling the driver:

localadmin@localadmin-laptop:~$ modprobe -l | grep bcm43xx
/lib/modules/2.6.24-19-generic/kernel/drivers/net/wireless/bcm43xx/bcm43xx.ko

localadmin@localadmin-laptop:~$ modprobe -l | grep b43
/lib/modules/2.6.24-19-generic/kernel/drivers/net/wireless/b43legacy/b43legacy.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/net/wireless/b43/b43.ko
l
ocaladmin@localadmin-laptop:~$ modprobe -l | grep ndiswrapper
/lib/modules/2.6.24-19-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko


The process I followed is linked below with one exception. I used ndiswrapper 1.52 because 1.53 was giving me an Error 2 in Step 9 at "make distclean"


[http://ubuntuforums.org/showthread.php?t=769990&highlight=installing+bcm943](http://ubuntuforums.org/showthread.php?t=769990&highlight=installing+bcm943)

Thanks again!

---

### Post by pytheas22 on 2008-06-20
Thanks for the information.  I'm still not entirely sure what's going on, but could you do this please:

Reboot and before doing anything else, type:
```

cat /etc/modprobe.d/blacklist
sudo rmmod --verbose bcm43xx b43 b43legacy
sudo modprobe ndiswrapper
sudo ifconfig wlan0 up
```

and again, please post any output.  Then wait a few seconds and see if the wireless works again.

If it still doesn't work, please try this and post any output:
```

sudo rmmod --verbose ndiswrapper
sudo modprobe b43
sudo ifconfig eth1 up
```

and then see if it works.

Since you got your card working using ndiswrapper, I'm a little confused because the "hardware drivers" utility shouldn't have anything to do with ndiswrapper, as far as I know.  Hardware drivers would be dealing with the b43 driver, the native Linux driver for your card.  So I'm wondering if maybe by default ndiswrapper is trying to drive the card but is failing for some reason, and by unchecking and rechecking the box in hardware drivers, you're forcing the b43 driver to be used.  The output of the commands above should help figure out what's going on.

Also have you always had to do the uncheck/recheck thing to get the wireless working, or did this issue develop all of a sudden?

---

### Post by waltcoleman on 2008-06-20
I've always had to do the uncheck/recheck to get it to work.  Here's the latest output:

localadmin@localadmin-laptop:~$ cat /etc/modprobe.d/blacklist
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
blacklist b43

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

localadmin@localadmin-laptop:~$ sudo rmmod --verbose bcm43xx b43 b43legacy
[sudo] password for localadmin: 
ERROR: Module bcm43xx does not exist in /proc/modules
ERROR: Module b43 does not exist in /proc/modules
ERROR: Module b43legacy does not exist in /proc/modules

localadmin@localadmin-laptop:~$ sudo modprobe ndiswrapper

localadmin@localadmin-laptop:~$ sudo ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device


No blue light at this point, so here's the rest:

localadmin@localadmin-laptop:~$ sudo rmmod --verbose ndiswrapper
rmmod ndiswrapper, wait=no

localadmin@localadmin-laptop:~$ sudo modprobe b43

localadmin@localadmin-laptop:~$ sudo ifconfig eth1 up
eth1: ERROR while getting interface flags: No such device

Thanks!!!

---

### Post by pytheas22 on 2008-06-20
Alright, I see that both bcm43xx and b43 were blacklisted, so I guess that ndiswrapper was driving the card.  I have no idea why you would have to do the uncheck/recheck thing before it works, however.  Also, you shouldn't need ndiswrapper for your card.  So I'm going to recommend that you follow these steps to get the device working with the native Linux driver, which should work fine and is preferable to ndiswrapper anyway.  If this doesn't work it's easy to switch back to ndiswrapper to revert to the point you're at now.  But this should definitely work:

1. add ndiswrapper and b43 modules to blacklist and remove bcm43xx:

```
sudo -s
sed -e 's/bcm43xx/ndiswrapper/' /etc/modprobe.d/blacklist
echo 'blacklist ssb' >> /etc/modprobe.d/blacklist
echo 'blacklist b43legacy' >> /etc/modprobe.d/blacklist
echo 'blacklist b43' >> /etc/modprobe.d/blacklist
echo 'blacklist b43 ssb' >> /etc/modprobe.d/blacklist
```

2. remove b43 firmware if it exists (it probably doesn't, but just in case you installed it at some point):
```

sudo apt-get remove --purge b43-fwcutter
```

3. install bcm43xx firmware:
```

sudo apt-get install bcm43xx-fwcutter
```

you'll be asked if it should automatically fetch the firmware; say yes.

Now reboot and the card should just work.  If for some reason it still doesn't, try running:
```

sudo modprobe bcm43xx
```

and try again.  Please let me know how it goes.

---

### Post by waltcoleman on 2008-06-20
Thank you.  I tried, but still have the same issue.  Unless I manually go in and disable/re-enable the driver, it doesn't work.

---

### Post by pytheas22 on 2008-06-20
Strange.  So you did all of that stuff in my last post, and the wireless still works fine, but only after the uncheck/recheck action?

The only other place where I can think to look to figure out what's going on is to reboot, do the uncheck/recheck, and then immediately run the command "dmesg"  This will dump information to you about what's going on behind the scenes--kernel modules being loaded or loaded or network interfaces being brought up and down, for instance.  If you could run dmesg and post the output here, maybe it will tell us what the uncheck/check action is actually doing that's causing the card to work.

---

### Post by waltcoleman on 2008-06-20
Correct, I followed all the steps from your previous post.  Here is the output from dmesg:

[   19.700316] system 00:02: iomem range 0xfed1c000-0xfed1ffff could not be reserved
[   19.700319] system 00:02: iomem range 0xfed20000-0xfed3ffff could not be reserved
[   19.700322] system 00:02: iomem range 0xfed40000-0xfed44fff could not be reserved
[   19.700325] system 00:02: iomem range 0xfed45000-0xfed8ffff could not be reserved
[   19.700333] system 00:04: iomem range 0xfed00000-0xfed003ff could not be reserved
[   19.700341] system 00:06: ioport range 0x380-0x383 has been reserved
[   19.700344] system 00:06: ioport range 0x680-0x69f has been reserved
[   19.700346] system 00:06: ioport range 0x800-0x80f has been reserved
[   19.700349] system 00:06: ioport range 0x1000-0x107f has been reserved
[   19.700352] system 00:06: ioport range 0x1180-0x11bf has been reserved
[   19.700355] system 00:06: ioport range 0x1640-0x164f has been reserved
[   19.700361] system 00:07: ioport range 0x6a0-0x6af has been reserved
[   19.700364] system 00:07: ioport range 0x6b0-0x6ff has been reserved
[   19.730851] PCI: Bridge: 0000:00:1c.0
[   19.730855]   IO window: 2000-2fff
[   19.730863]   MEM window: d6000000-d7ffffff
[   19.730868]   PREFETCH window: d2000000-d3ffffff
[   19.730874] PCI: Bridge: 0000:00:1c.1
[   19.730877]   IO window: 3000-3fff
[   19.730883]   MEM window: d4000000-d5ffffff
[   19.730888]   PREFETCH window: d0000000-d1ffffff
[   19.730895] PCI: Bridge: 0000:00:1e.0
[   19.730898]   IO window: 4000-4fff
[   19.730904]   MEM window: d8000000-d80fffff
[   19.730908]   PREFETCH window: disabled.
[   19.730944] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 16
[   19.730952] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   19.730977] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 17
[   19.730983] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   19.730994] PCI: Enabling device 0000:00:1e.0 (0004 -> 0007)
[   19.731001] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   19.731014] NET: Registered protocol family 2
[   19.777316] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   19.777554] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   19.778298] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   19.778675] TCP: Hash tables configured (established 131072 bind 65536)
[   19.778678] TCP reno registered
[   19.789410] checking if image is initramfs... it is
[   20.486664] Freeing initrd memory: 7320k freed
[   20.486840] Simple Boot Flag at 0x35 set to 0x1
[   20.487591] audit: initializing netlink socket (disabled)
[   20.487604] audit(1213974865.469:1): initialized
[   20.487809] highmem bounce pool size: 64 pages
[   20.489936] VFS: Disk quotas dquot_6.5.1
[   20.490018] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   20.490161] io scheduler noop registered
[   20.490164] io scheduler anticipatory registered
[   20.490166] io scheduler deadline registered
[   20.490178] io scheduler cfq registered (default)
[   20.490190] Boot video device is 0000:00:02.0
[   20.490293] PCI: Firmware left 0000:05:08.0 e100 interrupts enabled, disabling
[   20.490411] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   20.490470] assign_interrupt_mode Found MSI capability
[   20.490521] Allocate Port Service[0000:00:1c.0:pcie00]
[   20.490562] Allocate Port Service[0000:00:1c.0:pcie02]
[   20.490668] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   20.490726] assign_interrupt_mode Found MSI capability
[   20.490773] Allocate Port Service[0000:00:1c.1:pcie00]
[   20.490811] Allocate Port Service[0000:00:1c.1:pcie02]
[   20.491103] isapnp: Scanning for PnP cards...
[   20.845804] isapnp: No Plug & Play device found
[   20.875633] Real Time Clock Driver v1.12ac
[   20.875875] hpet_resources: 0xfed00000 is busy
[   20.875906] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   20.877236] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   20.877311] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   20.877418] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   20.894025] serio: i8042 KBD port at 0x60,0x64 irq 1
[   20.894031] serio: i8042 AUX port at 0x60,0x64 irq 12
[   20.904216] mice: PS/2 mouse device common for all mice
[   20.904347] EISA: Probing bus 0 at eisa.0
[   20.904354] Cannot allocate resource for EISA slot 1
[   20.904357] Cannot allocate resource for EISA slot 2
[   20.904359] Cannot allocate resource for EISA slot 3
[   20.904362] Cannot allocate resource for EISA slot 4
[   20.904381] EISA: Detected 0 cards.
[   20.904384] cpuidle: using governor ladder
[   20.904386] cpuidle: using governor menu
[   20.904479] NET: Registered protocol family 1
[   20.904509] Using IPI No-Shortcut mode
[   20.904540] registered taskstats version 1
[   20.904659]   Magic number: 12:261:235
[   20.904686]   hash matches device ttyv5
[   20.904769] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   20.904772] EDD information not available.
[   20.904960] Freeing unused kernel memory: 368k freed
[   20.925647] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   22.143653] fuse init (API version 7.9)
[   22.170039] ACPI: SSDT 3F67C189, 0238 (r1 HP     30BB         3000 INTL 20050624)
[   22.170264] ACPI: SSDT 3F67BC42, 04C2 (r1 HP     30BB         3001 INTL 20050624)
[   22.172527] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   22.172532] ACPI: Processor [CPU0] (supports 8 throttling states)
[   22.172789] ACPI: SSDT 3F67C3C1, 00C8 (r1 HP     30BB         3000 INTL 20050624)
[   22.172996] ACPI: SSDT 3F67C104, 0085 (r1 HP     30BB         3000 INTL 20050624)
[   22.173962] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[   22.173968] ACPI: Processor [CPU1] (supports 8 throttling states)
[   22.177662] ACPI: Thermal Zone [THR1] (34 C)
[   22.596839] usbcore: registered new interface driver usbfs
[   22.596866] usbcore: registered new interface driver hub
[   22.602778] usbcore: registered new device driver usb
[   22.604052] USB Universal Host Controller Interface driver v3.0
[   22.604108] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 18
[   22.604119] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   22.604124] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   22.604370] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   22.604406] uhci_hcd 0000:00:1d.0: irq 18, io base 0x00001820
[   22.604557] usb usb1: configuration #1 chosen from 1 choice
[   22.604583] hub 1-0:1.0: USB hub found
[   22.604589] hub 1-0:1.0: 2 ports detected
[   22.708039] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[   22.708052] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   22.708057] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   22.708081] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   22.708115] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001840
[   22.708231] usb usb2: configuration #1 chosen from 1 choice
[   22.708254] hub 2-0:1.0: USB hub found
[   22.708260] hub 2-0:1.0: 2 ports detected
[   22.721037] SCSI subsystem initialized
[   22.723817] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k4-NAPI
[   22.723821] e100: Copyright(c) 1999-2006 Intel Corporation
[   22.732799] libata version 3.00 loaded.
[   22.812027] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 20
[   22.812041] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   22.812046] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   22.812070] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   22.812104] uhci_hcd 0000:00:1d.2: irq 20, io base 0x00001860
[   22.812229] usb usb3: configuration #1 chosen from 1 choice
[   22.812254] hub 3-0:1.0: USB hub found
[   22.812259] hub 3-0:1.0: 2 ports detected
[   22.916013] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 17
[   22.916027] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   22.916032] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   22.916056] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   22.916089] uhci_hcd 0000:00:1d.3: irq 17, io base 0x00001880
[   22.916215] usb usb4: configuration #1 chosen from 1 choice
[   22.916239] hub 4-0:1.0: USB hub found
[   22.916245] hub 4-0:1.0: 2 ports detected
[   23.020166] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 18
[   23.020186] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   23.020190] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   23.020221] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   23.024135] ehci_hcd 0000:00:1d.7: debug port 1
[   23.024143] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   23.024151] ehci_hcd 0000:00:1d.7: irq 18, io mem 0xd8444000
[   23.039949] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   23.040100] usb usb5: configuration #1 chosen from 1 choice
[   23.040126] hub 5-0:1.0: USB hub found
[   23.040133] hub 5-0:1.0: 8 ports detected
[   23.144045] ACPI: PCI Interrupt 0000:05:05.0[A] -> GSI 16 (level, low) -> IRQ 17
[   23.144055] PCI: Setting latency timer of device 0000:05:05.0 to 64
[   23.196781] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[d8001000-d80017ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[   23.200864] ahci 0000:00:1f.2: version 3.0
[   23.200904] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
[   23.200959] ahci 0000:00:1f.2: nr_ports (4) and implemented port map (0x5) don't match, using nr_ports
[   23.200962] ahci 0000:00:1f.2: forcing PORTS_IMPL to 0xf
[   23.201042] ACPI: PCI Interrupt 0000:05:08.0[A] -> GSI 20 (level, low) -> IRQ 21
[   23.201105] PCI: Setting latency timer of device 0000:05:08.0 to 64
[   23.229789] e100: eth0: e100_probe: addr 0xd8000000, irq 21, MAC addr 00:1b:24:21:ed:63
[   23.503875] usb 5-4: new high speed USB device using ehci_hcd and address 2
[   23.515858] Clocksource tsc unstable (delta = -770504602 ns)
[   23.538246] Time: hpet clocksource has been installed.
[   23.645164] usb 5-4: configuration #1 chosen from 1 choice
[   23.861533] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 1.5 Gbps 0xf impl SATA mode
[   23.861539] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part 
[   23.861545] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   23.861857] scsi0 : ahci
[   23.862151] scsi1 : ahci
[   23.862332] scsi2 : ahci
[   23.862514] scsi3 : ahci
[   23.862604] ata1: SATA max UDMA/133 abar m1024@0xd8444400 port 0xd8444500 irq 221
[   23.862608] ata2: SATA max UDMA/133 abar m1024@0xd8444400 port 0xd8444580 irq 221
[   23.862612] ata3: SATA max UDMA/133 abar m1024@0xd8444400 port 0xd8444600 irq 221
[   23.862616] ata4: SATA max UDMA/133 abar m1024@0xd8444400 port 0xd8444680 irq 221
[   23.903083] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00241b005dba1200]
[   23.928703] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   23.929289] ata1.00: ATA-7: TOSHIBA MK6034GSX, AH101H, max UDMA/100
[   23.929292] ata1.00: 117231408 sectors, multi 16: LBA48 
[   23.929971] ata1.00: configured for UDMA/100
[   23.942046] ata2: SATA link down (SStatus 0 SControl 0)
[   23.953986] ata3: SATA link down (SStatus 0 SControl 300)
[   23.965114] ata4: SATA link down (SStatus 0 SControl 0)
[   23.965307] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK6034GS AH10 PQ: 0 ANSI: 5
[   23.965688] ata_piix 0000:00:1f.1: version 2.12
[   23.965709] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 20
[   23.965746] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   23.965842] scsi4 : ata_piix
[   23.966012] scsi5 : ata_piix
[   23.966507] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[   23.966511] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[   23.975182] Driver 'sd' needs updating - please use bus_type methods
[   23.976849] sd 0:0:0:0: [sda] 117231408 512-byte hardware sectors (60022 MB)
[   23.976889] sd 0:0:0:0: [sda] Write Protect is off
[   23.976893] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   23.976959] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   23.977057] sd 0:0:0:0: [sda] 117231408 512-byte hardware sectors (60022 MB)
[   23.977091] sd 0:0:0:0: [sda] Write Protect is off
[   23.977094] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   23.977158] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   23.977162]  sda: sda1 sda2
[   24.040145] sd 0:0:0:0: [sda] Attached SCSI disk
[   24.044875] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   24.280215] ata5.00: ATAPI: Optiarc DVD RW AD-7530A, EH31, max MWDMA2
[   24.453047] ata5.00: configured for MWDMA2
[   24.453141] ata6: port disabled. ignoring.
[   24.454562] scsi 4:0:0:0: CD-ROM            Optiarc  DVD RW AD-7530A  EH31 PQ: 0 ANSI: 5
[   24.454658] scsi 4:0:0:0: Attached scsi generic sg1 type 5
[   24.491519] Driver 'sr' needs updating - please use bus_type methods
[   24.503625] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   24.503630] Uniform CD-ROM driver Revision: 3.20
[   24.503687] sr 4:0:0:0: Attached scsi CD-ROM sr0
[   24.585637] loop: module loaded
[   24.622977] kjournald starting.  Commit interval 5 seconds
[   24.623006] EXT3-fs: mounted filesystem with ordered data mode.
[   35.631159] iTCO_vendor_support: vendor-support=0
[   35.659152] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   35.659265] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[   35.659307] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   35.725147] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   35.765172] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   35.803393] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   35.842745] Linux agpgart interface v0.102
[   35.890525] agpgart: Detected an Intel 945GM Chipset.
[   35.891105] agpgart: Detected 7932K stolen memory.
[   35.908553] agpgart: AGP aperture is 256M @ 0xc0000000
[   35.957702] intel_rng: FWH not detected
[   36.002815] input: Power Button (FF) as /devices/virtual/input/input3
[   36.054554] ACPI: Power Button (FF) [PWRF]
[   36.054622] input: Power Button (CM) as /devices/virtual/input/input4
[   36.118563] ACPI: Power Button (CM) [PWRB]
[   36.118635] input: Sleep Button (CM) as /devices/virtual/input/input5
[   36.158546] ACPI: Sleep Button (CM) [SLPB]
[   36.158618] input: Lid Switch as /devices/virtual/input/input6
[   36.178824] ACPI: Lid Switch [LID]
[   36.239238] ACPI: Battery Slot [BAT0] (battery present)
[   36.239344] ACPI: WMI-Acer: Mapper loaded
[   36.241910] ACPI: AC Adapter [ACAD] (on-line)
[   36.617952] ricoh-mmc: Ricoh MMC Controller disabling driver
[   36.617957] ricoh-mmc: Copyright(c) Philip Langdale
[   36.618008] ricoh-mmc: Ricoh MMC controller found at 0000:05:05.2 [1180:0843] (rev 1)
[   36.618022] ricoh-mmc: Controller is now disabled.
[   36.670536] sdhci: Secure Digital Host Controller Interface driver
[   36.670540] sdhci: Copyright(c) Pierre Ossman
[   36.670588] sdhci: SDHCI controller found at 0000:05:05.1 [1180:0822] (rev 19)
[   36.670607] PCI: Enabling device 0000:05:05.1 (0000 -> 0002)
[   36.670614] ACPI: PCI Interrupt 0000:05:05.1[B] -> GSI 17 (level, low) -> IRQ 16
[   36.670636] sdhci:slot0: Will use DMA mode even though HW doesn't fully claim to support it.
[   36.670644] PCI: Setting latency timer of device 0000:05:05.1 to 64
[   36.670693] mmc0: SDHCI at 0xd8001800 irq 16 DMA
[   36.844831] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/LNXVIDEO:00/input/input7
[   36.898450] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   36.900082] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input8
[   36.955880] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   36.962413] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   37.363715] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterInterruptEx'
[   37.363728] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[   37.363737] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[   37.363746] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[   37.363755] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[   37.363778] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterScatterGatherDma'
[   37.363791] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterInterruptEx'
[   37.363805] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSynchronizeWithInterruptEx'
[   37.363814] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[   37.363823] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[   37.363835] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[   37.363844] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterScatterGatherDma'
[   37.363857] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[   37.363871] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[   37.363880] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[   37.363888] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetBusData'
[   37.363897] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[   37.363916] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[   37.363931] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[   37.363942] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[   37.363951] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[   37.363960] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[   37.363969] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[   37.363983] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[   37.363995] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[   37.364000] ndiswrapper (load_sys_files:210): couldn't prepare driver 'bcmwl6'
[   37.365026] ndiswrapper (load_wrap_driver:112): couldn't load driver bcmwl6; check system log for messages from 'loadndisdriver'
[   37.443212] Linux video capture interface: v2.00
[   37.451725] usbcore: registered new interface driver ndiswrapper
[   37.476650] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04713/0x200000
[   37.501928] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (0c45:62c0)
[   37.504298] usbcore: registered new interface driver uvcvideo
[   37.504304] USB Video Class driver (v0.1.0)
[   37.542818] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
[   37.594470] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
[   37.594501] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   38.722271] lp: driver loaded but no devices found
[   39.436118] EXT3 FS on loop0, internal journal
[   56.506608] Adding 976552k swap on /host/ubuntu/disks/swap.disk.  Priority:-1 extents:1 across:976552k
[   57.294517] ip_tables: (C) 2000-2006 Netfilter Core Team
[   57.670474] No dock devices found.
[   58.834993] apm: BIOS not found.
[   59.548443] ppdev: user-space parallel port driver
[   59.671176] audit(1214000108.091:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5275 profile="/usr/sbin/cupsd" namespace="default"
[   61.061200] Bluetooth: Core ver 2.11
[   61.063834] NET: Registered protocol family 31
[   61.063844] Bluetooth: HCI device and connection manager initialized
[   61.063852] Bluetooth: HCI socket layer initialized
[   61.092111] Bluetooth: L2CAP ver 2.9
[   61.092119] Bluetooth: L2CAP socket layer initialized
[   61.149334] Bluetooth: RFCOMM socket layer initialized
[   61.149357] Bluetooth: RFCOMM TTY layer initialized
[   61.149361] Bluetooth: RFCOMM ver 1.8
[   62.751456] usbcore: deregistering interface driver ndiswrapper
[   62.751810] ndiswrapper (ntoskernel_exit:2708): object f7fff020(2) was not freed, freeing it now
[   62.764248] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   62.779309] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterInterruptEx'
[   62.779329] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[   62.779338] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[   62.779347] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[   62.779355] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[   62.779379] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterScatterGatherDma'
[   62.779391] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterInterruptEx'
[   62.779405] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSynchronizeWithInterruptEx'
[   62.779414] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[   62.779423] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[   62.779435] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[   62.779444] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterScatterGatherDma'
[   62.779457] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[   62.779471] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[   62.779480] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[   62.779489] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetBusData'
[   62.779497] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[   62.779516] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[   62.779531] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[   62.779542] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[   62.779551] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[   62.779560] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[   62.779569] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[   62.779582] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[   62.779595] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[   62.779599] ndiswrapper (load_sys_files:210): couldn't prepare driver 'bcmwl6'
[   62.784198] ndiswrapper (load_wrap_driver:112): couldn't load driver bcmwl6; check system log for messages from 'loadndisdriver'
[   62.786897] usbcore: registered new interface driver ndiswrapper
[   62.813013] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 17
[   62.813030] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   62.832766] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x11, vendor 0x4243)
[   62.832781] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0A, vendor 0x4243)
[   62.832792] ssb: Core 2 found: USB 1.1 Host (cc 0x817, rev 0x03, vendor 0x4243)
[   62.832804] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x01, vendor 0x4243)
[   62.872793] ssb: Sonics Silicon Backplane found on PCI device 0000:02:00.0
[   62.958716] ACPI: PCI interrupt for device 0000:02:00.0 disabled
[   62.960444] usbcore: deregistering interface driver ndiswrapper
[   62.960741] ndiswrapper (ntoskernel_exit:2708): object e007b820(2) was not freed, freeing it now
[   62.972497] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   62.985734] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterInterruptEx'
[   62.985752] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[   62.985761] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[   62.985770] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[   62.985779] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[   62.985802] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterScatterGatherDma'
[   62.985814] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterInterruptEx'
[   62.985828] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSynchronizeWithInterruptEx'
[   62.985837] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[   62.985846] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[   62.985859] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[   62.985868] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterScatterGatherDma'
[   62.985880] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[   62.985894] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[   62.985903] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[   62.985912] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetBusData'
[   62.985921] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[   62.985939] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[   62.985954] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[   62.985966] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[   62.985974] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[   62.985983] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[   62.985992] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[   62.986006] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[   62.986018] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[   62.986022] ndiswrapper (load_sys_files:210): couldn't prepare driver 'bcmwl6'
[   63.000939] ndiswrapper (load_wrap_driver:112): couldn't load driver bcmwl6; check system log for messages from 'loadndisdriver'
[   63.003561] usbcore: registered new interface driver ndiswrapper
[   63.016570] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 17
[   63.016591] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   63.032753] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x11, vendor 0x4243)
[   63.032773] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0A, vendor 0x4243)
[   63.032790] ssb: Core 2 found: USB 1.1 Host (cc 0x817, rev 0x03, vendor 0x4243)
[   63.032807] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x01, vendor 0x4243)
[   63.072769] ssb: Sonics Silicon Backplane found on PCI device 0000:02:00.0
[   63.130024] ACPI: PCI interrupt for device 0000:02:00.0 disabled
[   63.133830] usbcore: deregistering interface driver ndiswrapper
[   63.134078] ndiswrapper (ntoskernel_exit:2708): object e007b720(2) was not freed, freeing it now
[   63.156258] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   63.168406] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterInterruptEx'
[   63.168426] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[   63.168435] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[   63.168444] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[   63.168453] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[   63.168477] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterScatterGatherDma'
[   63.168490] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterInterruptEx'
[   63.168505] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSynchronizeWithInterruptEx'
[   63.168515] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[   63.168526] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[   63.168539] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[   63.168549] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterScatterGatherDma'
[   63.168563] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[   63.168578] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[   63.168588] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[   63.168598] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetBusData'
[   63.168608] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[   63.168649] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[   63.168666] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[   63.168678] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[   63.168688] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[   63.168698] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[   63.168708] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[   63.168723] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[   63.168736] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[   63.168741] ndiswrapper (load_sys_files:210): couldn't prepare driver 'bcmwl6'
[   63.169603] ndiswrapper (load_wrap_driver:112): couldn't load driver bcmwl6; check system log for messages from 'loadndisdriver'
[   63.171951] usbcore: registered new interface driver ndiswrapper
[   63.186485] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 17
[   63.186507] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   63.204712] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x11, vendor 0x4243)
[   63.204734] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0A, vendor 0x4243)
[   63.204749] ssb: Core 2 found: USB 1.1 Host (cc 0x817, rev 0x03, vendor 0x4243)
[   63.204759] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x01, vendor 0x4243)
[   63.244751] ssb: Sonics Silicon Backplane found on PCI device 0000:02:00.0
[   63.330856] ACPI: PCI interrupt for device 0000:02:00.0 disabled
[   63.334364] usbcore: deregistering interface driver ndiswrapper
[   63.335496] ndiswrapper (ntoskernel_exit:2708): object e007bf20(2) was not freed, freeing it now
[   63.353564] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   63.367517] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterInterruptEx'
[   63.367541] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[   63.367553] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[   63.367566] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[   63.367577] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[   63.367609] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterScatterGatherDma'
[   63.367626] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterInterruptEx'
[   63.367645] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSynchronizeWithInterruptEx'
[   63.367658] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[   63.367671] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[   63.367689] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[   63.367702] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterScatterGatherDma'
[   63.367719] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[   63.367738] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[   63.367751] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[   63.367764] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetBusData'
[   63.367777] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[   63.367802] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[   63.367823] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[   63.367839] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[   63.367852] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[   63.367864] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[   63.367877] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[   63.367896] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[   63.367914] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[   63.367920] ndiswrapper (load_sys_files:210): couldn't prepare driver 'bcmwl6'
[   63.368593] ndiswrapper (load_wrap_driver:112): couldn't load driver bcmwl6; check system log for messages from 'loadndisdriver'
[   63.371543] usbcore: registered new interface driver ndiswrapper
[   63.385793] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 17
[   63.385814] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   63.405672] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x11, vendor 0x4243)
[   63.405695] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0A, vendor 0x4243)
[   63.405709] ssb: Core 2 found: USB 1.1 Host (cc 0x817, rev 0x03, vendor 0x4243)
[   63.405720] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x01, vendor 0x4243)
[   63.444705] ssb: Sonics Silicon Backplane found on PCI device 0000:02:00.0
[   64.299436] [drm] Initialized drm 1.1.0 20060810
[   64.301837] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 17
[   64.301847] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   64.301933] [drm] Initialized i915 1.6.0 20060119 on minor 0
[  127.153528] NET: Registered protocol family 10
[  127.154557] lo: Disabled Privacy Extensions
[  127.155702] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  134.213067] CPU0 attaching NULL sched-domain.
[  134.213075] CPU1 attaching NULL sched-domain.
[  134.235888] CPU0 attaching sched-domain:
[  134.235894]  domain 0: span 03
[  134.235896]   groups: 01 02
[  134.235899] CPU1 attaching sched-domain:
[  134.235901]  domain 0: span 03
[  134.235903]   groups: 02 01
[  339.348334] b43-phy0: Broadcom 4311 WLAN found
[  339.390943] b43-phy0 debug: Found PHY: Analog 4, Type 2, Revision 8
[  339.390973] b43-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2050, Revision 2
[  339.416399] phy0: Selected rate control algorithm 'simple'
[  339.660220] b43-phy1: Broadcom 4311 WLAN found
[  339.702880] b43-phy1 debug: Found PHY: Analog 4, Type 2, Revision 8
[  339.702906] b43-phy1 debug: Found Radio: Manuf 0x17F, Version 0x2050, Revision 2
[  339.729317] phy1: Selected rate control algorithm 'simple'
[  339.827424] input: b43-phy1 as /devices/virtual/input/input10
[  340.023288] b43-phy1 debug: Loading firmware version 351.126 (2006-07-29 05:54:02)
[  341.263174] b43-phy1 debug: Chip initialized
[  341.263504] b43-phy1 debug: 32-bit DMA initialized
[  341.283085] Registered led device: b43-phy1:tx
[  341.283268] Registered led device: b43-phy1:rx
[  341.283427] Registered led device: b43-phy1:radio
[  341.283471] b43-phy1 debug: Wireless interface started
[  341.283865] b43-phy1 debug: Adding Interface type 2
[  341.287951] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  373.284941] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[  373.288986] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  375.848184] NET: Registered protocol family 17
[  391.265555] eth0: no IPv6 routers present
localadmin@localadmin-laptop:~$

---

### Post by Ayuthia on 2008-06-20
Ok.  Sorry for jumping in, but I just wanted to make a few comments.  Looking at your dmesg, it shows that you tried to use a Vista driver with NDISwrapper (bcmwl6).  They are not functioning in NDISwrapper yet.  It works with bcmwl5 drivers.  They are XP drivers and possibly older Windows version.

bcm43xx will work with the 4311 rev 01 card, but not as well as the b43 driver.  You might want to install the b43 driver(sudo apt-get install b43-fwcutter) again.  You will then need to edit the /etc/modprobe.d/blacklist file by:
```
gksu gedit /etc/modprobe.d/blacklist
```You will need to remove the following:
```
blacklist b43
blacklist ssb
blacklist b43 ssb
```
You will need to add (or make sure that it is in the file) the following:
```
blacklist bcm43xx
blacklist ndiswrapper
```You will also need to make sure that the following is not in /etc/modules (gksu gedit /etc/modules):
```
ndiswrapper
bcm43xx
```

The reason why you had to disable and the enable the hardware driver is most likely because you had ndiswrapper installed.

If you do reinstall b43 and want to test and see if it works, you can do the following:
```
sudo modprobe -r b43 b44 ssb bcm43xx wl ndiswrapper
sudo depmod -ae
sudo modprobe b43
```

---

### Post by pytheas22 on 2008-06-20
Thanks for all that information.  It looks like ndiswrapper is trying to control the card, but it keeps on failing for some reason, hence the messages like, "[ 37.364000] ndiswrapper (load_sys_files:210): couldn't prepare driver 'bcmwl6' / [ 37.365026] ndiswrapper (load_wrap_driver:112): couldn't load driver bcmwl6; check system log for messages from 'loadndisdriver'"  Eventually b43, the native Linux driver, seems to take control of the card, as indicated by "b43-phy0: Broadcom 4311 WLAN found."  This must be happening after you do the uncheck/recheck.  So at least we have a clearer idea of what's going on.

Please do this:

in a terminal, type:
```

sudo gedit /etc/modprobe.d/blacklist
```

Search for the strings "b43," "b43legacy" and "ssb."  Delete or comment (if you put a # at the beginning of a line it becomes a comment and the system disregards it) any line that contains these strings.  Then add to the bottom of the file these lines:
```

blacklist ndiswrapper
blacklist bcm43xx
```

if that isn't there already.

Then please save the file and reboot and see if the wireless works without the uncheck/recheck.  If it still doesn't work, please run the command:
```

sudo modprobe b43*
```

and see if it works then.

I'm sorry this isn't all going as smoothly as you probably hoped, but I think we're closer to a solution.

EDIT: Ayuthia beat me to the post, but I think we're both suggesting the same thing, so following either one of our directions should do the trick (Ayuthia's are probably a little clearer and more thorough).

---

### Post by Ayuthia on 2008-06-20
One more comment.  If you need help in figure out what to keep or remove in your /etc/modprobe.d/blacklist or /etc/modules, please let us know which option you want to use (bcm43xx, b43, ndiswrapper) and post the following:
```
cat /etc/modprobe.d/blacklist*|grep -i -e bcm43xx -e b43 -e ssb -e b44 -e ndiswrapper -e wl
cat /etc/modules|grep  -i -e bcm43xx -e b43 -e ssb -e b44 -e ndiswrapper -e wl
```Those two commands will list out any lines in the two files that contain bcm43xx, b43, ssb, b44, or ndiswrapper.

---

### Post by waltcoleman on 2008-06-24
Thanks for the follow up...sorry I've not replied sooner, been out of town for a couple days.  I will try this tonite and hopefully have some results soon.  I will definitely follow up in the forums.  Thank you again for all the help!

---

### Post by waltcoleman on 2008-06-25
Thank you both!  That solved the problem.  I've blacklisted ndiswrapper and bcm43xx and I assume it's picking up and using the b43 driver.  It boots with the blue light and picks up wireless with no problems.  Thanks again to both of you, I really appreciate your help!

---

### Post by pytheas22 on 2008-06-25
No problem; glad it's finally solved.

---

