---
title: "update annoyance....need to modprobe ndiswrapper everytime..."
date: 2007-02-02
forum: Networking &amp; Wireless
---

### Post by aggie333 on 2007-02-02
hi guys,
   i am getting extremely annoyed with the way updates over write ndiswrapper modprobe...i have to manually set it up every time there are updates..c.an some one tell me how this can be avoided...pleeeeeeeeeease help help...my ubuntu experience has been good excepting this one grouse...

---

### Post by codejunkie on 2007-02-02
> **aggie333 said:**
> hi guys,
   i am getting extremely annoyed with the way updates over write ndiswrapper modprobe...i have to manually set it up every time there are updates..c.an some one tell me how this can be avoided...pleeeeeeeeeease help help...my ubuntu experience has been good excepting this one grouse...
if your just wanting it to load a module on startup run
```
sudo gedit /etc/modules
```
and add 
```
ndiswrapper
```to the bottom of the file
save it and reboot and it should automaticly load it on startup.

---

### Post by aggie333 on 2007-02-05
hi, 
the

---

### Post by aggie333 on 2007-02-05
hi, 
   the problem is not that network manager does not start up automatically....it does normally...its just that it fails to do so after an update....i have to loggin and restart after every update to get network manager to start up automatically....this is sorta annoying cause it voids linux's design to never have to reboot to be maintained....thanks in advance...

---

### Post by dmizer on 2007-02-05
you don't have to reboot to restart the network manager.  simply do:
```
sudo /etc/init.d/networking restart
```

how did you install ndiswrapper?

---

### Post by Floppyjoe on 2007-02-06
> **dmizer said:**
> you don't have to reboot to restart the network manager.  simply do:
```
sudo /etc/init.d/networking restart
```


I've actually had trouble issuing this command. Sometimes it causes a crash where everything freezes up. Not sure why this occurs though. Maybe you have some insight? I usually just reboot the computer.

---

### Post by aggie333 on 2007-02-06
hey,
   i installed ndiswrapper from the cd....i think the version number is 1.8...i had previously installed version 1.34 from source but removed for some reason i dont remember now.....well now that uve asked this question  can u tell me why or how that would make a difference....i would like to learn....thanks

---

### Post by dmizer on 2007-02-07
> **Floppyjoe said:**
> I've actually had trouble issuing this command. Sometimes it causes a crash where everything freezes up. Not sure why this occurs though. Maybe you have some insight? I usually just reboot the computer.
i really don't know about this one.  i suggest taking a look at some of the logs in /var/log to see if anything turns up.

> **aggie333 said:**
> hey,
   i installed ndiswrapper from the cd....i think the version number is 1.8...i had previously installed version 1.34 from source but removed for some reason i dont remember now.....well now that uve asked this question  can u tell me why or how that would make a difference....i would like to learn....thanks
well, sometimes software that is installed by a script of some kind like automatix will cause problems.  but you didn't, so that's not your problem.

i really haven't had this problem ... ndiswrapper has worked solidly for me without interruption for months and even through ndiswrapper updates.

did you follow a howto to get your card to work?

