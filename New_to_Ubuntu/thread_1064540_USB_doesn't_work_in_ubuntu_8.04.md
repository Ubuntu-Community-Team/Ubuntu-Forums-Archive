---
title: "USB doesn't work in ubuntu 8.04?"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by xinman on 2009-02-08
Ok, I've used ubuntu for a few years now on the server side of things.  I recently had my main computers hard drive crash so instead of reloading XP I decided to give ubuntu a try on the desktop.  For the most part I like it and I would love to stick with it. But I work on a lot of windows machines etc and I need to be able to download stuff to my jump drives and stuff.  It seems that none of my jump drives work in ubuntu and none of the card readers work in ubuntu.  I also tried installing a usb mouse and it doesn't work?  Can anyone help me get my usb working, I'm afraid that without it I will be forced to move back to XP and I really don't want to.  Any thoughts would be great.  I am running gnome, Kernel 2.6.24-23 generic.  Both of the jump drives I've tried are standard sandisk brands, the mouse was a logitech usb optical mouse and the card readers were both generic card readers with 3 different sd cards.  I've been working on this for a few days and I've searched around but I cannot seem to find an answer, please help me.

TIA,
Dan

---

### Post by SunnyRabbiera on 2009-02-08
Ubuntu should work with USB, its the device that might be the issue.
Like your mouse, do you have a brand?
I blame the device before I blame ubuntu

---

### Post by &#32 Greg on 2009-02-08
Try running sudo fdisk -l to identify the name of your drive, and then 
mkdir /home/USERNAME/usb
sudo mount /dev/sdc1 /home/USERNAME/usb
for a temporary solution.

---

### Post by mc4man on 2009-02-08
there is a mount debug command for external drives that may or may not provide some useful info.

