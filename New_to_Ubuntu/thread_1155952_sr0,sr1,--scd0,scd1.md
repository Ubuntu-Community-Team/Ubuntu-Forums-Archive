---
title: "sr0,sr1,--scd0,scd1"
date: 2009-05-11
forum: New to Ubuntu
---

### Post by mickey57 on 2009-05-11
....Here's the situation;
.....I am using the 32 bit 9.04 now.Tried the 64 bit but after 2 weeks of pure frustration about my dvd and cd rom drives being totally out of wack I went to the 32bit.Believe me,I searched everywhere for the fix.Reconfigured the fstab time and time again,tried the noapic and adpi=off,to no avail.I used my dogs paw to reformat that HD :P
.....I am determined to understand the configuration of fstab.
.....When I first installed the 32bit,my DVD drive was not recognized so I went into fstab and~/dev/scd0       /media/cdrom1  udf,iso9660 user,noauto,exec,utf8 0       0
.....My CD rom is: /dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
............and this works but I just don't understand the:
mickey@mickey-desktop:~$ cd /dev
mickey@mickey-desktop:/dev$ ls -al cdr*
lrwxrwxrwx 1 root root 3 2009-05-10 19:07 cdrom -> sr1
lrwxrwxrwx 1 root root 3 2009-05-10 19:07 cdrom1 -> sr0
lrwxrwxrwx 1 root root 3 2009-05-10 19:07 cdrw1 -> sr0
mickey@mickey-desktop:/dev$ 
*******************************************
mickey@mickey-desktop:~$ sudo lshw -C disk
[sudo] password for mickey: 
  *-disk:0                
       description: ATA Disk
       product: WDC WD800JB-00JJ
       vendor: Western Digital
       physical id: 0
       bus info: scsi@2:0.0.0
       logical name: /dev/sda
       version: 05.0
       serial: WD-WCAM9S263707
       size: 74GiB (80GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=0c8acc5d
  *-disk:1
       description: ATA Disk
       product: Maxtor 6L080P0
       vendor: Maxtor
       physical id: 1
       bus info: scsi@2:0.1.0
       logical name: /dev/sdb
       version: BAH4
       serial: L2262S3G    L2262S3G
       size: 74GiB (80GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=f18df18d
  *-cdrom:0
       description: DVD reader
       product: DVD+RW 4X4X12
       vendor: ATAPI
       physical id: 2
       bus info: scsi@3:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/cdrw1
       logical name: /dev/dvd1
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: B1GY
       capabilities: removable audio cd-r cd-rw dvd
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom1
  *-cdrom:1
       description: SCSI CD-ROM
       product: CD-ROM LTN-5291S
       vendor: LITE-ON
       physical id: 3
       bus info: scsi@3:0.1.0
       logical name: /dev/cdrom
       logical name: /dev/scd1
       logical name: /dev/sr1
       version: NS08
       capabilities: removable audio
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
mickey@mickey-desktop:~$ 
**********************************
n't support DPO or FUA
[    2.621802]  sdb: sdb1 sdb2
[    2.655499] sd 2:0:1:0: [sdb] Attached SCSI disk
[    2.655532] sd 2:0:1:0: Attached scsi generic sg1 type 0
[    2.657811] scsi 3:0:0:0: CD-ROM            ATAPI    DVD+RW 4X4X12    B1GY PQ: 0 ANSI: 5
[    2.660739] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[    2.660743] Uniform CD-ROM driver Revision: 3.20
[    2.660825] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    2.660858] sr 3:0:0:0: Attached scsi generic sg2 type 5
[    2.670983] scsi 3:0:1:0: CD-ROM            LITE-ON  CD-ROM LTN-5291S NS08 PQ: 0 ANSI: 5
[    2.672366] sr1: scsi3-mmc drive: 4x/40x cd/rw xa/form2 cdda tray
[    2.672422] sr 3:0:1:0: Attached scsi CD-ROM sr1
[    2.672455] sr 3:0:1:0: Attached scsi generic sg3 type 5
[    2.672603] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.672831] ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 21
[    2.672838] ehci_hcd 0000:00:10.4: PCI INT C -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[    2.672864] ehci_hcd 0000:00:10.4: EHCI Host Controller
[    2.672921] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 1
[    2.672983] ehci_hcd 0000:00:10.4: irq 21, io mem 0xfb000000
[    2.684014] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00
[    2.684080] usb usb1: configuration #1 chosen from 1 choice
[    2.684108] hub 1-0:1.0: USB hub found
[    2.684116] hub 1-0:1.0: 8 ports detected
[    2.684211] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.684228] uhci_hcd: USB Universal Host Controller Interface driver
[    2.684258] uhci_hcd 0000:00:10.0: PCI INT A -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[    2.684264] uhci_hcd 0000:00:10.0: UHCI Host Controller
[    2.684310] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 2
[    2.684330] uhci_hcd 0000:00:10.0: irq 21, io base 0x0000df00
[    2.684397] usb usb2: configuration #1 chosen from 1 choice
[    2.684420] hub 2-0:1.0: USB hub found
[    2.684426] hub 2-0:1.0: 2 ports detected
[    2.684500] uhci_hcd 0000:00:10.1: PCI INT A -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[    2.684506] uhci_hcd 0000:00:10.1: UHCI Host Controller
[    2.684546] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 3
[    2.684564] uhci_hcd 0000:00:10.1: irq 21, io base 0x0000e000
[    2.684629] usb usb3: configuration #1 chosen from 1 choice
[    2.684652] hub 3-0:1.0: USB hub found
[    2.684658] hub 3-0:1.0: 2 ports detected
[    2.684733] uhci_hcd 0000:00:10.2: PCI INT B -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[    2.684738] uhci_hcd 0000:00:10.2: UHCI Host Controller
[    2.684775] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 4
[    2.684793] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000e100
[    2.684863] usb usb4: configuration #1 chosen from 1 choice
[    2.684885] hub 4-0:1.0: USB hub found
[    2.684891] hub 4-0:1.0: 2 ports detected
[    2.684962] uhci_hcd 0000:00:10.3: PCI INT B -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[    2.684967] uhci_hcd 0000:00:10.3: UHCI Host Controller
[    2.685017] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 5
[    2.685034] uhci_hcd 0000:00:10.3: irq 21, io base 0x0000e200
[    2.685102] usb usb5: configuration #1 chosen from 1 choice
[    2.685125] hub 5-0:1.0: USB hub found
[    2.685134] hub 5-0:1.0: 2 ports detected
[    2.685242] usbcore: registered new interface driver libusual
[    2.685272] usbcore: registered new interface driver usbserial
[    2.685282] USB Serial support registered for generic
[    2.685296] usbcore: registered new interface driver usbserial_generic
[    2.685298] usbserial: USB Serial Driver core
[    2.685340] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.685752] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.685758] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.689040] mice: PS/2 mouse device common for all mice
[    2.705058] rtc_cmos 00:05: RTC can wake from S4
[    2.705097] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    2.705149] rtc0: alarms up to one year, y3k, 242 bytes nvram
[    2.705207] device-mapper: uevent: version 1.0.3
[    2.705305] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [email]dm-devel@redhat.com[/email]
[    2.705419] device-mapper: multipath: version 1.0.5 loaded
[    2.705421] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.705510] EISA: Probing bus 0 at eisa.0
[    2.705530] Cannot allocate resource for EISA slot 4
[    2.705532] Cannot allocate resource for EISA slot 5
[    2.705545] EISA: Detected 0 cards.
[    2.705621] cpuidle: using governor ladder
[    2.705623] cpuidle: using governor menu
[    2.706100] TCP cubic registered
[    2.706195] NET: Registered protocol family 10
[    2.706576] lo: Disabled Privacy Extensions
[    2.706870] NET: Registered protocol family 17
[    2.706885] Bluetooth: L2CAP ver 2.11
[    2.706887] Bluetooth: L2CAP socket layer initialized
[    2.706890] Bluetooth: SCO (Voice Link) ver 0.6
[    2.706892] Bluetooth: SCO socket layer initialized
[    2.706926] Bluetooth: RFCOMM socket layer initialized
[    2.706934] Bluetooth: RFCOMM TTY layer initialized
[    2.706936] Bluetooth: RFCOMM ver 1.10
[    2.706980] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ processors (2 cpu cores) (version 2.20.00)
[    2.707030] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0xe
[    2.707032] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x10
[    2.707034] powernow-k8:    2 : fid 0x2 (1000 MHz), vid 0x12
[    2.707087] Using IPI No-Shortcut mode
[    2.707177] registered taskstats version 1
[    2.707302]   Magic number: 9:823:141
[    2.707328] block ram6: hash matches
[    2.707360] acpi device:12: hash matches
[    2.707413] rtc_cmos 00:05: setting system clock to 2009-05-10 19:07:35 UTC (1241982455)
[    2.707416] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.707418] EDD information not available.
[    2.707726] Freeing unused kernel memory: 532k freed
[    2.707872] Write protecting the kernel text: 4128k
[    2.707924] Write protecting the kernel read-only data: 1532k
[    2.721391] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    2.938174] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[    2.938178] via-rhine: Broken BIOS detected, avoid_D3 enabled.
[    2.938438] ACPI: PCI Interrupt Link [ALKD] enabled at IRQ 23
[    2.938447] via-rhine 0000:00:12.0: PCI INT A -> Link[ALKD] -> GSI 23 (level, low) -> IRQ 23
[    3.061830] eth0: VIA Rhine II at 0xfb001000, 00:e0:4d:43:c1:93, IRQ 23.
[    3.062541] eth0: MII PHY found at address 1, status 0x786d advertising 01e1 Link 41e1.
[    3.078781] Floppy drive(s): fd0 is 1.44M
[    3.099943] FDC 0 is a post-1991 82077
[    3.554132] PM: Starting manual resume from disk
[    3.554135] PM: Resume from partition 8:5
[    3.554137] PM: Checking hibernation image.
[    3.554381] PM: Resume from disk failed.
[    3.557781] EXT3-fs: INFO: recovery required on readonly filesystem.
[    3.557785] EXT3-fs: write access will be enabled during recovery.
[    3.604020] usb 2-1: new full speed USB device using uhci_hcd and address 2
[    3.822344] usb 2-1: configuration #1 chosen from 2 choices
[    4.085015] usb 3-2: new full speed USB device using uhci_hcd and address 2
[    4.269410] usb 3-2: configuration #1 chosen from 1 choice
[    4.286358] usbcore: registered new interface driver hiddev
[    4.291398] generic-usb 0003:043D:010B.0001: hiddev96,hidraw0: USB HID v1.00 Device [Lexmark  2500 Series] on usb-0000:00:10.1-2/input2
[    4.291421] usbcore: registered new interface driver usbhid
[    4.291424] usbhid: v2.6:USB HID core driver
[    4.926684] kjournald starting.  Commit interval 5 seconds
[    4.926698] EXT3-fs: sda1: orphan cleanup on readonly fs
[    4.926703] ext3_orphan_cleanup: deleting unreferenced inode 409624
[    4.926728] EXT3-fs: sda1: 1 orphan inode deleted
[    4.926730] EXT3-fs: recovery complete.
[    4.949555] EXT3-fs: mounted filesystem with ordered data mode.
[   10.166210] udev: starting version 141
[   10.656349] parport_pc 00:0a: reported by Plug and Play ACPI
[   10.656394] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
***********************************************
.......This works (for now)but they could blink out on me any sec,lol and there inlays the problem I ahve been having.It is the sr0,sr1,--scd0,scd1,I am trying to understand.What is calling the drives this?Root?
...I did find out,somewhere in my searching,about the scd0 having to be associated with cdrom1 and the scd1 having to associated with cdrom0,because of what grub calls up and the difference in what Ubuntu calls up.Hope I explained it well enough
 for someone to help me with this.
