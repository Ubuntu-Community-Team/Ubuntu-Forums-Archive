---
title: "Problem while starting Linux"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by bharaths_jois on 2009-01-26
Hi ppl,

  1st I would like to start with "This is my 1st login into Linux".Now, to the problem... I have this problem while booting up into Linux.The splash screen comes up and then loading bar does not move. And no other indication about the boot process. After a good amount of time (about 6-7 minutes), the non-GUI screen comes up showing a few errors. And then I see - 
[initramfs] Type 'help'..... on the same screen.

Its only when i type exit here the drivers and other managers are loaded and the GUI comes up. Could you please help me with this. Please let me know what other inputs are required to help me, like the log...

Best regards,
Bharath

---

### Post by drs305 on 2009-01-26
Please post the results of the following:
```

sudo blkid && cat /etc/initramfs-tools/conf.d/resume && cat /etc/fstab && cat /boot/grub/menu.lst

```

When you respond, please put the results in a code box by selecting the # symbol.

---

### Post by bharaths_jois on 2009-01-26
Below is the result of the command:

```
/dev/sda1: LABEL="WINXP" UUID="A890-3AE6" TYPE="vfat" 
/dev/sda5: LABEL="MISC" UUID="497B-CB87" TYPE="vfat" 
/dev/sda6: LABEL="SOFTWARES" UUID="DC73-4F51" TYPE="vfat" 
/dev/sdb2: UUID="a2bd95c1-57f2-4d57-843b-be6b9d7515a3" TYPE="ext2" 
/dev/sdb5: TYPE="swap" UUID="47d9a309-0d7c-49ac-bb34-e5c5c0c9a3bc" 
/dev/sdb6: UUID="92F7-9A2E" TYPE="vfat" LABEL="PICS N SW" 
/dev/sdb7: LABEL="SONGS" UUID="901F-27D2" TYPE="vfat" 
/dev/sdb8: LABEL="TECHSTUPH" UUID="D82E-BBC7" TYPE="vfat" 
/dev/sdb9: UUID="25EF-147C" TYPE="vfat" LABEL="MOVIES" 
/dev/sdb10: UUID="92F7-894E" TYPE="vfat" LABEL="MOVIES" 
/dev/sdb11: LABEL="SETUP_FILES" UUID="9027-12F2" TYPE="vfat" 
/dev/sdb12: LABEL="HIGHERSTUD" UUID="F86D-0BF9" TYPE="vfat" 
RESUME=UUID=47d9a309-0d7c-49ac-bb34-e5c5c0c9a3bc
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb2
UUID=a2bd95c1-57f2-4d57-843b-be6b9d7515a3 /               ext2    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=A890-3AE6  /media/sda1     vfat    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=497B-CB87  /media/sda5     vfat    defaults,umask=007,gid=46 0       1
# /dev/sda6
UUID=DC73-4F51  /media/sda6     vfat    defaults,umask=007,gid=46 0       1
# /dev/sdb10
UUID=92F7-894E  /media/sdb10    vfat    defaults,umask=007,gid=46 0       1
# /dev/sdb11
UUID=9027-12F2  /media/sdb11    vfat    defaults,umask=007,gid=46 0       1
# /dev/sdb12
UUID=F86D-0BF9  /media/sdb12    vfat    defaults,umask=007,gid=46 0       1
# /dev/sdb6
UUID=92F7-9A2E  /media/sdb6     vfat    defaults,umask=007,gid=46 0       1
# /dev/sdb7
UUID=901F-27D2  /media/sdb7     vfat    defaults,umask=007,gid=46 0       1
# /dev/sdb8
UUID=D82E-BBC7  /media/sdb8     vfat    defaults,umask=007,gid=46 0       1
# /dev/sdb9
UUID=25EF-147C  /media/sdb9     vfat    defaults,umask=007,gid=46 0       1
# /dev/sdb5
UUID=47d9a309-0d7c-49ac-bb34-e5c5c0c9a3bc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=a2bd95c1-57f2-4d57-843b-be6b9d7515a3 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,1)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd1,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=a2bd95c1-57f2-4d57-843b-be6b9d7515a3 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd1,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=a2bd95c1-57f2-4d57-843b-be6b9d7515a3 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd1,1)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1


```