You need to know the /dev/sdxx first, (fdisk -l  with the drive inserted should tell (or sudo lshw -c disk - stick a 1 on what's shown, sdb = sdb1, sdc = sdc1 ect.

```
gnome-mount -vbd /dev/sd[COLOR="Red"]b1[/COLOR]
```

---

### Post by xinman on 2009-02-08
SunnyRabbiera: You must not have read my post, I said I have tried 5 devices and the mouse was a logitech.  Read the post fully before you blame anything.

Greg: Here is the output of sudo fdisk -l

```
xinman@xinman-desktop:~$ sudo fdisk -l
[sudo] password for xinman:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x704c1840

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x49f69a22

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001    7  HPFS/NTFS
```

It literally doesn't see the drive at all this is a sandisk cruzer 4 gb. Same output if I plug in a sandisk 8 gb.

mc4man: Just like above it doesn't see my drive at all when I run sudo lshw -C disk see below:
```
xinman@xinman-desktop:~$ sudo lshw -C disk
  *-cdrom
       description: DVD-RAM writer
       product: DVDRW LH-20A1L
       vendor: LITE-ON
       physical id: 0
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       logical name: /media/cdrom0
       version: BL02
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
          logical name: /media/cdrom0
          capabilities: partitioned partitioned:mac
          configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime state=mounted
  *-disk:0
       description: ATA Disk
       product: WDC WD800JD-00LS
       vendor: Western Digital
       physical id: 1
       bus info: scsi@2:0.0.0
       logical name: /dev/sda
       version: 06.0
       serial: WD-WMAM96945285
       size: 74GiB (80GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=704c1840
  *-disk:1
       description: ATA Disk
       product: ST31000340AS
       vendor: Seagate
       physical id: 0.0.0
       bus info: scsi@3:0.0.0
       logical name: /dev/sdb
       version: SD15
       serial: 5QJ0WVB9
       size: 931GiB (1TB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=49f69a22
```

That's why I said USB doesn't work, I really don't think it has anything to do with the drives.  But I'm open to suggestions.

---

### Post by mc4man on 2009-02-09
This probably won't help but once I had my usb go out, nothing would show.

what I did was shutdown, unplug the pc, push the power button and wait a bit, then reconnect the power. There's a 'protection' circuit on the usb that can in rare cases be tripped


edit : run lsusb

---

### Post by xinman on 2009-02-09
mc4man: sadly no it didn't help, output for lsusb:

```
xinman@xinman-desktop:~$ lsusb
Bus 006 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

```

Does that mean anything to you?

---

### Post by SunnyRabbiera on 2009-02-09
> **xinman said:**
> SunnyRabbiera: You must not have read my post, I said I have tried 5 devices and the mouse was a logitech.  Read the post fully before you blame anything.

well we have to count for everything, but on a personal note I blame hardware before blaming Ubuntu.
we live in a windows bent world you know.
You gave little detail on your hardware, usb support in ubuntu is very decent but what you plug into those USB ports is where the difference is made.
can you give us a full list of the devices you tried?
logs will only solve one half of the puzzle.

---

### Post by mc4man on 2009-02-09
Why don't you run a few more things and see what shows up

lsmod

lspci | grep USB

---

### Post by xinman on 2009-02-09
SunnyRabbiera: I agree we do live in a windows bent world (and it's a shame) but ubuntu is not perfect either, remember I've been using linux for about 8 years so please do not be a pusher.  If you refer back to post #1 you will see the list of devices that I tried.  If you are not going to read the entire post why do you bother chiming in with your 2 cents.

mc4man: I appreciate your help and I will post the output of these as soon as I get home from work.

---

### Post by Robster2 on 2009-02-09
There is something wrong with your computer hardware.

I am using a Ubuntu 8.04 64 on my laptop.  Ubuntu 8.04 32 on my desktop.  with a logitec trackball at the moment every mouse that I have plugged into either machine has worked. 

I have a Sandisk card reader down stairs on my desktop - works perfectly.

I have used Sandisk, Toshiba,and a host of noname Usb thumb drives -  All worked perfectly.  (although I have never been able to make a bootable thumb drive)

Sorry I could not be more help

Try the recovery option on the grub use the fix broken packages options when you get to the menu

---

### Post by SunnyRabbiera on 2009-02-09
> **xinman said:**
> SunnyRabbiera: I agree we do live in a windows bent world (and it's a shame) but ubuntu is not perfect either, remember I've been using linux for about 8 years so please do not be a pusher.  If you refer back to post #1 you will see the list of devices that I tried.  If you are not going to read the entire post why do you bother chiming in with your 2 cents.


I did, but just saying "my card reader wont work" doesnt help.
What brand of card reader?
what model?
Just saying generic doesnt give us much info, do you have any information on them?
Your sandisks, do you have a model number?
Your logitech mouse, do you have the model number?
I am only trying to gather more info, yes you said the types of devices you tried but you didnt list the model numbers.
I know certain models and brands wont work with linux, I am just gathering more info

---

### Post by xinman on 2009-02-09
Robster2: I tried the recover option and it did not work.  Thanks for chiming in.  Are you saying that it's my motherboard?  It works fine in Windows.

mc4man:  Here are the outputs of what you requested.

lsmod:
```
xinman@xinman-desktop:~$ lsmod
Module                  Size  Used by
binfmt_misc            12808  1
af_packet              23812  2
rfcomm                 41744  2
l2cap                  25728  13 rfcomm
bluetooth              61028  4 rfcomm,l2cap
vboxnetflt             91656  0
vboxdrv               117672  1 vboxnetflt
ppdev                  10372  0
ipv6                  267908  12
powernow_k8            16704  1
cpufreq_powersave       2688  0
cpufreq_userspace       5284  0
cpufreq_conservative     8712  0
cpufreq_ondemand        9740  1
cpufreq_stats           7104  0
freq_table              5536  3 powernow_k8,cpufreq_ondemand,cpufreq_stats
video                  19856  0
output                  4736  1 video
container               5632  0
sbs                    15112  0
sbshc                   7680  1 sbs
dock                   11280  0
battery                14212  0
iptable_filter          3840  0
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
ac                      6916  0
sbp2                   24072  0
lp                     12324  0
parport_pc             36260  1
parport                37832  3 ppdev,lp,parport_pc
serio_raw               7940  0
evdev                  13056  3
pcspkr                  4224  0
psmouse                40336  0
snd_seq_dummy           4868  0
snd_hda_intel         346136  4
k8temp                  6656  0
snd_pcm_oss            42144  0
snd_mixer_oss          17920  1 snd_pcm_oss
snd_seq_oss            35584  0
snd_seq_midi            9376  0
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
i2c_piix4               9612  0
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
i2c_core               24832  1 i2c_piix4
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
fglrx                1555468  27
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  19 snd_seq_dummy,snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_seq_oss,snd_pcm,snd_hwdep,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
ati_agp                 9996  0
button                  9232  0
agpgart                34760  2 fglrx,ati_agp
shpchp                 34452  0
pci_hotplug            30880  1 shpchp
ext3                  136840  1
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0
sd_mod                 30720  5
sr_mod                 17956  0
cdrom                  37408  1 sr_mod
atiixp                  5648  0 [permanent]
ide_core              113996  1 atiixp
ata_generic             8324  0
usb_storage            73792  0
libusual               19236  1 usb_storage
pata_atiixp             8960  0
floppy                 59588  0
ohci1394               33584  0
ieee1394               93752  2 sbp2,ohci1394
pata_acpi               8320  0
ahci                   28548  3
ehci_hcd               37900  0
ohci_hcd               26640  0
usbcore               146412  5 usb_storage,libusual,ehci_hcd,ohci_hcd
libata                159600  4 ata_generic,pata_atiixp,pata_acpi,ahci
scsi_mod              151436  6 sbp2,sg,sd_mod,sr_mod,usb_storage,libata
r8169                  33156  0
thermal                16796  0
processor              36488  2 powernow_k8,thermal
fan                     5636  0
fbcon                  42912  0
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  5

```

lspci | grep USB:
```
xinman@xinman-desktop:~$ lspci | grep USB
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
```

SunnyRabbiera:
I understand that you are trying to gather information, here it is.
Both card readers were tried with an A-Data 2GB card and a Kingston 1 GB card.

Lexar USB 2.0 Multi-Card Reader Part number RW022 (there is no model number)
Kodak Multi-Card Reader (No model number just has CE2A012)
Sandisk SDCZ6-8192RB 8GB Jump drive
Sandisk 4 GB Jump drive (model # has worn off)
Logitech MouseMan Wheel Model: M-BD53

---

### Post by SunnyRabbiera on 2009-02-09
Well personally looking at those devices I personally think its the USB interface that is at fault.
Both sandisk and logitech products have a decent track record with Ubuntu and linux in general, but the logitech mouse still might have issues if its one of those 5 button mice.
But if its a standard 3 button mouse,then its very strange it wont work.
The track record for those kinds of mice are good with linux, so there is the possibility its the USB interface.

---

### Post by LowSky on 2009-02-09
All those things should work, something must have gone wrong with the install. I makes no sense for none of it to not work. As for the 5 button comment by SunnyRabboira, I'm using two different 5 button mice Logitech mice and since the newest version of Xorg, they work out of the box, so you can't blame that.

Have you rebooted at all since the install?
What happens if you disconnect all other USB devices not including the mouse and keyboard.
Also have you flashed the BIOS? make sure that you set USB to PS/2 mode or backward compatable mode (depends on the BIOS) sometimes without this set USB wont work.

My other suggestion is to reinstall Ubuntu, with a new download or use the newer version 8.10

---

### Post by kansasnoob on 2009-02-09
Try just installing pmount from synaptic or:

```
sudo apt-get install pmount
```

A brief description from synaptic:

> mount removable devices as normal user
pmount is a wrapper around the standard mount program which permits normal
users to mount removable devices without a matching /etc/fstab entry. This
provides a robust basis for automounting frameworks like GNOME's Utopia
project and confines the amount of code that runs as root to a minimum.

This package also contains a wrapper "pmount-hal" which reads some
information like device labels and mount options from hal and passes
them to pmount. Install the package "hal" if you want to use this
feature.

If a LUKS capable cryptsetup package is installed, pmount is able to
transparently mount encrypted volumes.

---

### Post by neu2buntu on 2009-02-09
perhaps try installing "usbmount" and "gnome-volume-manager" open terminal and type

```
sudo apt-get install usbmount gnome-volume-manager
```   this may help with some pen drives etc

---

### Post by louieb on 2009-02-09
> **LowSky said:**
>  make sure that you set USB to PS/2 mode or backward compatable mode (depends on the BIOS) sometimes without this set USB wont work.


Just about to suggest checking the BIOS setup to see if has a legacy USB mode. :P

---

### Post by gsocker on 2009-02-09
Let's take a look a the kernel log and make sure everthing gets detected. Please run dmesg and post the output. This will print the current kernel message buffer. 
Also post the contents of /proc/interrupts. 
Something funny is going on; your lsusb output **not** be all zeros for IDs.
lsusb output should look more like this:
```

Bus 001 Device 009: ID 046d:c714 Logitech, Inc.
Bus 001 Device 008: ID 046d:c713 Logitech, Inc.
Bus 001 Device 007: ID 046d:0b04 Logitech, Inc.
Bus 001 Device 006: ID 056a:00b1 Wacom Co., Ltd
Bus 001 Device 004: ID 0424:2504 Standard Microsystems Corp. USB 2.0 Hub
Bus 001 Device 001: ID 1d6b:0002
Bus 002 Device 004: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 002 Device 003: ID 051d:0002 American Power Conversion Uninterruptible Power Supply
Bus 002 Device 002: ID 0e97:090b Fingerworks, Inc.
Bus 002 Device 001: ID 1d6b:0001

```

---

### Post by xinman on 2009-02-10
SunnyRabbiera:  Well I must say these devices work on one of my other boxes that is running Ubuntu 5.10 and another one that is running 7.04.  Your suggesting that it is the usb port.  It does work in Windows (I know I know...)  

I have checked the BIOS and I've tried pmount and usbmount.

I did notice that when I had one of the card readers and card plugged in while I booted it did mount the card and I could access the pictures on it.  But that was the only time that it worked and it was very slow copying pictures from it.  So there is hope!

Here is the output of dmesg:
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-23-generic (buildd@vernadsky) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Mon Jan 26 00:13:11 UTC 2009 (Ubuntu 2.6.24-23.48-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cfee0000 (usable)
[    0.000000]  BIOS-e820: 00000000cfee0000 - 00000000cfee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cfee3000 - 00000000cfef0000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cfef0000 - 00000000cff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000130000000 (usable)
[    0.000000] Warning only 4GB will be used.
[    0.000000] Use a HIGHMEM64G enabled kernel.
[    0.000000] 3200MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f52b0
[    0.000000] Entering add_active_range(0, 0, 1048576) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->  1048576
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->  1048576
[    0.000000] On node 0 totalpages: 1048576
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 6400 pages used for memmap
[    0.000000]   HighMem zone: 812800 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F6C70 checksum 0
[    0.000000] ACPI: RSDP 000F6C70, 0014 (r0 GBT   )
[    0.000000] ACPI: RSDT CFEE3000, 0038 (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
[    0.000000] ACPI: FACP CFEE3040, 0074 (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
[    0.000000] ACPI: DSDT CFEE30C0, 4162 (r1 GBT    GBTUACPI     1000 MSFT  3000000)
[    0.000000] ACPI: FACS CFEE0000, 0040
[    0.000000] ACPI: SSDT CFEE7300, 02CC (r1 PTLTD  POWERNOW        1  LTP        1)
[    0.000000] ACPI: HPET CFEE7600, 0038 (r1 GBT    GBTUACPI 42302E31 GBTU       98)
[    0.000000] ACPI: MCFG CFEE7640, 003C (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
[    0.000000] ACPI: APIC CFEE7240, 0084 (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
[    0.000000] ATI board detected. Disabling timer routing over 8254.
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:11 APIC version 16
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:11 APIC version 16
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x10b9a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at d0000000 (gap: cff00000:10100000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1040384
[    0.000000] Kernel command line: root=UUID=c0d16d18-e55c-4360-9af5-cc69434d5db7 ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2712.442 MHz processor.
[   31.880508] Console: colour VGA+ 80x25
[   31.880510] console [tty0] enabled
[   31.880748] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   31.881007] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   32.017991] Memory: 3360360k/4194304k available (2179k kernel code, 45112k reserved, 1008k data, 368k init, 2489216k highmem)
[   32.017997] virtual kernel memory layout:
[   32.017997]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   32.017998]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   32.017999]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   32.018000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   32.018001]       .init : 0xc0423000 - 0xc047f000   ( 368 kB)
[   32.018001]       .data : 0xc0320c08 - 0xc041cdc4   (1008 kB)
[   32.018002]       .text : 0xc0100000 - 0xc0320c08   (2179 kB)
[   32.018004] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   32.018028] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   32.018136] hpet clockevent registered
[   32.098193] Calibrating delay using timer specific routine.. 5544.19 BogoMIPS (lpj=11088384)
[   32.098208] Security Framework initialized
[   32.098212] SELinux:  Disabled at boot.
[   32.098222] AppArmor: AppArmor initialized
[   32.098224] Failure registering capabilities with primary security module.
[   32.098230] Mount-cache hash table entries: 512
[   32.098308] Initializing cgroup subsys ns
[   32.098310] Initializing cgroup subsys cpuacct
[   32.098317] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000011f 00000000
[   32.098323] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   32.098325] CPU: L2 Cache: 512K (64 bytes/line)
[   32.098326] CPU 0(2) -> Core 0
[   32.098328] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00020410 00002001 00000000 0000011f 00000000
[   32.098334] Compat vDSO mapped to ffffe000.
[   32.098341] Checking 'hlt' instruction... OK.
[   32.114360] SMP alternatives: switching to UP code
[   32.115175] Early unpacking initramfs... done
[   32.350054] ACPI: Core revision 20070126
[   32.350095] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   32.362455] CPU0: AMD Athlon(tm) 64 X2 Dual Core Processor 5200+ stepping 02
[   32.362469] SMP alternatives: switching to SMP code
[   32.362772] Booting processor 1/1 eip 3000
[   32.373352] Initializing CPU#1
[   32.453912] Calibrating delay using timer specific routine.. 5424.69 BogoMIPS (lpj=10849385)
[   32.453917] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000011f 00000000
[   32.453921] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   32.453923] CPU: L2 Cache: 512K (64 bytes/line)
[   32.453924] CPU 1(2) -> Core 1
[   32.453925] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00020410 00002001 00000000 0000011f 00000000
[   32.453630] CPU1: AMD Athlon(tm) 64 X2 Dual Core Processor 5200+ stepping 02
[   32.453642] Total of 2 processors activated (10968.88 BogoMIPS).
[   32.453947] ENABLING IO-APIC IRQs
[   32.454169] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   32.601386] Brought up 2 CPUs
[   32.601435] CPU0 attaching sched-domain:
[   32.601436]  domain 0: span 03
[   32.601438]   groups: 01 02
[   32.601440] CPU1 attaching sched-domain:
[   32.601441]  domain 0: span 03
[   32.601442]   groups: 02 01
[   32.601582] net_namespace: 64 bytes
[   32.601586] Booting paravirtualized kernel on bare hardware
[   32.601900] Time: 23:11:29  Date: 02/09/09
[   32.601917] NET: Registered protocol family 16
[   32.602037] EISA bus registered
[   32.602040] ACPI: bus type pci registered
[   32.602901] PCI: PCI BIOS revision 3.00 entry at 0xfb4f0, last bus=3
[   32.602902] PCI: Using configuration type 1
[   32.602905] Setting up standard PCI resources
[   32.605722] ACPI: EC: Look up EC in DSDT
[   32.608362] ACPI: Interpreter enabled
[   32.608363] ACPI: (supports S0 S3 S4 S5)
[   32.608372] ACPI: Using IOAPIC for interrupt routing
[   32.611290] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   32.611471] pci 0000:00:12.0: set SATA to AHCI mode
[   32.612547] PCI: Transparent bridge - 0000:00:14.4
[   32.612571] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   32.612719] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[   32.624421] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   32.624486] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   32.624550] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   32.624613] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   32.624677] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   32.624741] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   32.624804] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   32.624868] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   32.624947] Linux Plug and Play Support v0.97 (c) Adam Belay
[   32.624968] pnp: PnP ACPI init
[   32.624973] ACPI: bus type pnp registered
[   32.626904] pnp: PnP ACPI: found 15 devices
[   32.626905] ACPI: ACPI bus type pnp unregistered
[   32.626908] PnPBIOS: Disabled by ACPI PNP
[   32.627043] PCI: Using ACPI for IRQ routing
[   32.627045] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   32.627052] PCI: Cannot allocate resource region 3 of device 0000:00:00.0
[   32.705171] NET: Registered protocol family 8
[   32.705172] NET: Registered protocol family 20
[   32.705197] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[   32.705200] hpet0: 4 32-bit timers, 14318180 Hz
[   32.706231] AppArmor: AppArmor Filesystem Enabled
[   32.709161] Time: hpet clocksource has been installed.
[   32.709173] Switched to high resolution mode on CPU 0
[   32.709644] Switched to high resolution mode on CPU 1
[   32.717144] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[   32.717146] system 00:01: ioport range 0x220-0x225 has been reserved
[   32.717148] system 00:01: ioport range 0x290-0x294 has been reserved
[   32.717152] system 00:02: ioport range 0x4100-0x411f has been reserved
[   32.717154] system 00:02: ioport range 0x228-0x22f has been reserved
[   32.717155] system 00:02: ioport range 0x40b-0x40b has been reserved
[   32.717157] system 00:02: ioport range 0x4d6-0x4d6 has been reserved
[   32.717159] system 00:02: ioport range 0xc00-0xc01 has been reserved
[   32.717161] system 00:02: ioport range 0xc14-0xc14 has been reserved
[   32.717162] system 00:02: ioport range 0xc50-0xc52 has been reserved
[   32.717164] system 00:02: ioport range 0xc6c-0xc6d has been reserved
[   32.717166] system 00:02: ioport range 0xc6f-0xc6f has been reserved
[   32.717168] system 00:02: ioport range 0xcd0-0xcd1 has been reserved
[   32.717170] system 00:02: ioport range 0xcd2-0xcd3 has been reserved
[   32.717172] system 00:02: ioport range 0xcd4-0xcdf has been reserved
[   32.717173] system 00:02: ioport range 0x4000-0x40fe has been reserved
[   32.717175] system 00:02: ioport range 0x4210-0x4217 has been reserved
[   32.717177] system 00:02: ioport range 0xb00-0xb1f could not be reserved
[   32.717179] system 00:02: ioport range 0x238-0x23f has been reserved
[   32.717186] system 00:0d: iomem range 0xe0000000-0xefffffff could not be reserved
[   32.717190] system 00:0e: iomem range 0xcf800-0xcffff has been reserved
[   32.717192] system 00:0e: iomem range 0xf0000-0xf7fff could not be reserved
[   32.717194] system 00:0e: iomem range 0xf8000-0xfbfff could not be reserved
[   32.717196] system 00:0e: iomem range 0xfc000-0xfffff could not be reserved
[   32.717198] system 00:0e: iomem range 0xcfee0000-0xcfefffff could not be reserved
[   32.717200] system 00:0e: iomem range 0xffff0000-0xffffffff could not be reserved
[   32.717202] system 00:0e: iomem range 0x0-0x9ffff could not be reserved
[   32.717203] system 00:0e: iomem range 0x100000-0xcfedffff could not be reserved
[   32.717205] system 00:0e: iomem range 0xfec00000-0xfec00fff could not be reserved
[   32.717207] system 00:0e: iomem range 0xfee00000-0xfee00fff could not be reserved
[   32.717209] system 00:0e: iomem range 0xfff80000-0xfffeffff could not be reserved
[   32.747448] PCI: Bridge: 0000:00:02.0
[   32.747450]   IO window: d000-dfff
[   32.747453]   MEM window: fde00000-fdefffff
[   32.747455]   PREFETCH window: d0000000-dfffffff
[   32.747458] PCI: Bridge: 0000:00:0a.0
[   32.747459]   IO window: e000-efff
[   32.747462]   MEM window: fdd00000-fddfffff
[   32.747464]   PREFETCH window: fdf00000-fdffffff
[   32.747467] PCI: Bridge: 0000:00:14.4
[   32.747469]   IO window: c000-cfff
[   32.747474]   MEM window: fdc00000-fdcfffff
[   32.747478]   PREFETCH window: fdb00000-fdbfffff
[   32.747490] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   32.747497] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[   32.747511] NET: Registered protocol family 2
[   32.785074] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   32.785269] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   32.785790] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   32.786043] TCP: Hash tables configured (established 131072 bind 65536)
[   32.786045] TCP reno registered
[   32.797106] checking if image is initramfs... it is
[   33.232250] Freeing initrd memory: 7315k freed
[   33.233235] audit: initializing netlink socket (disabled)
[   33.233245] audit(1234221089.104:1): initialized
[   33.233412] highmem bounce pool size: 64 pages
[   33.234710] VFS: Disk quotas dquot_6.5.1
[   33.234758] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   33.234837] io scheduler noop registered
[   33.234839] io scheduler anticipatory registered
[   33.234840] io scheduler deadline registered
[   33.234847] io scheduler cfq registered (default)
[   34.087556] 0000:00:13.2 OHCI: BIOS handoff failed (BIOS bug ?) 00000184
[   34.143503] Boot video device is 0000:01:00.0
[   34.143580] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   34.143604] assign_interrupt_mode Found MSI capability
[   34.143627] Allocate Port Service[0000:00:02.0:pcie00]
[   34.143682] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[   34.143704] assign_interrupt_mode Found MSI capability
[   34.143725] Allocate Port Service[0000:00:0a.0:pcie00]
[   34.143890] isapnp: Scanning for PnP cards...
[   34.497322] isapnp: No Plug & Play device found
[   34.517026] Real Time Clock Driver v1.12ac
[   34.517138] hpet_resources: 0xfed00000 is busy
[   34.517157] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   34.517285] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   34.517758] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   34.518319] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   34.518364] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   34.518436] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   34.518773] serio: i8042 KBD port at 0x60,0x64 irq 1
[   34.518777] serio: i8042 AUX port at 0x60,0x64 irq 12
[   34.535949] mice: PS/2 mouse device common for all mice
[   34.536034] EISA: Probing bus 0 at eisa.0
[   34.536052] Cannot allocate resource for EISA slot 4
[   34.536068] EISA: Detected 0 cards.
[   34.536070] cpuidle: using governor ladder
[   34.536072] cpuidle: using governor menu
[   34.536128] NET: Registered protocol family 1
[   34.536144] Using IPI No-Shortcut mode
[   34.536167] registered taskstats version 1
[   34.536240]   Magic number: 13:706:200
[   34.536267]   hash matches device ttypf
[   34.536327] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   34.536329] EDD information not available.
[   34.536489] Freeing unused kernel memory: 368k freed
[   34.536508] Write protecting the kernel read-only data: 806k
[   34.581722] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   35.695173] fuse init (API version 7.9)
[   35.708107] ACPI Exception (processor_core-0822): AE_NOT_FOUND, Processor Device is not present [20070126]
[   35.708115] ACPI Exception (processor_core-0822): AE_NOT_FOUND, Processor Device is not present [20070126]
[   35.828439] r8169 Gigabit Ethernet driver 2.2LK loaded
[   35.828466] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 18 (level, low) -> IRQ 16
[   35.828482] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   35.828742] eth0: RTL8168b/8111b at 0xf8848000, 00:1d:7d:d7:df:d3, XID 38000000 IRQ 221
[   35.847658] usbcore: registered new interface driver usbfs
[   35.847674] usbcore: registered new interface driver hub
[   35.848632] SCSI subsystem initialized
[   35.848515] usbcore: registered new device driver usb
[   35.861074] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   35.861114] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 16 (level, low) -> IRQ 17
[   35.861125] ohci_hcd 0000:00:13.0: OHCI Host Controller
[   35.861321] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[   35.861338] ohci_hcd 0000:00:13.0: irq 17, io mem 0xfe02e000
[   35.868577] libata version 3.00 loaded.
[   35.920619] usb usb1: configuration #1 chosen from 1 choice
[   35.920637] hub 1-0:1.0: USB hub found
[   35.920646] hub 1-0:1.0: 2 ports detected
[   36.024383] ACPI: PCI Interrupt 0000:00:13.1[B] -> GSI 17 (level, low) -> IRQ 18
[   36.024395] ohci_hcd 0000:00:13.1: OHCI Host Controller
[   36.024412] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[   36.024428] ohci_hcd 0000:00:13.1: irq 18, io mem 0xfe02d000
[   36.034724] Floppy drive(s): fd0 is 1.44M
[   36.055664] FDC 0 is a post-1991 82077
[   36.084390] usb usb2: configuration #1 chosen from 1 choice
[   36.084406] hub 2-0:1.0: USB hub found
[   36.084414] hub 2-0:1.0: 2 ports detected
[   36.188131] ACPI: PCI Interrupt 0000:00:13.2[C] -> GSI 18 (level, low) -> IRQ 16
[   36.188144] ohci_hcd 0000:00:13.2: OHCI Host Controller
[   36.188158] ohci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[   36.188175] ohci_hcd 0000:00:13.2: irq 16, io mem 0xfe02c000
[   36.248108] usb usb3: configuration #1 chosen from 1 choice
[   36.248123] hub 3-0:1.0: USB hub found
[   36.248129] hub 3-0:1.0: 2 ports detected
[   36.351898] ACPI: PCI Interrupt 0000:00:13.3[B] -> GSI 17 (level, low) -> IRQ 18
[   36.351912] ohci_hcd 0000:00:13.3: OHCI Host Controller
[   36.351928] ohci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 4
[   36.351940] ohci_hcd 0000:00:13.3: irq 18, io mem 0xfe02b000
[   36.415866] usb usb4: configuration #1 chosen from 1 choice
[   36.415881] hub 4-0:1.0: USB hub found
[   36.415888] hub 4-0:1.0: 2 ports detected
[   36.499608] usb 2-1: new full speed USB device using ohci_hcd and address 2
[   36.515628] ACPI: PCI Interrupt 0000:00:13.4[C] -> GSI 18 (level, low) -> IRQ 16
[   36.515637] ohci_hcd 0000:00:13.4: OHCI Host Controller
[   36.515651] ohci_hcd 0000:00:13.4: new USB bus registered, assigned bus number 5
[   36.515661] ohci_hcd 0000:00:13.4: irq 16, io mem 0xfe02a000
[   36.575620] usb usb5: configuration #1 chosen from 1 choice
[   36.575634] hub 5-0:1.0: USB hub found
[   36.575640] hub 5-0:1.0: 2 ports detected
[   36.679918] ahci 0000:00:12.0: version 3.0
[   36.679949] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 22 (level, low) -> IRQ 19
[   36.679968] ahci 0000:00:12.0: controller can't do 64bit DMA, forcing 32bit
[   36.679970] ahci 0000:00:12.0: controller can't do PMP, turning off CAP_PMP
[   36.723849] usb 2-1: configuration #1 chosen from 1 choice
[   37.035238] usb 5-1: new full speed USB device using ohci_hcd and address 2
[   37.251052] usb 5-1: configuration #1 chosen from 1 choice
[   37.252696] usbcore: registered new interface driver libusual
[   37.261943] Initializing USB Mass Storage driver...
[   37.262281] scsi0 : SCSI emulation for USB Mass Storage devices
[   37.262326] usb-storage: device found at 2
[   37.262328] usb-storage: waiting for device to settle before scanning
[   37.262347] scsi1 : SCSI emulation for USB Mass Storage devices
[   37.262378] usbcore: registered new interface driver usb-storage
[   37.262380] USB Mass Storage support registered.
[   37.262447] usb-storage: device found at 2
[   37.262448] usb-storage: waiting for device to settle before scanning
[   37.682327] ahci 0000:00:12.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[   37.682331] ahci 0000:00:12.0: flags: ncq sntf ilck pm led clo pio slum part 
[   37.682587] scsi2 : ahci
[   37.682768] scsi3 : ahci
[   37.682854] scsi4 : ahci
[   37.682937] scsi5 : ahci
[   37.682988] ata1: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f100 irq 19
[   37.682991] ata2: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f180 irq 19
[   37.682994] ata3: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f200 irq 19
[   37.682996] ata4: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f280 irq 19
[   37.993429] ata1: SATA link down (SStatus 0 SControl 300)
[   38.468732] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   38.637853] ata2.00: ATAPI: LITE-ON DVDRW LH-20A1L, BL02, max UDMA/100, ATAPI AN
[   38.805677] ata2.00: configured for UDMA/100
[   39.279542] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   39.280387] ata3.00: ATA-7: WDC WD800JD-00LSA0, 06.01D06, max UDMA/133
[   39.280389] ata3.00: 156301488 sectors, multi 16: LBA48 
[   39.280896] ata3.00: configured for UDMA/133
[   39.754844] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   39.758179] ata4.00: HPA unlocked: 1953523055 -> 1953525168, native 1953525168
[   39.758182] ata4.00: ATA-8: ST31000340AS, SD15, max UDMA/133
[   39.758184] ata4.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[   39.760005] ata4.00: configured for UDMA/133
[   39.761126] scsi 3:0:0:0: CD-ROM            LITE-ON  DVDRW LH-20A1L   BL02 PQ: 0 ANSI: 5
[   39.761399] scsi 4:0:0:0: Direct-Access     ATA      WDC WD800JD-00LS 06.0 PQ: 0 ANSI: 5
[   39.761600] scsi 5:0:0:0: Direct-Access     ATA      ST31000340AS     SD15 PQ: 0 ANSI: 5
[   39.761264] ACPI: PCI Interrupt 0000:00:13.5[D] -> GSI 19 (level, low) -> IRQ 20
[   39.761277] ehci_hcd 0000:00:13.5: EHCI Host Controller
[   39.761300] ehci_hcd 0000:00:13.5: new USB bus registered, assigned bus number 6
[   39.761333] ehci_hcd 0000:00:13.5: debug port 1
[   39.761348] ehci_hcd 0000:00:13.5: irq 20, io mem 0xfe029000
[   39.761864] usb 2-1: USB disconnect, address 2