.........Mickey:confused:

---

### Post by unutbu on 2009-05-11
This line 
```

# Compatibility symlinks for /dev/scd* devices
SUBSYSTEMS=="scsi", KERNEL=="sr[0-9]*",	SYMLINK+="%k"
```

in /etc/udev/rules.d/60-symlinks.rules creates the symlink(s) from /dev/sr0 to /dev/scd0.

---

### Post by mickey57 on 2009-05-11
> **unutbu said:**
> This line 
```

# Compatibility symlinks for /dev/scd* devices
SUBSYSTEMS=="scsi", KERNEL=="sr[0-9]*",	SYMLINK+="%k"
```

in /etc/udev/rules.d/60-symlinks.rules creates the symlink(s) from /dev/sr0 to /dev/scd0.

**************************************************
...KERNEL=="sr[0-9]*"~~~~~Thanks dude..When I go back to try the 64 bit again I will be prepared!Never could get it to boot up without going into recovery mode..:rolleyes:

---

### Post by mickey57 on 2009-05-11
Here we go again.Poof and their gone...
***
From this:lshw -C disk
       capabilities: removable audio cd-r cd-rw dvd
       [COLOR="Red"]configuration: ansiversion=5 status=ready[/COLOR]
     *-medium
          physical id: 0
          logical name: /dev/cdrom1

       capabilities: removable audio
      [COLOR="Red"] configuration: ansiversion=5 status=ready[/COLOR]
     *-medium
          physical id: 0
          logical name: /dev/cdrom
