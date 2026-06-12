---
title: "Karmic doesn't recognize CD-RW drive"
date: 2010-01-20
forum: New to Ubuntu
---

### Post by Crimson_Tider on 2010-01-20
Hey y'all. I was wondering if someone could help me with my CD-RW drive. I put a CD-ROM in it for the first time since I installed Karmic, and the light on the front of the drive starts blinking, and it sounds like the disc is spinning for a few seconds, and then it goes totally silent. Ubuntu never automounts it, so I never see any icon on my desktop, and Nautilus doesn't automatically open and show the contents like it does when I plug in my USB thumb drive. I'm not totally sure exactly what information anyone might need, so I've printed below what I've learned so far (I am a newbie) that might come in handy:

Results of sudo lshw -class disk -class storage

```
******@******-desktop:~$ sudo lshw -class disk -class storage
[sudo] password for ******: 
  *-ide:0                 
       description: IDE interface
       product: MCP51 IDE
       vendor: nVidia Corporation
       physical id: d
       bus info: pci@0000:00:0d.0
       logical name: scsi2
       logical name: scsi3
       version: a1
       width: 32 bits
       clock: 66MHz
       capabilities: ide pm bus_master cap_list emulated
       configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
       resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:f400(size=16)
     *-disk:0
          description: ATA Disk
          product: ExcelStor Techno
          physical id: 0.0.0
          bus info: scsi@2:0.0.0
          logical name: /dev/sda
          version: P21O
          serial: PV6704Q3A52KHB
          size: 74GiB (80GB)
          capabilities: partitioned partitioned:dos
          configuration: ansiversion=5 signature=f560f834
     *-disk:1
          description: ATA Disk
          product: WDC WD200EB-75CP
          vendor: Western Digital
          physical id: 0
          bus info: scsi@2:0.1.0
          logical name: /dev/sdb
          version: 06.0
          serial: WD-WMAAU5222350
          size: 18GiB (20GB)
          capabilities: partitioned partitioned:dos
          configuration: ansiversion=5 signature=00c02ed1
     *-cdrom
          description: SCSI CD-ROM
          physical id: 1
          bus info: scsi@3:0.1.0
          logical name: /dev/cdrom1
          logical name: /dev/scd0
          logical name: /dev/sr0
          capabilities: audio
          configuration: status=ready
  *-ide:1
       description: IDE interface
       product: MCP51 Serial ATA Controller
       vendor: nVidia Corporation
       physical id: e
       bus info: pci@0000:00:0e.0
       version: a1
       width: 32 bits
       clock: 66MHz
       capabilities: ide pm msi ht bus_master cap_list
       configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
       resources: irq:23 ioport:9f0(size=8) ioport:bf0(size=4) ioport:970(size=8) ioport:b70(size=4) ioport:e000(size=16) memory:fe02d000-fe02dfff
  *-scsi
       physical id: 6
       bus info: usb@1:4
       logical name: scsi4
       capabilities: emulated scsi-host
       configuration: driver=usb-storage
     *-disk
          description: SCSI Disk
          physical id: 0.0.0
          bus info: scsi@4:0.0.0
          logical name: /dev/sdc
          size: 1915MiB (2008MB)
          capabilities: partitioned partitioned:dos

```

Contents of /etc/fstab

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=92ff2a95-44df-4d52-9912-d8881a0557f8 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=551f5053-9048-436d-9bf5-dfc62a04e919 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

You might need to know that I also have a CD-ROM drive; I think it is listed above in the results of lshw, but I don't think that drive is working at all as of a few days ago. Whatever the case, I'm not really concerned about that problem right now.

Thanks.

---

### Post by cariboo on 2010-01-21
You don't have a mount point setup in /etc/fstab. My looks like this:

```
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

add the above line to the bottom of your /etc/fstab and see if it helps.

---

### Post by Crimson_Tider on 2010-01-21
After I edit the file and hit save, it gives me the following message:

```
Unable to mount cdrom0
mount: block device /dev/sr0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


```

I did just notice that there is a directory in /media that wasn't there before; it is named
1a106a8c-30e8-4b2c-a444-7c3f71cc0a3b and has 22 items in it, including /bin and /boot and /usr and /var

---

### Post by Crimson_Tider on 2010-01-22
Anyone?

Bueller?

---