Best regards,
Bharath

---

### Post by drs305 on 2009-01-26
I reviewed the 'pointers' for / and the swap partition and everything seems to be pointing to the correct locations. The UUIDs all are correct and I can't see any discrepancies.

You mentioned error messages. It would be helpful if you could report these to us. You might look at /var/log/dmesg , which reports actions accomplished during the first part of the boot process. You can look for "fail" or "error" messages. The log is time-stamped so you should also look for sections where there are long delays between executions.

How is the disk space ( df -h ) and memory ( free -m )- any shortage of either? Your graphics run okay once they finally kick in?

By the way, welcome to the ubuntu forums...

---

### Post by bharaths_jois on 2009-01-28
The disk space and the memory seems to be fine. But in the dmesg file, I could see that there is a 30s delay b/w```
[   26.904129] eth0:  Identified 8139 chip type 'RTL-8100'
[   56.642190] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
``` 

Although I could not find any "error" in the file, I could see the SErr quite a few times. And yes, once the GUI is up, all is fine. Below is the contents of the file dmesg:

```

[    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000026ff0000 (usable)
[    0.000000]  BIOS-e820: 0000000026ff0000 - 0000000026ff8000 (ACPI data)
[    0.000000]  BIOS-e820: 0000000026ff8000 - 0000000027000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fffc0000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 623MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 159728) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   159728
[    0.000000]   HighMem    159728 ->   159728
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   159728
[    0.000000] On node 0 totalpages: 159728
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1215 pages used for memmap
[    0.000000]   Normal zone: 154417 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00FC390 checksum 0
[    0.000000] ACPI: RSDP 000FC390, 0014 (r0 AMI   )
[    0.000000] ACPI: RSDT 26FF0000, 0028 (r1 AMIINT SiS730SX     1000 MSFT  100000B)
[    0.000000] ACPI: FACP 26FF0030, 0074 (r1 AMIINT SiS730SX     1000 MSFT  100000B)
[    0.000000] ACPI: DSDT 26FF00B0, 2D2C (r1    SiS     730S      100 MSFT  100000B)
[    0.000000] ACPI: FACS 26FF8000, 0040
[    0.000000] ACPI: BIOS age (1997) fails cutoff (2000), acpi=force is required to enable ACPI
[    0.000000] ACPI: Disabling ACPI support
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 27000000:d8fc0000)
[    0.000000] Built 1 zonelists.  Total pages: 158481
[    0.000000] Kernel command line: root=UUID=a2bd95c1-57f2-4d57-843b-be6b9d7515a3 ro quiet splash
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffd000 (014ee000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1244.508 MHz processor.
[   20.728546] Console: colour VGA+ 80x25
[   20.730649] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   20.734522] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   20.781086] Memory: 621324k/638912k available (2015k kernel code, 16960k reserved, 916k data, 364k init, 0k highmem)
[   20.781105] virtual kernel memory layout:
[   20.781107]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   20.781109]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   20.781111]     vmalloc : 0xe7800000 - 0xff7fe000   ( 383 MB)
[   20.781113]     lowmem  : 0xc0000000 - 0xe6ff0000   ( 623 MB)
[   20.781115]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   20.781117]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
[   20.781119]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
[   20.781126] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   20.781226] SLUB: Genslabs=22, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   20.861178] Calibrating delay using timer specific routine.. 2490.43 BogoMIPS (lpj=4980875)
[   20.861254] Security Framework v1.0.0 initialized
[   20.861273] SELinux:  Disabled at boot.
[   20.861309] Mount-cache hash table entries: 512
[   20.861656] CPU: After generic identify, caps: 0183f9ff c1c3f9ff 00000000 00000000 00000000 00000000 00000000
[   20.861670] Enabling disabled K7/SSE Support.
[   20.861675] CPU: CLK_CTL MSR was 6003d22f. Reprogramming to 2003d22f
[   20.861682] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   20.861687] CPU: L2 Cache: 256K (64 bytes/line)
[   20.861693] CPU: After all inits, caps: 0383f9ff c1c3f9ff 00000000 00000420 00000000 00000000 00000000
[   20.861718] Compat vDSO mapped to ffffe000.
[   20.861748] Checking 'hlt' instruction... OK.
[   20.877506] SMP alternatives: switching to UP code
[   20.878195] Freeing SMP alternatives: 11k freed
[   20.879070] Early unpacking initramfs... done
[   21.447277] CPU0: AMD Athlon(tm) Processor stepping 01
[   21.447293] SMP motherboard not detected.
[   21.447299] Local APIC not detected. Using dummy APIC emulation.
[   21.447421] Brought up 1 CPUs
[   21.447820] Booting paravirtualized kernel on bare hardware
[   21.447973] Time: 23:24:52  Date: 00/28/109
[   21.448072] NET: Registered protocol family 16
[   21.448338] EISA bus registered
[   21.450994] PCI: PCI BIOS revision 2.10 entry at 0xfdb01, last bus=1
[   21.451000] PCI: Using configuration type 1
[   21.451003] Setting up standard PCI resources
[   21.452761] ACPI: Interpreter disabled.
[   21.452771] Linux Plug and Play Support v0.97 (c) Adam Belay
[   21.452789] pnp: PnP ACPI: disabled
[   21.452798] PnPBIOS: Scanning system for PnP BIOS support...
[   21.452837] PnPBIOS: Found PnP BIOS installation structure at 0xc00f7d80
[   21.452843] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0x6b44, dseg 0xf0000
[   21.454329] PnPBIOS: 15 nodes reported by PnP BIOS; 15 recorded by driver
[   21.454439] PCI: Probing PCI hardware
[   21.454459] PCI: Probing PCI hardware (bus 00)
[   21.455843] PCI: Using IRQ router SIS [1039/0018] at 0000:00:01.0
[   21.457735] NET: Registered protocol family 8
[   21.457740] NET: Registered protocol family 20
[   21.457902] pnp: 00:01: iomem range 0x0-0x9fbff could not be reserved
[   21.457908] pnp: 00:01: iomem range 0x9fc00-0x9ffff could not be reserved
[   21.457913] pnp: 00:01: iomem range 0xf0000-0xfffff could not be reserved
[   21.457918] pnp: 00:01: iomem range 0x100000-0x26feffff could not be reserved
[   21.458543] PCI: Bridge: 0000:00:02.0
[   21.458548]   IO window: b000-bfff
[   21.458557]   MEM window: cfe00000-cfefffff
[   21.458563]   PREFETCH window: bfc00000-cfcfffff
[   21.458584] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   21.458611] NET: Registered protocol family 2
[   21.460595] Time: tsc clocksource has been installed.
[   21.488743] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   21.489305] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   21.496973] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   21.499678] TCP: Hash tables configured (established 131072 bind 65536)
[   21.499688] TCP reno registered
[   21.508908] checking if image is initramfs... it is
[   22.644278] Freeing initrd memory: 7289k freed
[   22.645277] audit: initializing netlink socket (disabled)
[   22.645316] audit(1233185093.684:1): initialized
[   22.649248] VFS: Disk quotas dquot_6.5.1
[   22.649382] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   22.649710] io scheduler noop registered
[   22.649716] io scheduler anticipatory registered
[   22.649719] io scheduler deadline registered
[   22.649747] io scheduler cfq registered (default)
[   22.649819] Boot video device is 0000:01:00.0
[   22.650184] isapnp: Scanning for PnP cards...
[   23.003461] isapnp: No Plug & Play device found
[   23.074711] Real Time Clock Driver v1.12ac
[   23.074868] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   23.075142] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   23.077135] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   23.078952] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   23.079692] input: Macintosh mouse button emulation as /class/input/input0
[   23.079882] PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[   23.080345] serio: i8042 KBD port at 0x60,0x64 irq 1
[   23.080357] serio: i8042 AUX port at 0x60,0x64 irq 12
[   23.080669] mice: PS/2 mouse device common for all mice
[   23.080922] EISA: Probing bus 0 at eisa.0
[   23.080961] Cannot allocate resource for EISA slot 5
[   23.080982] EISA: Detected 0 cards.
[   23.081482] TCP cubic registered
[   23.081503] NET: Registered protocol family 1
[   23.081551] Using IPI No-Shortcut mode
[   23.081755]   Magic number: 9:887:454
[   23.083668] Freeing unused kernel memory: 364k freed
[   23.107190] input: AT Translated Set 2 keyboard as /class/input/input1
[   24.498269] AppArmor: AppArmor initialized<5>audit(1233185095.684:2):  type=1505 info="AppArmor initialized" pid=1123
[   24.515578] fuse init (API version 7.8)
[   24.527824] Failure registering capabilities with primary security module.
[   24.570745] thermal: Unknown symbol acpi_processor_set_thermal_limit
[   25.779667] SCSI subsystem initialized
[   25.789103] libata version 2.21 loaded.
[   25.795299] pata_sis 0000:00:00.1: version 0.5.1
[   25.795732] scsi0 : pata_sis
[   25.795844] scsi1 : pata_sis
[   25.795922] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001ff00 irq 14
[   25.795929] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001ff08 irq 15
[   25.834049] usbcore: registered new interface driver usbfs
[   25.834116] usbcore: registered new interface driver hub
[   25.834166] usbcore: registered new device driver usb
[   25.835975] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   26.033803] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   26.112404] ata1.00: ATAPI: SONY    DVD RW AW-G170A, 1.62, max UDMA/66
[   26.191410] Floppy drive(s): fd0 is 1.44M
[   26.241070] FDC 0 is a post-1991 82077
[   26.284140] ata1.00: configured for UDMA/66
[   26.456022] ata2.00: ATA-6: ST340015A, 3.01, max UDMA/100
[   26.456033] ata2.00: 78165360 sectors, multi 16: LBA 
[   26.502180] ata2.01: ATA-7: ST3160215A, 3.AAD, max UDMA/100
[   26.502189] ata2.01: 312581808 sectors, multi 16: LBA48 
[   26.515997] ata2.00: configured for UDMA/100
[   26.576985] ata2.01: configured for UDMA/100
[   26.578185] scsi 0:0:0:0: CD-ROM            SONY     DVD RW AW-G170A  1.62 PQ: 0 ANSI: 5
[   26.579236] scsi 1:0:0:0: Direct-Access     ATA      ST340015A        3.01 PQ: 0 ANSI: 5
[   26.579860] scsi 1:0:1:0: Direct-Access     ATA      ST3160215A       3.AA PQ: 0 ANSI: 5
[   26.580297] PCI: setting IRQ 5 as level-triggered
[   26.580303] PCI: Found IRQ 5 for device 0000:00:01.2
[   26.580314] PCI: Sharing IRQ 5 with 0000:00:01.3
[   26.580349] ohci_hcd 0000:00:01.2: OHCI Host Controller
[   26.580833] ohci_hcd 0000:00:01.2: new USB bus registered, assigned bus number 1
[   26.580874] ohci_hcd 0000:00:01.2: irq 5, io mem 0xcfffc000
[   26.628237] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[   26.628253] Uniform CD-ROM driver Revision: 3.20
[   26.628867] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   26.638319] usb usb1: configuration #1 chosen from 1 choice
[   26.638397] hub 1-0:1.0: USB hub found
[   26.638430] hub 1-0:1.0: 3 ports detected
[   26.642799] sr 0:0:0:0: Attached scsi generic sg0 type 5
[   26.643077] sd 1:0:0:0: Attached scsi generic sg1 type 0
[   26.643348] scsi 1:0:1:0: Attached scsi generic sg2 type 0
[   26.672482] sd 1:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[   26.672723] sd 1:0:0:0: [sda] Write Protect is off
[   26.672728] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   26.672765] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   26.673078] sd 1:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[   26.673096] sd 1:0:0:0: [sda] Write Protect is off
[   26.673100] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   26.673126] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   26.673136]  sda:<6>PCI: Found IRQ 5 for device 0000:00:01.3
[   26.739809] PCI: Sharing IRQ 5 with 0000:00:01.2
[   26.739851] ohci_hcd 0000:00:01.3: OHCI Host Controller
[   26.739913] ohci_hcd 0000:00:01.3: new USB bus registered, assigned bus number 2
[   26.739948] ohci_hcd 0000:00:01.3: irq 5, io mem 0xcfffd000
[   26.797544] usb usb2: configuration #1 chosen from 1 choice
[   26.797607] hub 2-0:1.0: USB hub found
[   26.797635] hub 2-0:1.0: 3 ports detected
[   26.899879] 8139cp 0000:00:09.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[   26.899894] 8139cp 0000:00:09.0: Try the "8139too" driver instead.
[   26.903560] 8139too Fast Ethernet driver 0.9.28
[   26.903683] PCI: setting IRQ 3 as level-triggered
[   26.903688] PCI: Found IRQ 3 for device 0000:00:09.0
[   26.904123] eth0: RealTek RTL8139 at 0xe7832f00, 00:e0:4c:77:13:55, IRQ 3
[   26.904129] eth0:  Identified 8139 chip type 'RTL-8100'
[   56.642190] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[   56.642214] ata2.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 cdb 0x0 data 4096 in
[   56.642217]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[   56.642240] ata2: soft resetting port
[   56.858251] ata2.00: configured for UDMA/100
[   56.901816] ata2.01: configured for UDMA/100
[   56.901869] ata2: EH complete
[   86.872552] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[   86.872575] ata2.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 cdb 0x0 data 4096 in
[   86.872578]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[   86.872601] ata2: soft resetting port
[   87.088650] ata2.00: configured for UDMA/100
[   87.134254] ata2.01: configured for UDMA/100
[   87.134303] ata2: EH complete
[  117.102948] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  117.102971] ata2.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 cdb 0x0 data 4096 in
[  117.102974]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[  117.102997] ata2: soft resetting port
[  117.323015] ata2.00: configured for UDMA/100
[  117.366091] ata2.01: configured for UDMA/100
[  117.366140] ata2: EH complete
[  147.333302] ata2.00: limiting speed to UDMA/66:PIO4
[  147.333317] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  147.333334] ata2.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 cdb 0x0 data 4096 in
[  147.333337]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[  147.333359] ata2: soft resetting port
[  147.553347] ata2.00: configured for UDMA/66
[  147.597517] ata2.01: configured for UDMA/100
[  147.597566] ata2: EH complete
[  147.601149]  sda1 sda2 <<5>sd 1:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[  147.623576] sd 1:0:0:0: [sda] Write Protect is off
[  147.623581] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  147.623599]  sda5<5>sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  147.648182]  sda6 >
[  147.648493] sd 1:0:0:0: [sda] Attached SCSI disk
[  147.650242] sd 1:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[  147.650271] sd 1:0:1:0: [sdb] 312581808 512-byte hardware sectors (160042 MB)
[  147.650295] sd 1:0:0:0: [sda] Write Protect is off
[  147.650300] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  147.650313] sd 1:0:1:0: [sdb] Write Protect is off
[  147.650316] sd 1:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[  147.650361] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  147.650375] sd 1:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  147.650499] sd 1:0:1:0: [sdb] 312581808 512-byte hardware sectors (160042 MB)
[  147.650516] sd 1:0:1:0: [sdb] Write Protect is off
[  147.650520] sd 1:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[  147.650546] sd 1:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  147.650553]  sdb:<3>ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  177.619633] ata2.01: cmd c8/00:08:00:00:00/00:00:00:00:00/f0 tag 0 cdb 0x0 data 4096 in
[  177.619637]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[  177.619664] ata2: soft resetting port
[  177.835631] ata2.00: configured for UDMA/66
[  177.886109] ata2.01: configured for UDMA/100
[  177.886152] ata2: EH complete
[  207.853988] ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  207.854065] ata2.01: cmd c8/00:08:00:00:00/00:00:00:00:00/f0 tag 0 cdb 0x0 data 4096 in
[  207.854068]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[  207.854136] ata2: soft resetting port
[  208.070004] ata2.00: configured for UDMA/66
[  208.139860] ata2.01: configured for UDMA/100
[  208.139895] ata2: EH complete
[  208.140068] sd 1:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[  238.108339] ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  238.108403] ata2.01: cmd c8/00:08:00:00:00/00:00:00:00:00/f0 tag 0 cdb 0x0 data 4096 in
[  238.108406]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[  238.108476] ata2: soft resetting port
[  238.324359] ata2.00: configured for UDMA/66
[  238.376163] ata2.01: configured for UDMA/100
[  238.376191] ata2: EH complete
[  238.376353] sd 1:0:0:0: [sda] Write Protect is off
[  238.376358] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  268.346664] ata2.01: limiting speed to UDMA/66:PIO4
[  268.346670] ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  268.346723] ata2.01: cmd c8/00:08:00:00:00/00:00:00:00:00/f0 tag 0 cdb 0x0 data 4096 in
[  268.346726]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[  268.346783] ata2: soft resetting port
[  268.566719] ata2.00: configured for UDMA/66
[  268.620201] ata2.01: configured for UDMA/66
[  268.620209] ata2: EH complete
[  268.668108] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  268.668191]  sdb1 <<5>sd 1:0:1:0: [sdb] 312581808 512-byte hardware sectors (160042 MB)
[  268.678725]  sdb5<5>sd 1:0:1:0: [sdb] Write Protect is off
[  268.682520] sd 1:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[  268.685921]  sdb6<5>sd 1:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  268.702576]  sdb7<5>sd 1:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[  268.730212]  sdb8<5>sd 1:0:0:0: [sda] Write Protect is off
[  268.739720] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  268.739733]  sdb9 sdb10<5>sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  268.795318]  sdb11 sdb12 > sdb2
[  268.810359] sd 1:0:1:0: [sdb] 312581808 512-byte hardware sectors (160042 MB)
[  268.814011] sd 1:0:1:0: [sdb] Attached SCSI disk
[  268.814342] sd 1:0:1:0: [sdb] Write Protect is off
[  268.814348] sd 1:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[  268.822346] sd 1:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  275.362310] Attempting manual resume
[  275.362322] swsusp: Resume From Partition 8:21
[  275.362325] PM: Checking swsusp image.
[  275.375805] PM: Resume from disk failed.
[  283.131119] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[  284.356628] NET: Registered protocol family 10
[  284.356845] lo: Disabled Privacy Extensions
[  287.533598] Linux agpgart interface v0.102 (c) Dave Jones
[  288.195275] agpgart: Detected SiS chipset - id:1840
[  288.204420] agpgart: AGP aperture is 64M @ 0xd0000000
[  288.224450] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[  288.228257] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[  288.300863] input: PC Speaker as /class/input/input2
[  288.968740] PCI: setting IRQ 11 as level-triggered
[  288.968752] PCI: Found IRQ 11 for device 0000:00:01.4
[  289.065759] input: PS/2 Logitech Mouse as /class/input/input3
[  289.069459] parport_pc 00:0c: reported by Plug and Play BIOS
[  289.069534] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[  292.460650] Clocksource tsc unstable (delta = 2280161323 ns)
[  292.490267] Time: pit clocksource has been installed.
[  293.591558] MC'97 1 converters and GPIO not ready (0x800f)
[  293.608231] gameport: Trident 4DWave is pci0000:00:01.4/gameport0, speed 2130kHz
[  293.717141] ac97 codec read TIMEOUT [0x5a/0x800fc05a]!!!
[  293.746891] ac97 codec read TIMEOUT [0x54/0x800fc0d4]!!!
[  294.377437] lp0: using parport0 (interrupt-driven).
[  294.466590] Adding 819272k swap on /dev/sdb5.  Priority:-1 extents:1 across:819272k
[  298.045575] eth0: no IPv6 routers present

```