******************[COLOR="DarkRed"]To This~~Poof~~[/COLOR]***************
       capabilities: audio cd-r cd-rw dvd
      [COLOR="Red"] configuration: status=open[/COLOR]

       capabilities: audio
      [COLOR="DarkRed"] configuration: status=open[/COLOR]
*************************
....Got to have my rom drives.
........All over the Web ya see people with this problem:confused:
**********************************
....Nothing works.The dvd drive will not even open with the button being pushed..Looks like it is time for fedora 10
~~~~~~~~~~~~~~~~~~~~~
mickey@mickey-desktop:~$ sudo eject /dev/scd1
[sudo] password for mickey: 
mickey@mickey-desktop:~$ sudo eject /dev/scd0
mickey@mickey-desktop:~$ sudo eject /dev/sr1
mickey@mickey-desktop:~$ sudo eject /dev/sr0
mickey@mickey-desktop:~$ sudo eject /dev/cdrom
mickey@mickey-desktop:~$ sudo eject /dev/cdrom0


mickey@mickey-desktop:~$ sudo eject /dev/sdb
mickey@mickey-desktop:~$ sudo eject /dev/cdrw1
mickey@mickey-desktop:~$ sudo eject /dev/dvd1
mickey@mickey-desktop:~$ sudo eject /dev/scd0
mickey@mickey-desktop:~$ sudo eject /dev/sr0
***************************************
# /etc/pmount.allow
# pmount will allow users to additionally mount all devices that are
# listed here.
/etc/scd1/pmount.allow
/etc/scd0/pmount.allow