[   39.770811] ehci_hcd 0000:00:13.5: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   39.770881] usb usb6: configuration #1 chosen from 1 choice
[   39.770897] hub 6-0:1.0: USB hub found
[   39.770900] hub 6-0:1.0: 10 ports detected
[   39.874784] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 17
[   39.874822] ACPI: PCI interrupt for device 0000:00:14.1 disabled
[   39.875225] ACPI: PCI Interrupt 0000:03:0e.0[A] -> GSI 22 (level, low) -> IRQ 19
[   39.888080] usb 5-1: USB disconnect, address 2
[   39.925960] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[fdcff000-fdcff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   39.927776] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 17
[   39.927991] scsi6 : pata_atiixp
[   39.928024] scsi7 : pata_atiixp
[   39.928558] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf900 irq 14
[   39.928560] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf908 irq 15
[   39.929318] Driver 'sd' needs updating - please use bus_type methods
[   39.930386] sd 4:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   39.929986] Driver 'sr' needs updating - please use bus_type methods
[   39.930405] sd 4:0:0:0: [sda] Write Protect is off
[   39.930407] sd 4:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   39.930419] sd 4:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   39.930456] sd 4:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   39.930461] sd 4:0:0:0: [sda] Write Protect is off
[   39.930463] sd 4:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   39.930472] sd 4:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   39.930475]  sda:sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[   39.938212] Uniform CD-ROM driver Revision: 3.20
[   39.938249] sr 3:0:0:0: Attached scsi CD-ROM sr0
[   39.940200]  sda1 sda2 < sda5 >
[   39.966648] sd 4:0:0:0: [sda] Attached SCSI disk
[   39.966686] sd 5:0:0:0: [sdb] 1953525168 512-byte hardware sectors (1000205 MB)
[   39.966694] sd 5:0:0:0: [sdb] Write Protect is off
[   39.966695] sd 5:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   39.966706] sd 5:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   39.966733] sd 5:0:0:0: [sdb] 1953525168 512-byte hardware sectors (1000205 MB)
[   39.966738] sd 5:0:0:0: [sdb] Write Protect is off
[   39.966740] sd 5:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   39.966749] sd 5:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   39.966751]  sdb: sdb1
[   39.989396] sd 5:0:0:0: [sdb] Attached SCSI disk
[   39.991958] sr 3:0:0:0: Attached scsi generic sg0 type 5
[   39.991971] sd 4:0:0:0: Attached scsi generic sg1 type 0
[   39.991983] sd 5:0:0:0: Attached scsi generic sg2 type 0
[   40.243712] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   40.243717] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   40.304813] Attempting manual resume
[   40.304816] swsusp: Resume From Partition 8:5
[   40.304817] PM: Checking swsusp image.
[   40.304920] PM: Resume from disk failed.
[   40.341955] kjournald starting.  Commit interval 5 seconds
[   40.342373] EXT3-fs: mounted filesystem with ordered data mode.
[   40.498160] usb 6-9: new high speed USB device using ehci_hcd and address 3
[   40.635599] usb 6-9: configuration #1 chosen from 1 choice
[   40.636234] scsi8 : SCSI emulation for USB Mass Storage devices
[   40.635868] usb-storage: device found at 3
[   40.635871] usb-storage: waiting for device to settle before scanning
[   40.945509] usb 2-1: new full speed USB device using ohci_hcd and address 3
[   41.181579] usb 2-1: configuration #1 chosen from 1 choice
[   41.183578] scsi9 : SCSI emulation for USB Mass Storage devices
[   41.183218] usb-storage: device found at 3
[   41.183220] usb-storage: waiting for device to settle before scanning
[   41.204775] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00db72e600001d7d]
[   45.637195] usb-storage: device scan complete
[   45.638444] scsi 8:0:0:0: Direct-Access     Generic  STORAGE DEVICE   9144 PQ: 0 ANSI: 0
[   45.639684] scsi 8:0:0:1: Direct-Access     Generic  STORAGE DEVICE   9144 PQ: 0 ANSI: 0
[   45.640930] scsi 8:0:0:2: Direct-Access     Generic  STORAGE DEVICE   9144 PQ: 0 ANSI: 0
[   45.642179] scsi 8:0:0:3: Direct-Access     Generic  STORAGE DEVICE   9144 PQ: 0 ANSI: 0
[   45.643457] sd 8:0:0:0: [sdc] Attached SCSI removable disk
[   45.643483] sd 8:0:0:0: Attached scsi generic sg3 type 0
[   45.645124] sd 8:0:0:1: [sdd] Attached SCSI removable disk
[   45.645154] sd 8:0:0:1: Attached scsi generic sg4 type 0
[   45.646343] sd 8:0:0:2: [sde] Attached SCSI removable disk
[   45.646367] sd 8:0:0:2: Attached scsi generic sg5 type 0
[   45.647590] sd 8:0:0:3: [sdf] Attached SCSI removable disk
[   45.647609] sd 8:0:0:3: Attached scsi generic sg6 type 0
[   45.725988] Linux agpgart interface v0.102
[   45.934420] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   45.948212] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   45.966301] input: Power Button (FF) as /devices/virtual/input/input2
[   45.991182] ACPI: Power Button (FF) [PWRF]
[   45.991239] input: Power Button (CM) as /devices/virtual/input/input3
[   46.019124] ACPI: Power Button (CM) [PWRB]
[   46.214427] usb-storage: device scan complete
[   46.219077] scsi 9:0:0:0: Direct-Access     Kodak    CF/SD/MMC/SM     0108 PQ: 0 ANSI: 0 CCS
[   46.225046] scsi 9:0:0:1: Direct-Access     Kodak    CF/SD/MMC/SM     0108 PQ: 0 ANSI: 0 CCS
[   46.231037] scsi 9:0:0:2: Direct-Access     Kodak    CF/SD/MMC/SM     0108 PQ: 0 ANSI: 0 CCS
[   46.241084] sd 9:0:0:0: [sdg] Attached SCSI removable disk
[   46.241117] sd 9:0:0:0: Attached scsi generic sg7 type 0
[   46.251062] sd 9:0:0:1: [sdh] Attached SCSI removable disk
[   46.251097] sd 9:0:0:1: Attached scsi generic sg8 type 0
[   46.317670] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   46.332423] [fglrx] Maximum main memory to use for locked dma buffers: 3139 MBytes.
[   46.332448] [fglrx] ASYNCIO init succeed!
[   46.332668] [fglrx] PAT is enabled successfully!
[   46.332687] [fglrx] module loaded - fglrx 8.47.3 [Feb 25 2008] on minor 0
[   46.391520] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[   46.483747] sd 9:0:0:2: [sdi] Attached SCSI removable disk
[   46.483782] sd 9:0:0:2: Attached scsi generic sg9 type 0
[   46.682106] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 17
[   46.739924] ACPI: PCI Interrupt 0000:01:00.1[B] -> GSI 18 (level, low) -> IRQ 16
[   46.739941] PCI: Setting latency timer of device 0000:01:00.1 to 64
[   46.924861] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   47.070084] irq 20: nobody cared (try booting with the "irqpoll" option)
[   47.070089] Pid: 3379, comm: modprobe Tainted: P        2.6.24-23-generic #1
[   47.070097]  [<c0169214>] __report_bad_irq+0x24/0x80
[   47.070104]  [<c01694eb>] note_interrupt+0x27b/0x2c0
[   47.070108]  [<f88b8ccb>] usb_hcd_irq+0x2b/0x60 [usbcore]
[   47.070124]  [<c0168710>] handle_IRQ_event+0x30/0x60
[   47.070127]  [<c0169ea6>] handle_fasteoi_irq+0x86/0xe0
[   47.070130]  [<c0106f0b>] do_IRQ+0x3b/0x70
[   47.070133]  [<c01929a1>] sys_read+0x41/0x70
[   47.070137]  [<c0105403>] common_interrupt+0x23/0x30
[   47.070143]  =======================
[   47.070144] handlers:
[   47.070145] [<f88b8ca0>] (usb_hcd_irq+0x0/0x60 [usbcore])
[   47.070157] Disabling IRQ #20
[   47.756556] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:593: hda_intel: azx_get_response timeout, switching to polling mode: last cmd=0x000f0000
[   48.030039] input: ImExPS/2 Generic Explorer Mouse as /devices/platform/i8042/serio1/input/input5
[   48.055885] sd 9:0:0:2: [sdi] 3948544 512-byte hardware sectors (2022 MB)
[   48.061876] sd 9:0:0:2: [sdi] Write Protect is off
[   48.061880] sd 9:0:0:2: [sdi] Mode Sense: 43 00 00 00
[   48.061882] sd 9:0:0:2: [sdi] Assuming drive cache: write through
[   48.081240] parport_pc 00:0a: reported by Plug and Play ACPI
[   48.081307] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   48.083725] sd 9:0:0:2: [sdi] 3948544 512-byte hardware sectors (2022 MB)
[   48.087832] sd 9:0:0:2: [sdi] Write Protect is off
[   48.087836] sd 9:0:0:2: [sdi] Mode Sense: 43 00 00 00
[   48.087838] sd 9:0:0:2: [sdi] Assuming drive cache: write through
[   48.087842]  sdi: sdi1
[   78.015389] usb 6-9: reset high speed USB device using ehci_hcd and address 3
[   93.086110] usb 6-9: USB disconnect, address 3
[   93.085711] sd 8:0:0:1: Device offlined - not ready after error recovery
[   93.086837] scsi 8:0:0:3: rejecting I/O to dead device
[   93.086845] scsi 8:0:0:3: rejecting I/O to dead device
[   93.086848] scsi 8:0:0:3: rejecting I/O to dead device
[   93.086850] scsi 8:0:0:3: rejecting I/O to dead device
[   93.086852] scsi 8:0:0:3: [sdf] READ CAPACITY failed
[   93.086854] scsi 8:0:0:3: [sdf] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[   93.086856] scsi 8:0:0:3: [sdf] Sense not available.
[   93.086859] scsi 8:0:0:3: rejecting I/O to dead device
[   93.086862] scsi 8:0:0:3: [sdf] Write Protect is off
[   93.086863] scsi 8:0:0:3: [sdf] Mode Sense: 00 00 00 00
[   93.086865] scsi 8:0:0:3: [sdf] Assuming drive cache: write through
[   93.086868] scsi 8:0:0:3: rejecting I/O to dead device
[   93.086872] scsi 8:0:0:3: rejecting I/O to dead device
[   93.086875] scsi 8:0:0:3: rejecting I/O to dead device
[   93.086877] scsi 8:0:0:3: rejecting I/O to dead device
[   93.086880] scsi 8:0:0:3: rejecting I/O to dead device
[   93.086882] scsi 8:0:0:3: [sdf] READ CAPACITY failed
[   93.086883] scsi 8:0:0:3: [sdf] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[   93.086885] scsi 8:0:0:3: [sdf] Sense not available.
[   93.086887] scsi 8:0:0:3: rejecting I/O to dead device
[   93.086889] scsi 8:0:0:3: [sdf] Write Protect is off
[   93.086890] scsi 8:0:0:3: [sdf] Mode Sense: 00 00 00 00
[   93.086892] scsi 8:0:0:3: [sdf] Assuming drive cache: write through
[   93.086566] scsi 8:0:0:0: rejecting I/O to dead device
[   93.086576] scsi 8:0:0:0: rejecting I/O to dead device
[   93.086579] scsi 8:0:0:0: rejecting I/O to dead device
[   93.086582] scsi 8:0:0:0: rejecting I/O to dead device
[   93.086584] scsi 8:0:0:0: [sdc] READ CAPACITY failed
[   93.086586] scsi 8:0:0:0: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[   93.086589] scsi 8:0:0:0: [sdc] Sense not available.
[   93.086592] scsi 8:0:0:0: rejecting I/O to dead device
[   93.086594] scsi 8:0:0:0: [sdc] Write Protect is off
[   93.086596] scsi 8:0:0:0: [sdc] Mode Sense: 00 00 00 00
[   93.086597] scsi 8:0:0:0: [sdc] Assuming drive cache: write through
[   93.086600] scsi 8:0:0:0: rejecting I/O to dead device
[   93.086606] scsi 8:0:0:0: rejecting I/O to dead device
[   93.086608] scsi 8:0:0:0: rejecting I/O to dead device
[   93.086611] scsi 8:0:0:0: rejecting I/O to dead device
[   93.086614] scsi 8:0:0:0: rejecting I/O to dead device
[   93.086616] scsi 8:0:0:0: [sdc] READ CAPACITY failed
[   93.086617] scsi 8:0:0:0: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[   93.086619] scsi 8:0:0:0: [sdc] Sense not available.
[   93.086621] scsi 8:0:0:0: rejecting I/O to dead device
[   93.086623] scsi 8:0:0:0: [sdc] Write Protect is off
[   93.086625] scsi 8:0:0:0: [sdc] Mode Sense: 00 00 00 00
[   93.086626] scsi 8:0:0:0: [sdc] Assuming drive cache: write through
[   93.087600] scsi 8:0:0:3: rejecting I/O to dead device
[   93.087775] scsi 8:0:0:2: rejecting I/O to dead device
[   93.087785] scsi 8:0:0:2: rejecting I/O to dead device
[   93.087788] scsi 8:0:0:2: rejecting I/O to dead device
[   93.087791] scsi 8:0:0:2: rejecting I/O to dead device
[   93.087793] scsi 8:0:0:2: [sde] READ CAPACITY failed
[   93.087794] scsi 8:0:0:2: [sde] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[   93.087797] scsi 8:0:0:2: [sde] Sense not available.
[   93.087800] scsi 8:0:0:2: rejecting I/O to dead device
[   93.087802] scsi 8:0:0:2: [sde] Write Protect is off
[   93.087804] scsi 8:0:0:2: [sde] Mode Sense: 00 00 00 00
[   93.087805] scsi 8:0:0:2: [sde] Assuming drive cache: write through
[   93.087808] scsi 8:0:0:2: rejecting I/O to dead device
[   93.087813] scsi 8:0:0:2: rejecting I/O to dead device
[   93.087816] scsi 8:0:0:2: rejecting I/O to dead device
[   93.087818] scsi 8:0:0:2: rejecting I/O to dead device
[   93.087821] scsi 8:0:0:2: rejecting I/O to dead device
[   93.087823] scsi 8:0:0:2: [sde] READ CAPACITY failed
[   93.087824] scsi 8:0:0:2: [sde] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[   93.087826] scsi 8:0:0:2: [sde] Sense not available.
[   93.087828] scsi 8:0:0:2: rejecting I/O to dead device
[   93.087830] scsi 8:0:0:2: [sde] Write Protect is off
[   93.087831] scsi 8:0:0:2: [sde] Mode Sense: 00 00 00 00
[   93.087833] scsi 8:0:0:2: [sde] Assuming drive cache: write through
[   93.088331] scsi 8:0:0:2: rejecting I/O to dead device
[   93.088860] scsi 8:0:0:0: rejecting I/O to dead device
[   93.197907] usb 6-9: new high speed USB device using ehci_hcd and address 4
[  108.731457] usb 6-9: device not accepting address 4, error -110
[  108.843294] usb 6-9: new high speed USB device using ehci_hcd and address 5
[  124.376847] usb 6-9: device not accepting address 5, error -110
[  124.488684] usb 6-9: new high speed USB device using ehci_hcd and address 6
[  134.905631] usb 6-9: device not accepting address 6, error -110
[  135.017469] usb 6-9: new high speed USB device using ehci_hcd and address 7
[  143.275097] lp0: using parport0 (interrupt-driven).
[  143.334016] Adding 3229024k swap on /dev/sda5.  Priority:-1 extents:1 across:3229024k
[  143.886166] EXT3 FS on sda1, internal journal
[  145.002547] ip_tables: (C) 2000-2006 Netfilter Core Team
[  145.315284] No dock devices found.
[  145.435413] usb 6-9: device not accepting address 7, error -110
[  145.630321] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 5200+ processors (2 cpu cores) (version 2.20.00)
[  145.629966] powernow-k8:    0 : fid 0x13 (2700 MHz), vid 0x9
[  145.629969] powernow-k8:    1 : fid 0x12 (2600 MHz), vid 0xa
[  145.629971] powernow-k8:    2 : fid 0x10 (2400 MHz), vid 0xc
[  145.629973] powernow-k8:    3 : fid 0xe (2200 MHz), vid 0xe
[  145.629974] powernow-k8:    4 : fid 0xc (2000 MHz), vid 0x10
[  145.629975] powernow-k8:    5 : fid 0xa (1800 MHz), vid 0x10
[  145.629977] powernow-k8:    6 : fid 0x2 (1000 MHz), vid 0x12
[  146.467492] NET: Registered protocol family 10
[  146.467831] lo: Disabled Privacy Extensions
[  146.657427] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[  146.657430] apm: disabled - APM is not SMP safe.
[  146.853152] ppdev: user-space parallel port driver
[  147.007035] audit(1234221203.812:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5741 profile="/usr/sbin/cupsd" namespace="default"
[  147.784035] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[  147.784039] vboxdrv: Successfully done.
[  147.784040] vboxdrv: Found 2 processor cores.
[  147.784410] vboxdrv: fAsync=1 offMin=0x1055ba offMax=0x1055ba
[  147.784560] vboxdrv: TSC mode is 'asynchronous', kernel timer mode is 'normal'.
[  147.784563] vboxdrv: Successfully loaded version 2.1.2 (interface 0x000a0009).
[  148.285726] Clocksource tsc unstable (delta = -176133370 ns)
[  149.200385] r8169: eth0: link up
[  149.200392] r8169: eth0: link up
[  150.003696] NET: Registered protocol family 17
[  150.010665] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 18 (level, low) -> IRQ 16
[  150.134645] Bluetooth: Core ver 2.11
[  150.134839] NET: Registered protocol family 31
[  150.134843] Bluetooth: HCI device and connection manager initialized
[  150.134846] Bluetooth: HCI socket layer initialized
[  150.148588] Bluetooth: L2CAP ver 2.9
[  150.148591] Bluetooth: L2CAP socket layer initialized
[  150.168183] usb 6-9: new high speed USB device using ehci_hcd and address 8
[  150.172739] Bluetooth: RFCOMM socket layer initialized
[  150.172747] Bluetooth: RFCOMM TTY layer initialized
[  150.172749] Bluetooth: RFCOMM ver 1.8
[  150.394170] [fglrx] Reserve Block - 0 offset =  0Xfffc000 length = 0X4000
[  150.394176] [fglrx] Reserve Block - 1 offset =  0X0 length = 0X1000000
[  150.394179] [fglrx] Reserve Block - 2 offset =  0Xff7b000 length = 0X80000
[  150.467544] [fglrx] interrupt source 10000000 successfully enabled
[  150.467549] [fglrx] enable ID = 0x00000006
[  150.467556] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000
[  150.471738] [fglrx] interrupt source 60000001 successfully enabled
[  150.471742] [fglrx] enable ID = 0x00000007
[  150.471747] [fglrx] Receive enable interrupt message with irqEnableMask: 60000001
[  150.471781] [fglrx] interrupt source 00000040 successfully enabled
[  150.471784] [fglrx] enable ID = 0x00000008
[  150.471787] [fglrx] Receive enable interrupt message with irqEnableMask: 00000040
[  150.480982] [fglrx] interrupt source ff00002c successfully enabled
[  150.480986] [fglrx] enable ID = 0x00000009
[  150.480989] [fglrx] Receive enable interrupt message with irqEnableMask: ff00002c
[  150.481017] [fglrx] interrupt source ff00002d successfully enabled
[  150.481020] [fglrx] enable ID = 0x0000000A
[  150.481023] [fglrx] Receive enable interrupt message with irqEnableMask: ff00002d
[  150.481055] [fglrx] interrupt source 20000400 successfully enabled
[  150.481057] [fglrx] enable ID = 0x0000000B
[  150.481060] [fglrx] Receive enable interrupt message with irqEnableMask: 20000400
[  155.360264] hda-intel: Invalid position buffer, using LPIB read method instead.
[  157.655237] eth0: no IPv6 routers present
[  158.624669] usb 6-9: device not accepting address 8, error -110
[  158.666125] usb 6-9: new high speed USB device using ehci_hcd and address 9
[  164.422010] usb 6-9: device not accepting address 9, error -110
[  164.463822] usb 6-9: new high speed USB device using ehci_hcd and address 10
[  168.323421] usb 6-9: device not accepting address 10, error -110
[  168.365232] usb 6-9: new high speed USB device using ehci_hcd and address 11
[  172.225198] usb 6-9: device not accepting address 11, error -110
[  201.348237] usb 6-9: new high speed USB device using ehci_hcd and address 12
[  213.277413] usb 6-9: device not accepting address 12, error -110
[  213.390405] usb 6-9: new high speed USB device using ehci_hcd and address 13
[  228.930405] usb 6-9: device not accepting address 13, error -110
[  229.042305] usb 6-9: new high speed USB device using ehci_hcd and address 14
[  239.468315] usb 6-9: device not accepting address 14, error -110
[  239.580210] usb 6-9: new high speed USB device using ehci_hcd and address 15
[  249.129271] usb 6-9: device not accepting address 15, error -110
[65319.907018] usb 6-9: new high speed USB device using ehci_hcd and address 16
[65334.796648] usb 6-9: device not accepting address 16, error -110
[65334.904503] usb 6-9: new high speed USB device using ehci_hcd and address 17
[65349.979251] usb 6-9: device not accepting address 17, error -110
[65350.091101] usb 6-9: new high speed USB device using ehci_hcd and address 18
[65360.374175] usb 6-9: device not accepting address 18, error -110
[65360.485983] usb 6-9: new high speed USB device using ehci_hcd and address 19
[65370.856655] usb 6-9: device not accepting address 19, error -110
[65685.193358] usb 2-1: USB disconnect, address 3
[65704.631482] usb 6-3: new high speed USB device using ehci_hcd and address 20
[65719.661606] usb 6-3: device not accepting address 20, error -110
[65719.773452] usb 6-3: new high speed USB device using ehci_hcd and address 21
[65734.209958] usb 6-3: device not accepting address 21, error -110
[65734.292808] usb 6-3: new high speed USB device using ehci_hcd and address 22
[65743.791997] usb 6-3: device not accepting address 22, error -110
[65743.903837] usb 6-3: new high speed USB device using ehci_hcd and address 23
[65753.632667] usb 6-3: device not accepting address 23, error -110
[65753.744198] usb 6-9: new high speed USB device using ehci_hcd and address 24
[65768.864639] usb 6-9: device not accepting address 24, error -110
[65768.976621] usb 6-9: new high speed USB device using ehci_hcd and address 25
[65784.052417] usb 6-9: device not accepting address 25, error -110
[65784.151828] usb 6-9: new high speed USB device using ehci_hcd and address 26
[65794.351158] usb 6-9: device not accepting address 26, error -110
[65794.463950] usb 6-9: new high speed USB device using ehci_hcd and address 27
[65803.321074] usb 6-9: device not accepting address 27, error -110
```

Here are the contents of /proc/interrupts
```

           CPU0       CPU1
  0:        145          1   IO-APIC-edge      timer
  1:         13       4601   IO-APIC-edge      i8042
  4:          0          4   IO-APIC-edge
  6:          0          5   IO-APIC-edge      floppy
  7:          0          0   IO-APIC-edge      parport0
  8:          1          6   IO-APIC-edge      rtc
  9:          0          2   IO-APIC-fasteoi   acpi
 12:        775     312189   IO-APIC-edge      i8042
 14:          0          0   IO-APIC-edge      libata
 15:          0          0   IO-APIC-edge      libata
 16:       5483    5709315   IO-APIC-fasteoi   ohci_hcd:usb3, ohci_hcd:usb5, HDA Intel, fglrx
 17:        140      75814   IO-APIC-fasteoi   ohci_hcd:usb1, HDA Intel
 18:       1859     500519   IO-APIC-fasteoi   ohci_hcd:usb2, ohci_hcd:usb4
 19:       2162     323100   IO-APIC-fasteoi   ahci, ohci1394
 20:         39      99962   IO-APIC-fasteoi   ehci_hcd:usb6
221:        335     153724   PCI-MSI-edge      eth0
NMI:          0          0   Non-maskable interrupts
LOC:   23068541   32829793   Local timer interrupts
RES:    6020098    6131672   Rescheduling interrupts
CAL:        179         98   function call interrupts
TLB:      14808      17874   TLB shootdowns
TRM:          0          0   Thermal event interrupts
SPU:          0          0   Spurious interrupts
ERR:          0
MIS:          0

```

Any other thoughts let me know.

Thanks

---

### Post by neu2buntu on 2009-02-10
could it be a permissions issue. check >system > administration > users and groups > unlock > "your username" > properties > user privileges > and see you have ticked access external storage devicess automatically .    

another thought ,your errors in dmesg e.g 
```
device not accepting address 15, error -110 
```  i googled it and almost similar errors were mostly down to usb 1.1 and 2.0 incompatability,i dont know much about this but it might be a step in the right direction

---

### Post by gsocker on 2009-02-11
From dmesg:
```
[   47.070084] irq 20: nobody cared (try booting with the "irqpoll" option)
[   47.070089] Pid: 3379, comm: modprobe Tainted: P        2.6.24-23-generic #1
[   47.070097]  [<c0169214>] __report_bad_irq+0x24/0x80
[   47.070104]  [<c01694eb>] note_interrupt+0x27b/0x2c0
[   47.070108]  [<f88b8ccb>] usb_hcd_irq+0x2b/0x60 [usbcore]
[   47.070124]  [<c0168710>] handle_IRQ_event+0x30/0x60
[   47.070127]  [<c0169ea6>] handle_fasteoi_irq+0x86/0xe0
[   47.070130]  [<c0106f0b>] do_IRQ+0x3b/0x70
[   47.070133]  [<c01929a1>] sys_read+0x41/0x70
[   47.070137]  [<c0105403>] common_interrupt+0x23/0x30
[   47.070143]  =======================
[   47.070144] handlers:
[   47.070145] [<f88b8ca0>] (usb_hcd_irq+0x0/0x60 [usbcore])
**[   47.070157] Disabling IRQ #20**

```According to /proc/interrupts:
```
 20:         39      99962   IO-APIC-fasteoi   **ehci_hcd:usb6**
```For some reason, the USB 2.0(EHCI) driver is not grabbing interrupts for its associated  USB interface.
Try booting with "noapic" or the "irqpoll" option listed in dmesg and see if either makes a difference.
Boot options howto: [https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)
If not, best bet is to file a bug report on launchpad. 
Also, if you have one handy, try booting from an 8.10 livce cd and see if the problem still exists.

As a workaround, you may be able to disable the USB2 driver(ehci-hcd) and use your devices at USB 1.1 speeds.

---

### Post by Vaedrah on 2009-02-11
I have 2 notebooks and 1 PC of very different ages and Ubuntu 8.04 is installed on all (as dual boot/XP and also as virtual machines + Ubuntu8.10. No configuration has had problems with a mouse either wired or wireless. I suggest you check your hardware for faults.

Is there a diagnostic/Ubuntu that will do this? In windows, the "device manager" sort of does but it isn't that capable - real USB h/w faults will be missed of course!

I suggest try some other USB items out (printer, etc) and see if the h/w actually works. The USB port(s) may be faulty. I have never seen any need for corrective measures with Ubuntu/Fedora/Debian (and yes Vista/XP) wrt mouse/USB connectivity. 

As a previous poster commented "I wouldn't blame Ubuntu" - it's almost impossible to "incorrectly install Ubuntu" - even more so for a mouse to not work. 

Perhaps you have a very strange computer configuration? If this is the case, and XP/Vista used to work then I suggest go back to it - buy a new computer sometime - try Ubuntu on a clear machine! - You will like it a lot, trust me :popcorn:

---

### Post by xinman on 2009-02-12
neu2buntu:  It's not a permission thing, I checked that before I posted.  Thanks for you thoughts though.

Vaedrah:  You must not read the entire post to see what has been tried and what hasn't.  If you'll notice multiple devices had been tried and these devices work on other machines running earlier versions of Ubuntu.  Also, to not that these devices worked on the very same ports a week ago in Windows XP.  I appreciate your 2 cents but I do ask that if your going to reply to a post the least you can do is read the entire post to see what has been tried prior to just assuming that you know it cannot be Ubuntu.  As I pointed out prior to this I have been using Linux for a while now (around 8 years) and I have never had to use a corrective procedure to get usb to work either.  But that doesn't mean it couldn't happen, there are many motherboards and also many version of the kernel.  Ubuntu is not always just going to work, hence the "Global Bug Jam" taking place this month.  I was considering to go back to XP but I must say I've been using Linux for years now as a server or an experiment and never could get myself to go Linux as a full time desktop.  I was trying to fix this problem before I jumped ship.  This may be the year of Linux on the desktop (for me anyway).  But if I give up so easily then I fail that quickly.  I do like Ubuntu and I've used it for a while now, in fact since before 5.10 (5.02? or 5.04? :confused:)

gsocker: I really appreciate your help, I tried the noapic and it didn't seem to work but then I tried the irqpoll and wallah!!!  I think you've done it.  It seems to be working, I've tried 3 of the devices and they all seem to work.  Is there anyway to tell if it's using 2.0 or 1.1 specs?

---

### Post by niteshifter on 2009-02-12
Hi,

> **xinman said:**
> ...  Is there anyway to tell if it's using 2.0 or 1.1 specs?

This can get complicated :) Do this:
```
cd /proc/bus/usb
cat devices | less

```
A typical output (i.e. here's mine, just the first _internal_ device)
```
T:  Bus=07 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 6
B:  Alloc=  0/800 us ( 0%), #Int=  0, #Iso=  0
[COLOR="Red"]D:  Ver= 2.00[/COLOR] Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.22-16-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.7
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:* If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   4 Ivl=256ms

```

That text highlighted in red is USB version. Here's where it gets a bit complicated: those Bus numbers don't necessarily correspond to a physical port. For example, I can plug a USB 2.0 device into a port on my laptop in this example, a flash drive. Here's lsusb output:
```
Bus 006 Device 001: ID 0000:0000  
Bus 007 Device 007: ID 0d7d:1600 Phison Electronics Corp. 
Bus 007 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000 

```
Ok, I unmount it and plug in a USB 1.1 device (an old 3.5 floppy drive) - same physical port , and get this from lsusb:
```
Bus 006 Device 001: ID 0000:0000  
Bus 007 Device 001: ID 0000:0000  
Bus 003 Device 003: ID 054c:002c Sony Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000 

```
See the difference? The hardware does some switching independent of the OS on some systems.

Best way I can think of to test port speed, as you have a couple of GB-sized storage units is to time a transfer of a large file and do the math.

---

### Post by niteshifter on 2009-02-12
Hi,

I was a bit rushed on that last post. Let me amplify a bit.
```
cat /proc/bus/usb/devices
```
dumps all the the terminal.
```
cat /proc/bus/usb/devices | less
```
will pass the output through the pager utility (less), scroll up/down with arrow or page up/dn keys.

When done with no devices physically connected to the machine will return a listing of the base characteristics of the machine's internal USB devices. When done with external devices connected it will show that external devices characteristics mapped in.
This mapping of external device to internal device is hardware and software (the OS) controlled on modern machines, but mostly hardware controlled since the OS just instructs the hardware during init.

So, to answer your question about 1.1 vs 2.0, list the devices as described above. Those that show Ver 2.0 should have any 2.0 external device connected mapped to them, Ver 1.1 get the low speed (1.1) devices mapped.

Now, back to speed determination. The only sure-fire way is to measure the transfer as I described in my first post on this thread. To see what the system believes the speed of an attached device is do these two steps:
First locate the bus the device is attached to:
```
lsusb
```
Example output:
```
Bus 007 Device 002: ID 0d7d:1600 Phison Electronics Corp. 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  

```
Now lets look here:
```
cd /sys/bus/usb/devices
ls
```
Example output:
```
1-0:1.0  3-0:1.0  5-0:1.0  7-0:1.0  7-1:1.0  usb2  usb4  usb6
2-0:1.0  4-0:1.0  6-0:1.0  7-1      usb1     usb3  usb5  usb7

```
From lsusb output, we know the device is on Bus 7, so:
```
cd usb7
ls

```
Example output:
```
7-0:1.0              bNumInterfaces  maxchild
7-1                  bus             power
bcdDevice            busnum          product
bConfigurationValue  configuration   quirks
bDeviceClass         dev             serial
bDeviceProtocol      devnum          speed
bDeviceSubClass      driver          subsystem
bmAttributes         ep_00           uevent
bMaxPacketSize0      idProduct       usb_device:usbdev7.1
bMaxPower            idVendor        usb_endpoint:usbdev7.1_ep00
bNumConfigurations   manufacturer    version

```

Printing the speed file gives us the speed the system believes it to be:
> foo@bar:/sys/bus/usb/devices/usb7$ cat speed
foo@bar:/sys/bus/usb/devices/usb7$ 480

The above shows a connect speed of 480 Mb/s, USB 2.0 speed.
And yes, the version is there also:
> foo@bar:/sys/bus/usb/devices/usb7$ cat version
foo@bar:/sys/bus/usb/devices/usb7$ 2.00


Again, these are values the system is attempting. Actual transfer speeds are usually less than datasheet maximums, depending on load, USB network topology and the like. Best to measure :)

---

### Post by xinman on 2009-02-13
niteshifter: 

Thanks for the great explaination, I never would have got that myself.  The usb seems to be working great and I would say by the speed of the pics downloading from my sd card its running at 2.0. According to your method it says its running at 2.0.  I do have one problem, but I'm not that worried about it as it all seems to work.

> I was a bit rushed on that last post. Let me amplify a bit.
Code:

cat /proc/bus/usb/devices

dumps all the the terminal.
Code:

cat /proc/bus/usb/devices | less

will pass the output through the pager utility (less), scroll up/down with arrow or page up/dn keys.

This returns: 
```
cat: /proc/bus/usb/devices: No such file or directory
```

Like I said it seems to work fine so its no big deal, just wondering.

Thanks again for the help!!!

---

### Post by niteshifter on 2009-02-14
Hi,

Differences in the way our two systems are configured. And that's sorta a my bad on my part - I forgot I had to adjust mine to support earlier versions of Virtualbox (enable usbfs). Stock Ubuntu doesn't have that enabled (not needed except for a very few (older) applications).

I should add for any others reading this that enabling usbfs is no longer needed for Virtualbox (as of 2.x onward).

---