---

### Post by drs305 on 2009-01-29
It seems to me the majority of the time is spent from 56:00 on dealing with drive issues. I don't know how to interpret them but hopefully someone knowledgeable in this area will be able to provide some insight. 

Consider this post a bump to assist in finding someone who can discern the problem.

---

### Post by bharaths_jois on 2009-01-30
Hi ppl,

  Can anybody please look into this and let me know what is the problem? 

Best regards,
Bharath

---

### Post by sumit.kalra999 on 2009-01-30
Hi,
just press "Alt + F 7" or "Alt + F 6" or "Alt + F 5" or "Alt + F 4" or "Alt + F 3" or "Alt + F 2" or "Alt + F 1"
There are 7 terminals, only one of them is GUI based, all other are text based

---

### Post by avtolle on 2009-01-30
[http://www.ubuntu.com/getubuntu/releasenotes/810](http://www.ubuntu.com/getubuntu/releasenotes/810) and scroll down the page to a discussion of a similar problem with Intel 945 motherboard, and the solution offered.

---

### Post by bharaths_jois on 2009-01-30
The problem is very similar to what is mentioned in [http://www.ubuntu.com/getubuntu/releasenotes/810](http://www.ubuntu.com/getubuntu/releasenotes/810), but the messages I see are different than what is told there.

I also tried the solution proposed in [http://www.ubuntu.com/getubuntu/releasenotes/810](http://www.ubuntu.com/getubuntu/releasenotes/810). But it did not help me, though I read it is a work around. Moreover, I read that this problem has popped up in version 08.10. I am presently using Ubuntu 07.10.

Somehow I feel it is a problem with my hard disk (not sure!), which I don't know to solve. I tried changing the BIOS options as suggested, but only to find out that it did not help me.

Here are a few more details:

AMD Athlon XP 2000+, 640MB RAM
A 40GB SATA on primary - WinXP there - Has 4 volumes - All FAT32

A 160GB SATA on secondary - Linux here - Has 9 volumes - 1 ext2, 1 swap, rest all FAT32

In the GRUB menu, I choose the kernel to be Linux (Ubuntu 7.10, kernel 2.6.22-14-generic = /boot/vmlinuz-2.6.22-14-generic root=UUID=a2bd95c1-57f2-4d57-843b-be6b9d7515a3 ro quiet splash)

After this I can see the splash screen but no activity. I will get back with the result of the boot command /boot/vmlinuz-2.6.22-14-generic root=UUID=a2bd95c1-57f2-4d57-843b-be6b9d7515a3 ro no splash in some time.

After some time,I can see the Busy Box showing (initramfs) and I can see the string "exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen" quite a few times.

If I use exit, it does not work immediately, i.e. the system does not respond to it. If I do the same after some time (maybe after a minute), only then it starts: Reading files required to boot..........     [OK] stuff.

After this, I can see the fsck in the picture and it shows me a message which indicates that 
There are differences in bootsector and its backup. Not automatically fixing this and then continues into the GUI. Once the GUI comes up, I see/experience no problems (till now, at least)

The logs and messages show me:
```
[   26.904129] eth0:  Identified 8139 chip type 'RTL-8100'
[   56.642190] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[   56.642214] ata2.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 cdb 0x0 data 4096 in
[   56.642217]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[   56.642240] ata2: soft resetting port
[   56.858251] ata2.00: configured for UDMA/100
[   56.901816] ata2.01: configured for UDMA/100
[   56.901869] ata2: EH complete

```
And this repeats itself after every 30 seconds.

Kindly let me know if more inputs are required.

Regards,
Bharath

---

### Post by bharaths_jois on 2009-01-30
The command ```
/boot/vmlinuz-2.6.22-14-generic root=UUID=a2bd95c1-57f2-4d57-843b-be6b9d7515a3 ro no splash 
``` resulted in the same delay.
But this time, I got to know where it was stuck.
After "Loading essential drivers", it continuously showed 
"Waiting for root file system..." So, I guess this is where is the problem is. Solution????

---

### Post by ugm6hr on 2009-01-30
I am afraid I have no idea what the issue is.

However, Ubuntu 7.10 only has about 3 months of support remaining.

I think the effort involved in solving this may be misspent; I suggest you install a newer version (8.04 or 8.10), and see if the problem persists.

---

### Post by bharaths_jois on 2009-01-30
Oh! In that case, I will install the newer versions and check the problem.

---

### Post by drs305 on 2009-01-30
> ```
/boot/vmlinuz-2.6.22-14-generic root=UUID=a2bd95c1-57f2-4d57-843b-be6b9d7515a3 ro **no splash** 
```

Try removing "no splash".  Don't know how much trouble that might cause but it may help.

---

### Post by bharaths_jois on 2009-02-05
Ubuntu 08.10 on. Now, she is running fast, faster than ever. Solved!!

Thank you guys.:D

---