> echo /media/cdrom >> /etc/pmount.allow &&
> echo /media/cdrom0 >> /etc/pmount.allow &&
> echo /media/cdrom1 >> /etc/pmount.allow &&
> echo /media/scd1 >> /etc/pmount.allow &&
> echo /media/scd0 >> /etc/pmount.allow &&

---

### Post by mickey57 on 2009-05-11
:confused:[SIZE="5"][COLOR="DarkRed"]No matter what i do,the two drives crap out.:confused:[/COLOR][/SIZE]

---

### Post by mickey57 on 2009-05-13
Jezzzzzzzzzz.
.....When I reboot all is fine for about 30 min or until I use a program to access the drives.
.....I have about had my fill of trying to figure this out.
...Could these differences  be the problem (scsi diffeneces from the -cat /etc/udev/rules.d/70-persistent-cd.rules--[COLOR="DarkRed"]scsi-1:0:0:0[/COLOR]-----and the --grep 'ATAPI' /var/log/kern.log---[COLOR="DarkRed"]scsi@3:0.1.0[/COLOR]---)
***********************************
mickey@mickey-desktop:~$ cat /etc/udev/rules.d/70-persistent-cd.rules
# This file maintains persistent names for CD/DVD reader and writer devices.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-cd-aliases-generator.rules
# file; however you are also free to add your own entries provided you
# add the ENV{GENERATED}=1 flag to your own rules as well.
# CD-ROM_LTN-5291S (pci-0000:00:0f.1-scsi-1:0:1:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-scsi-1:0:1:0", SYMLINK+="cdrom", ENV{GENERATED}="1"
# DVD+RW_4X4X12 (pci-0000:00:0f.1-scsi-1:0:0:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-scsi-1:0:0:0", SYMLINK+="cdrom1", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-scsi-1:0:0:0", SYMLINK+="cdrw1", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-scsi-1:0:0:0", SYMLINK+="dvd1", ENV{GENERATED}="1"
******************************************
mickey@mickey-desktop:~$ grep 'ATAPI' /var/log/kern.log
May 10 17:28:14 mickey-desktop kernel: [    2.548570] ata4.00: ATAPI: ATAPI   DVD+RW 4X4X12, B1GY, max UDMA/33
May 10 17:28:14 mickey-desktop kernel: [    2.548597] ata4.01: ATAPI: LITE-ON CD-ROM LTN-5291S, NS08, max UDMA/33
******************************************
mickey@mickey-desktop:~$ sudo lshw -C disk

  *-cdrom:0
       description: DVD reader
       physical id: 2
       bus info: scsi@3:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/cdrw1
       logical name: /dev/dvd1
       logical name: /dev/scd0
       logical name: /dev/sr0
       capabilities: audio cd-r cd-rw dvd
       configuration: status=open
  *-cdrom:1
       description: SCSI CD-ROM
       physical id: 3
       bus info: scsi@3:0.1.0
       logical name: /dev/cdrom
       logical name: /dev/scd1
       logical name: /dev/sr1
       capabilities: audio
       configuration: status=open