next time it happens (before you reboot, and while it's broken), please record the output of:
lsmod
dmesg

and then post them here.  we'll see if we can't get this nailed down for ya.

---

### Post by AAM on 2007-02-07
the commands that you should invoke (don't forget the dead chickens!) with ndiswrapper installation are:

take the dongle OUT....

install the ndiswrapper package
sudo gedit /etc/modules (add **ndiswrapper**)
sudo gedit /etc/iftab (add **wlan0 mac xx: xx: xx: xx: xx apt 1**)
sudo gedit /etc/modprobe.d/blacklist (add 4 lines that blacklist islsm, islsm_pci, islsm_usb and prism2_usb)
cd /folder/WG111 (substitute the directory name here)
sudo ndiswrapper -i netwg111.inf (substitute name if different)
sudo depmod -a
sudo modprobe ndiswrapper
**sudo ndiswrapper -m (*this may be what you are missing*)**

.... insert the dongle
go to System | Administration | Networking
select the wlan0 and edit properties to include your ESSID.

---

### Post by aggie333 on 2007-03-10
hi guys,
   these are the outputs that were asked for....the problem stills persists and is still annoying:-(

**lsmod**
Module                  Size  Used by
nls_utf8                2304  1 
nls_cp437               6016  1 
vfat                   13440  1 
fat                    54556  1 vfat
ipv6                  257632  8 
binfmt_misc            11784  1 
rfcomm                 38936  0 
l2cap                  23300  5 rfcomm
bluetooth              48996  4 rfcomm,l2cap
vmnet                  38444  13 
vmmon                 115948  0 
speedstep_lib           4868  0 
cpufreq_userspace       4372  0 
cpufreq_stats           5892  0 
freq_table              4996  1 cpufreq_stats
cpufreq_powersave       2048  0 
cpufreq_ondemand        6944  0 
cpufreq_conservative     7200  0 
video                  16644  0 
tc1100_wmi              7428  0 
sbs                    15776  0 
sony_acpi               5516  0 
pcc_acpi               13184  0 
i2c_ec                  5376  1 sbs
hotkey                 10660  0 
dev_acpi               11140  0 
button                  7056  0 
battery                10756  0 
container               4736  0 
ac                      5892  0 
asus_acpi              16792  0 
sg                     35356  0 
sd_mod                 21648  1 
lp                     11972  0 
af_packet              21768  2 
snd_ens1371            26272  1 
gameport               15368  1 snd_ens1371
snd_rawmidi            25600  1 snd_ens1371
snd_seq_device          8972  1 snd_rawmidi
snd_ac97_codec         96672  1 snd_ens1371
snd_ac97_bus            2432  1 snd_ac97_codec
snd_pcm_oss            46080  0 
snd_mixer_oss          18560  1 snd_pcm_oss
snd_pcm                80520  3 snd_ens1371,snd_ac97_codec,snd_pcm_oss
snd_timer              23172  1 snd_pcm
nvidia               3931148  8 
usb_storage            73408  1 
scsi_mod              141320  3 sg,sd_mod,usb_storage
snd                    55428  10 snd_ens1371,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9952  1 snd
libusual               15632  1 usb_storage
snd_page_alloc         10504  1 snd_pcm
i2c_core               22288  1 i2c_ec
tsdev                   8256  0 
se401                  19076  0 
compat_ioctl32          1536  1 se401
videodev                9728  1 se401
3c59x                  45736  0 
mii                     6016  1 3c59x
evdev                  10496  1 
psmouse                40072  0 
pcspkr                  3072  0 
serio_raw               7300  0 
parport_pc             36132  1 
parport                37320  2 lp,parport_pc
intel_agp              25116  1 
agpgart                33456  2 nvidia,intel_agp
shpchp                 40856  0 
pci_hotplug            31284  1 shpchp
floppy                 60676  0 
rtc                    12596  0 
ide_floppy             18944  0 
ext3                  138888  1 
jbd                    55700  1 ext3
uhci_hcd               23176  0 
usbcore               130304  5 usb_storage,libusual,se401,uhci_hcd
ide_generic             1536  0 
ide_cd                 32416  0 
cdrom                  37792  1 ide_cd
ide_disk               17664  3 
piix                   10628  1 
generic                 5252  0 
thermal                14600  0 
processor              26028  1 thermal
fan                     5124  0 
fbcon                  40480  0 
tileblit                2944  1 fbcon
font                    8448  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2432  1 bitblit
vesafb                  8348  0 
capability              5000  0 
commoncap               7808  1 capability





**dmesg**
[17179569.184000] Linux version 2.6.17-11-386 (root@terranova) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 Thu Feb 1 19:50:13 UTC 2007 (Ubuntu 2.6.17-11.35-386)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 0000000017fc0000 (usable)
[17179569.184000]  BIOS-e820: 0000000017fc0000 - 0000000017ff8000 (ACPI data)
[17179569.184000]  BIOS-e820: 0000000017ff8000 - 0000000018000000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 00000000ffb80000 - 00000000ffc00000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 383MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 98240
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 94144 pages, LIFO batch:31
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 AMI                                   ) @ 0x000ff980
[17179569.184000] ACPI: RSDT (v001 DELL   ZUUL     0x20020611 MSFT 0x00001011) @ 0x17ff0000
[17179569.184000] ACPI: FADT (v001 DELL   ZUUL     0x20020611 MSFT 0x00001011) @ 0x17ff1000
[17179569.184000] ACPI: BOOT (v001 DELL   ZUUL     0x20020611 MSFT 0x00001011) @ 0x17ff4000
[17179569.184000] ACPI: DSDT (v001 D815EA EA81510A 0x00000013 MSFT 0x0100000b) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x408
[17179569.184000] Allocating PCI resources starting at 20000000 (gap: 18000000:e7b80000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash
[17179569.184000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[17179569.184000] mapped APIC to ffffd000 (01302000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[17179569.184000] Detected 930.434 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179569.296000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179569.296000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179569.328000] Memory: 380052k/392960k available (1829k kernel code, 12300k reserved, 1041k data, 288k init, 0k highmem)
[17179569.328000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179569.408000] Calibrating delay using timer specific routine.. 1862.34 BogoMIPS (lpj=3724680)
[17179569.408000] Security Framework v1.0.0 initialized
[17179569.408000] SELinux:  Disabled at boot.
[17179569.408000] Mount-cache hash table entries: 512
[17179569.408000] CPU: After generic identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[17179569.408000] CPU: After vendor identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[17179569.408000] CPU: L1 I cache: 16K, L1 D cache: 16K
[17179569.408000] CPU: L2 cache: 256K
[17179569.408000] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[17179569.408000] CPU: Intel Pentium III (Coppermine) stepping 06
[17179569.408000] Checking 'hlt' instruction... OK.
[17179569.424000] SMP alternatives: switching to UP code
[17179569.424000] Freeing SMP alternatives: 0k freed
[17179569.424000] checking if image is initramfs... it is
[17179570.428000] Freeing initrd memory: 5251k freed
[17179570.428000] ACPI: Core revision 20060707
[17179570.428000] ACPI: Looking for DSDT ... not found!
[17179570.432000] ACPI: setting ELCR to 0200 (from 0e08)
[17179570.436000] NET: Registered protocol family 16
[17179570.436000] EISA bus registered
[17179570.436000] ACPI: bus type pci registered
[17179570.436000] PCI: PCI BIOS revision 2.10 entry at 0xfda95, last bus=2
[17179570.436000] PCI: Using configuration type 1
[17179570.436000] Setting up standard PCI resources
[17179570.444000] ACPI: Interpreter enabled
[17179570.444000] ACPI: Using PIC for interrupt routing
[17179570.444000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179570.444000] PCI: Probing PCI hardware (bus 00)
[17179570.448000] PCI quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
[17179570.448000] PCI quirk: region 0500-053f claimed by ICH4 GPIO
[17179570.448000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[17179570.448000] Boot video device is 0000:01:00.0
[17179570.448000] PCI: Transparent bridge - 0000:00:1e.0
[17179570.448000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179570.452000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[17179570.456000] ACPI: Power Resource [URP1] (off)
[17179570.456000] ACPI: Power Resource [URP2] (off)
[17179570.456000] ACPI: Power Resource [FDDP] (off)
[17179570.456000] ACPI: Power Resource [LPTP] (off)
[17179570.456000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12)
[17179570.460000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *9 10 11 12)
[17179570.460000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 11 12) *0, disabled.
[17179570.460000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 *10 11 12)
[17179570.460000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12) *0, disabled.
[17179570.460000] ACPI: PCI Interrupt Link [LNKF] (IRQs *3 4 5 6 7 9 10 11 12)
[17179570.460000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 *11 12)
[17179570.460000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12) *0, disabled.
[17179570.460000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179570.460000] pnp: PnP ACPI init
[17179570.468000] pnp: PnP ACPI: found 12 devices
[17179570.468000] PnPBIOS: Disabled by ACPI PNP
[17179570.468000] PCI: Using ACPI for IRQ routing
[17179570.468000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179570.472000] PCI: Bridge: 0000:00:01.0
[17179570.472000]   IO window: disabled.
[17179570.472000]   MEM window: fc900000-fe9fffff
[17179570.472000]   PREFETCH window: f0600000-f46fffff
[17179570.472000] PCI: Bridge: 0000:00:1e.0
[17179570.472000]   IO window: d000-dfff
[17179570.472000]   MEM window: fea00000-feafffff
[17179570.472000]   PREFETCH window: f4700000-f47fffff
[17179570.472000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179570.472000] NET: Registered protocol family 2
[17179570.512000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[17179570.512000] TCP established hash table entries: 16384 (order: 4, 65536 bytes)
[17179570.512000] TCP bind hash table entries: 8192 (order: 3, 32768 bytes)
[17179570.512000] TCP: Hash tables configured (established 16384 bind 8192)
[17179570.512000] TCP reno registered
[17179570.512000] Simple Boot Flag at 0x7a set to 0x1
[17179570.512000] audit: initializing netlink socket (disabled)
[17179570.512000] audit(1173581835.512:1): initialized
[17179570.512000] VFS: Disk quotas dquot_6.5.1
[17179570.512000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179570.512000] Initializing Cryptographic API
[17179570.512000] io scheduler noop registered
[17179570.512000] io scheduler anticipatory registered
[17179570.512000] io scheduler deadline registered
[17179570.512000] io scheduler cfq registered (default)
[17179570.512000] isapnp: Scanning for PnP cards...
[17179570.868000] isapnp: No Plug & Play device found
[17179570.912000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179570.912000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179570.916000] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179570.916000] mice: PS/2 mouse device common for all mice
[17179570.916000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179570.916000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179570.916000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179570.916000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[17179570.920000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179570.920000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179570.920000] EISA: Probing bus 0 at eisa.0
[17179570.920000] EISA: Detected 0 cards.
[17179570.920000] TCP bic registered
[17179570.920000] NET: Registered protocol family 1
[17179570.920000] NET: Registered protocol family 8
[17179570.920000] NET: Registered protocol family 20
[17179570.920000] Using IPI Shortcut mode
[17179570.920000] ACPI: (supports S0 S1 S4 S5)
[17179570.924000] Freeing unused kernel memory: 288k freed
[17179570.956000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179572.088000] Capability LSM initialized
[17179573.016000] ICH2: IDE controller at PCI slot 0000:00:1f.1
[17179573.016000] ICH2: chipset revision 2
[17179573.016000] ICH2: not 100% native mode: will probe irqs later
[17179573.016000]     ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:pio
[17179573.016000]     ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:DMA, hdd:pio
[17179573.016000] Probing IDE interface ide0...
[17179573.304000] hda: IC35L020AVER07-0, ATA DISK drive
[17179573.976000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179573.996000] Probing IDE interface ide1...
[17179574.736000] hdc: Lite-On LTN486 48x Max, ATAPI CD/DVD-ROM drive
[17179575.520000] hdd: IOMEGA ZIP 250 ATAPI, ATAPI FLOPPY drive
[17179575.576000] ide1 at 0x170-0x177,0x376 on irq 15
[17179575.596000] hda: max request size: 128KiB
[17179575.620000] hda: 39102336 sectors (20020 MB) w/1916KiB Cache, CHS=38792/16/63, UDMA(100)
[17179575.620000] hda: cache flushes not supported
[17179575.620000]  hda: hda1 hda2 < hda5 >
[17179575.704000] hdc: ATAPI 48X CD-ROM drive, 120kB Cache, UDMA(33)
[17179575.704000] Uniform CD-ROM driver Revision: 3.20
[17179575.996000] usbcore: registered new driver usbfs
[17179576.000000] usbcore: registered new driver hub
[17179576.004000] USB Universal Host Controller Interface driver v3.0
[17179576.004000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 10
[17179576.004000] PCI: setting IRQ 10 as level-triggered
[17179576.004000] ACPI: PCI Interrupt 0000:00:1f.2[D] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
[17179576.004000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[17179576.004000] uhci_hcd 0000:00:1f.2: UHCI Host Controller
[17179576.004000] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
[17179576.004000] uhci_hcd 0000:00:1f.2: irq 10, io base 0x0000ef80
[17179576.008000] usb usb1: configuration #1 chosen from 1 choice
[17179576.008000] hub 1-0:1.0: USB hub found
[17179576.008000] hub 1-0:1.0: 2 ports detected
[17179576.192000] Attempting manual resume
[17179576.252000] kjournald starting.  Commit interval 5 seconds
[17179576.252000] EXT3-fs: mounted filesystem with ordered data mode.
[17179576.352000] usb 1-1: new full speed USB device using uhci_hcd and address 2
[17179576.524000] usb 1-1: config 1 interface 0 has no altsetting 1
[17179576.564000] usb 1-1: configuration #1 chosen from 1 choice
[17179576.804000] usb 1-2: new full speed USB device using uhci_hcd and address 3
[17179576.976000] usb 1-2: configuration #1 chosen from 1 choice
[17179590.392000] ide-floppy driver 0.99.newide
[17179590.396000] hdd: No disk in drive
[17179590.396000] hdd: 0kB, 0/64/32 CHS, 4096 kBps, 512 sector size, 2941 rpm
[17179590.424000] Real Time Clock Driver v1.12ac
[17179590.584000] Floppy drive(s): fd0 is 1.44M
[17179590.600000] FDC 0 is a post-1991 82077
[17179590.608000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179590.616000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179590.664000] Linux agpgart interface v0.101 (c) Dave Jones
[17179590.668000] agpgart: Detected an Intel i815 Chipset.
[17179590.672000] agpgart: AGP aperture is 64M @ 0xf8000000
[17179590.692000] parport: PnPBIOS parport detected.
[17179590.692000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[17179590.812000] input: PC Speaker as /class/input/input1
[17179590.856000] hw_random: RNG not detected
[17179591.580000] input: PS/2 Generic Mouse as /class/input/input2
[17179592.652000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 9
[17179592.652000] PCI: setting IRQ 9 as level-triggered
[17179592.652000] ACPI: PCI Interrupt 0000:02:0c.0[A] -> Link [LNKB] -> GSI 9 (level, low) -> IRQ 9
[17179592.652000] 3c59x: Donald Becker and others. [www.scyld.com/network/vortex.html](www.scyld.com/network/vortex.html)
[17179592.652000] 0000:02:0c.0: 3Com PCI 3c905C Tornado at d88a0c00.
[17179592.792000] Linux video capture interface: v1.00
[17179592.808000] drivers/media/video/se401.c: SE401 usb camera driver version 0.24 registering
[17179592.808000] drivers/media/video/se401.c: SE401 camera found: Kensington VideoCAM 6701(5/7)
[17179592.808000] drivers/media/video/se401.c: firmware version: 30
[17179592.812000] drivers/media/video/se401.c: ExtraFeatures: 0 Sizes: 160x120 176x144 320x240 352x288 400x300 640x480
[17179592.816000] hdd: No disk in drive
[17179592.824000] videodev: "Kensington VideoCAM 6701(5/7)" has no release callback. Please fix your driver for proper sysfs support, see [http://lwn.net/Articles/36850/](http://lwn.net/Articles/36850/)
[17179592.824000] drivers/media/video/se401.c: registered new video device: video0
[17179592.824000] usbcore: registered new driver se401
[17179592.848000] ts: Compaq touchscreen protocol output
[17179592.848000] hdd: No disk in drive
[17179592.920000] ACPI: PCI Interrupt 0000:02:0c.0[A] -> Link [LNKB] -> GSI 9 (level, low) -> IRQ 9
[17179592.920000] eth0:  setting half-duplex.
[17179592.980000] usbcore: registered new driver libusual
[17179593.232000] SCSI subsystem initialized
[17179593.244000] Initializing USB Mass Storage driver...
[17179593.244000] scsi0 : SCSI emulation for USB Mass Storage devices
[17179593.244000] usb-storage: device found at 3
[17179593.244000] usb-storage: waiting for device to settle before scanning
[17179593.244000] usbcore: registered new driver usb-storage
[17179593.244000] USB Mass Storage support registered.
[17179593.496000] nvidia: module license 'NVIDIA' taints kernel.
[17179593.620000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[17179593.620000] PCI: setting IRQ 11 as level-triggered
[17179593.620000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17179593.620000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-7184  Tue Aug  1 18:38:58 PDT 2006
[17179593.760000] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 11
[17179593.760000] ACPI: PCI Interrupt 0000:02:0a.0[A] -> Link [LNKG] -> GSI 11 (level, low) -> IRQ 11
[17179593.988000] NET: Registered protocol family 17
[17179594.856000] lp0: using parport0 (interrupt-driven).
[17179594.912000] Adding 835340k swap on /dev/disk/by-uuid/01822671-6597-480c-ae99-d0f061ca2954.  Priority:-1 extents:1 across:835340k
[17179595.008000] EXT3 FS on hda1, internal journal
[17179598.244000] usb-storage: device scan complete
[17179598.248000]   Vendor: Kingston  Model: DataTraveler 2.0  Rev: 1.00
[17179598.248000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[17179598.436000] SCSI device sda: 1952256 512-byte hdwr sectors (1000 MB)
[17179598.440000] sda: Write Protect is off
[17179598.440000] sda: Mode Sense: 03 00 00 00
[17179598.440000] sda: assuming drive cache: write through
[17179598.452000] SCSI device sda: 1952256 512-byte hdwr sectors (1000 MB)
[17179598.456000] sda: Write Protect is off
[17179598.456000] sda: Mode Sense: 03 00 00 00
[17179598.456000] sda: assuming drive cache: write through
[17179598.456000]  sda: unknown partition table
[17179598.476000] sd 0:0:0:0: Attached scsi removable disk sda
[17179598.496000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17179601.292000] ACPI: Power Button (FF) [PWRF]
[17179601.292000] ACPI: Power Button (CM) [PBTN]
[17179601.504000] ibm_acpi: ec object not found
[17179601.556000] pcc_acpi: loading...
[17179602.260000] acpi_cpufreq: Unknown symbol cpu_online_map
[17179605.776000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[17179605.776000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[17179605.776000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[17179606.000000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[17179606.000000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[17179606.000000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[17179607.020000] Dell Dimension 4100 machine detected. Disabling APM.
[17179607.020000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179607.020000] apm: disabled on user request.
[17179614.976000] /dev/vmmon[4049]: Module vmmon: registered with major=10 minor=165
[17179614.976000] /dev/vmmon[4049]: Module vmmon: initialized
[17179615.064000] /dev/vmnet: open called by PID 4071 (vmnet-bridge)
[17179615.064000] /dev/vmnet: hub 0 does not exist, allocating memory.
[17179615.064000] /dev/vmnet: port on hub 0 successfully opened
[17179615.064000] bridge-eth0: enabling the bridge
[17179615.064000] bridge-eth0: up
[17179615.064000] bridge-eth0: already up
[17179615.064000] bridge-eth0: attached
[17179615.120000] /dev/vmnet: open called by PID 4077 (vmnet-netifup)
[17179615.120000] /dev/vmnet: hub 1 does not exist, allocating memory.
[17179615.120000] /dev/vmnet: port on hub 1 successfully opened
[17179615.128000] /dev/vmnet: open called by PID 4087 (vmnet-netifup)
[17179615.128000] /dev/vmnet: hub 8 does not exist, allocating memory.
[17179615.128000] /dev/vmnet: port on hub 8 successfully opened
[17179615.256000] /dev/vmnet: open called by PID 4086 (vmnet-natd)
[17179615.256000] /dev/vmnet: port on hub 8 successfully opened
[17179615.280000] /dev/vmnet: open called by PID 4113 (vmnet-dhcpd)
[17179615.280000] /dev/vmnet: port on hub 1 successfully opened
[17179615.320000] /dev/vmnet: open called by PID 4112 (vmnet-dhcpd)
[17179615.320000] /dev/vmnet: port on hub 8 successfully opened
[17179615.532000] Bluetooth: Core ver 2.8
[17179615.532000] NET: Registered protocol family 31
[17179615.532000] Bluetooth: HCI device and connection manager initialized
[17179615.532000] Bluetooth: HCI socket layer initialized
[17179615.568000] Bluetooth: L2CAP ver 2.8
[17179615.568000] Bluetooth: L2CAP socket layer initialized
[17179615.596000] Bluetooth: RFCOMM socket layer initialized
[17179615.596000] Bluetooth: RFCOMM TTY layer initialized
[17179615.596000] Bluetooth: RFCOMM ver 1.7
[17179624.308000] NET: Registered protocol family 10
[17179624.308000] lo: Disabled Privacy Extensions
[17179624.308000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17179624.308000] IPv6 over IPv4 tunneling driver
[17179634.336000] vmnet8: no IPv6 routers present
[17179635.152000] vmnet1: no IPv6 routers present
[17179730.484000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[17179730.484000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[17179730.484000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[17179753.144000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[17179753.144000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[17179753.144000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[17179783.544000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[17179783.544000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[17179783.544000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[17179809.972000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!



**output from what i did next**
linmach@linmach:~$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

vmnet1    no wireless extensions.

vmnet8    no wireless extensions.

sit0      no wireless extensions.
linmach@linmach:~$ 
linmach@linmach:~$ sudo depmod -a
Password:
linmach@linmach:~$ sudo modprobe ndiswrapper
linmach@linmach:~$ sudo ndiswrapper -m
modprobe config already contains alias directive

linmach@linmach:~$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

vmnet1    no wireless extensions.

vmnet8    no wireless extensions.

sit0      no wireless extensions.

wlan0     IEEE 802.11FH  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Sensitivity=-200 dBm  
          RTS thr:2346 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

linmach@linmach:~$

---

### Post by gaston9x19 on 2007-11-04
> **AAM said:**
> the commands that you should invoke (don't forget the dead chickens!) with ndiswrapper installation are:

take the dongle OUT....

install the ndiswrapper package
sudo gedit /etc/modules (add **ndiswrapper**)
sudo gedit /etc/iftab (add **wlan0 mac xx: xx: xx: xx: xx apt 1**)
sudo gedit /etc/modprobe.d/blacklist (add 4 lines that blacklist islsm, islsm_pci, islsm_usb and prism2_usb)
cd /folder/WG111 (substitute the directory name here)
sudo ndiswrapper -i netwg111.inf (substitute name if different)
sudo depmod -a
sudo modprobe ndiswrapper
**sudo ndiswrapper -m (*this may be what you are missing*)**

.... insert the dongle
go to System | Administration | Networking
select the wlan0 and edit properties to include your ESSID.



I get a bunch of errors immediately after trying to do the **sudo modprobe ndiswrapper** line. Here's what my terminal console looks like so far:

```
bensauve@ubuntu:~$ sudo -s
root@ubuntu:~# ndiswrapper -l
No drivers installed
root@ubuntu:~# sudo gedit /etc/modprobe.d/blacklist
root@ubuntu:~# sudo gedit /etc/modules/
root@ubuntu:~# sudo gedit /etc/iftab/
root@ubuntu:~# cd /home/bensauve/
root@ubuntu:~# dir
Desktop   net111v2.cat   net111v2.inf   wg111v2.sys
root@ubuntu:~# sudo ndiswrapper -i net111v2.inf
Installing net111v2
root@ubuntu:~# sudo depmod -a
root@ubuntu:~# sudo modprobe ndiswrapper
WARNING: /etc/modprobe.d/blacklist Line 1: ignoring bad line starting with 'blacklist'
WARNING: /etc/modprobe.d/blacklist Line 2: ignoring bad line starting with 'blacklist'
WARNING: /etc/modprobe.d/blacklist Line 3: ignoring bad line starting with 'blacklist'
WARNING: /etc/modprobe.d/blacklist Line 4: ignoring bad line starting with 'blacklist'
root@ubuntu:~# 

```

Here's what I have  when I open up /etc/modprobe.d/blacklist with gedit:

```

blacklist islsm
blacklist islsm_pci
blacklist islsm_usb
blacklist prism2_usb

```

Now I'm brand new to Linux, and I thought maybe you're not supposed to have to include the term 'blacklist' when the file you appear to be opening is also called '.../blacklist'. I tried taking out those terms and just putting in the islsm stuff, and it still gave me the error, just with a different 'starting with....' line.

What do I do to make the netgear wireless dongle work??? This is all so confusing!

---

### Post by djdarrin91 on 2008-01-19
Thanks Codejunkie adding ndiswrapper to modules worked perfect for me!:)

---

### Post by HermanAB on 2008-01-19
Another thought:  If everything is working properly and your machine is safely behind a firewall, why do you do updates?

Most Linux trouble is due to bad updates.  I never do updates, unless there is a damn good reason for it.  Once a year I reinstall all my machines with the latest version.

Cheers,

Herman

---

