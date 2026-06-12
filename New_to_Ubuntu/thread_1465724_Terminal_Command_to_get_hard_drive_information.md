---
title: "Terminal Command to get hard drive information?"
date: 2010-04-29
forum: New to Ubuntu
---

### Post by Messyhair42 on 2010-04-29
What are the terminal commands to relate /dev/hda,/hdb,/hdc... to IDE(A,B,C), SCSI(D,E,F)...? I''m preparing for a total system reformat with the release of Lucid and this would be useful, thank you.

---

### Post by srs5694 on 2010-04-29
It's unclear precisely what you mean.

Drive letters in the Microsoft sense (C:, D:, etc.) are essentially unmappable to Linux disks or partitions, at least in a completely reliable way. As floppies, A: and B: will translate to /dev/fd0 and /dev/fd1 (or possibly the other way around), but the rest could be anything, in principle. Most Windows drive letters will map to partitions in Linux, so C: might be /dev/sda1 and D: might be /dev/sdb5. Windows' CD/DVD drive letters will map to a Linux CD/DVD device, typically /dev/cdrom, /dev/dvd, or some variant of those. This will usually be a symbolic link to something else, such as /dev/sr0 or /dev/hdb.

I suspect, though, that you're talking about whole disks, which don't normally get letters in Windows except as partition identifiers. (Floppies and CD/DVDs are exceptions to this rule.) This issue is both easier and harder. In the past, IDE disks got /dev/hdn identifiers, where n was a letter from a on, as in /dev/hda, /dev/hdb, etc. SCSI disks got /dev/sdn identifiers. The master device on the first IDE chain was /dev/hda, that chain's slave device was /dev/sdb, the master device on the second IDE chain was /dev/hdc, and so on. Device letters could be skipped, so a system could have /dev/hda and /dev/hdc but no /dev/hdb. SCSI devices, OTOH, were assigned from a onward, without respect to position on the SCSI chain or SCSI ID number, so if you had a /dev/sdc, you'd also necessarily have a /dev/sda and a /dev/sdb. SCSI device filenames were assigned sequentially, but the rules varied a bit from one SCSI host adapter to another. If a system had multiple host adapters, ordering would depend on the order in which the drivers were loaded, which could vary with system configuration.

These same basic rules are still followed today, but there are a lot of new wrinkles. Most notably, the old IDE drivers are on the way out. Even IDE (today often called Parallel ATA, or PATA) disks often use SCSI compatibility drivers, so they often get /dev/sda, /dev/sdb, etc. names. Serial ATA (SATA) disks usually use SCSI compatibility drivers, although some older IDE-style drivers for SATA devices do exist. USB and most other device interfaces follow the SCSI model. Because some of these devices are hot-swappable, gaps can now exist in the device numbering -- if you've got an SATA disk (/dev/sda) and plug in two USB flash drives (/dev/sdb and /dev/sdc) and then remove the first of these USB flash drives, you'll have /dev/sda and /dev/sdc but no /dev/sdb. Device ordering still depends on order of driver loading and device detection, but if you've got a motherboard with multiple ports, it can be hard to predict which disk will get which device ID, both because the ports may not be well labelled and because the motherboard may use two different chipsets to control all its ports. There's certainly no guarantee that the numbering in Linux will match the IDs in Windows, OS X, FreeBSD, or any other OS.

---

### Post by Messyhair42 on 2010-04-30
I am talking about whole drives/devices. and i meant to label them as /hda, /hdb... and I'm trying to relate something like /hda to (hdA,B)
here is a part of my /grub/menu.lst file that has an example of the information that i'm trying to gather
```
title              Windows 7 (on /dev/sda1)
root               **(hd1,0)**
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
```

what's most important in my case is having the location of my boot sector for a specified OS, in bold above

---

### Post by championboxes on 2010-04-30
not sure if this is what you are looking for but

```
sudo fdisk -l
```

should list all hdd's and partitions

---

### Post by laffinet on 2010-04-30
oops, beat me to it.

---

### Post by Messyhair42 on 2010-04-30
here's the output of ```
sudo fdisk -l
```
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x622b854a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13        8924    71577600    7  HPFS/NTFS
/dev/sda3            8925        8936       96390   83  Linux
/dev/sda4            8937       19457    84509932+   5  Extended
/dev/sda5            8937        9191     2048256   82  Linux swap / Solaris
/dev/sda6            9192        9701     4096543+  83  Linux
/dev/sda7            9702       13526    30724281   83  Linux

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007fe0d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         267     2144646   83  Linux
/dev/sdb2             268      117954   945320827+   5  Extended
/dev/sdb3          117955      121602    29294592    6  FAT16
/dev/sdb5             268         753     3903763+  82  Linux swap / Solaris
/dev/sdb6             754        1239     3903763+  83  Linux
/dev/sdb7            1240        1506     2144646   83  Linux
/dev/sdb8            1507        1542      289138+  83  Linux
/dev/sdb9            1543      117954   935079358+  83  Linux

```

it identifies all my partitions, but how the hardware is recognized, see my last post. I'm trying to identify locations as they would be put into /boot/grub/menu.lst, such as (hdA,B)

---

### Post by Paqman on 2010-04-30
> **Messyhair42 said:**
> I'm trying to identify locations as they would be put into /boot/grub/menu.lst, such as (hdA,B)

/boot/grub/menu.lst isn't used in the newer version of Grub that Ubuntu has used for the last couple of versions. Is there some reason you'd need to be editing the Grub setup manually? If you let us know what you're trying to do, we can tell you how to do it in Grub2.

If all you're trying to do is make sure Windows boots alright, don't worry about it. Grub2 is pretty good at identifying other OSes and setting them up correctly.

---