*******************************************
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=19baa576-2c23-43a0-a2b0-989342bab7d8 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=958e4595-4b07-49ad-bc91-b2a470139923 none            swap    sw              0       0
/dev/scd1       /media/cdrom,user,noauto,exec,utf8           0       0
/dev/scd0       /media/cdrom1,user,noauto,exec,utf8          0       0
/dev/fd0        /media/floppy0,noauto    rw,user,noauto,exec,utf8 0       0

---

### Post by mickey57 on 2009-05-15
[SIZE="4"][COLOR="DarkRed"][SIZE="4"][COLOR="DarkRed"]....Just a heads up about this issue.
.......No matter what I did it didn't help the problem.Worked on this for two weeks.About two hours ago I decided to not access my NTFS partion,then used and abused my cd and dvd roms...Played them,ejected them,movies and tunes.All is well while not accessing my XP partion. [/COLOR][/SIZE][/COLOR][/SIZE]

---

### Post by mickey57 on 2009-05-15
[SIZE="4"]Back to the same crap.but found this.Why in the hell would a new kernell need this[/SIZE]
[    1.550676] Driver 'sd' needs updating - please use bus_type methods
[    1.550685] Driver 'sr' needs updating - please use bus_type methods

[http://www.mail-archive.com/linux-acpi@vger.kernel.org/msg10993.html]("http://www.mail-archive.com/linux-acpi@vger.kernel.org/msg10993.html")

[SIZE="5"]...[COLOR="DarkRed"]I give up for the day[/COLOR][/SIZE]

---

### Post by mickey57 on 2009-05-17
[COLOR="DarkRed"][SIZE="4"]Here is what i did.

....sudo gedit /etc/pmount.allow
.....Put your fstab configurations for your CD and DVD and whatever else you have in there.Like this;[/SIZE][/COLOR]
********
# /etc/pmount.allow
# pmount will allow users to additionally mount all devices that are
# listed here.
[COLOR="DarkRed"]/dev/scd1       /media/cdrom0  users,r autohide,exec,udf          0       0
/dev/scd0       /media/cdrom1  users,rw autohide,exec,udf         0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0[/COLOR]
************************************
[COLOR="Red"][SIZE="3"]....This seems to work;)[/SIZE][/COLOR]

---

