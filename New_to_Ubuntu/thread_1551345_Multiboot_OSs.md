---
title: "Multiboot OSs"
date: 2010-08-12
forum: New to Ubuntu
---

### Post by zer010 on 2010-08-12
Right now, I am dual-booting 10.04 and XP. I've googled trying to boot multiple OSs. I'd like to be able to try out other *nix type OSs and keep what I have. There were a couple different ways that I found to do this. Which one is best? My current partitions are setup as so:*-disk:0
                description: ATA Disk
                product: IBM-DPTA-372050
                vendor: IBM
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: P76G
                serial: JMYJMGF2756
                size: 19GiB (20GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000590a4
              *-volume
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 8070a922-5e20-1a4c-870e-5866c9da641c
                   size: 19GiB
                   capacity: 19GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2010-07-18 18:18:02 filesystem=ntfs state=clean
           *-disk:1
                description: ATA Disk
                product: WDC WD400BB-60DG
                vendor: Western Digital
                physical id: 1
                bus info: scsi@0:0.1.0
                logical name: /dev/sdb
                version: 05.0
                serial: WD-WMADK1357608
                size: 37GiB (40GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=00051790
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.1.0,1
                   logical name: /dev/sdb1
                   logical name: /
                   version: 1.0
                   serial: c32e2952-309c-46ca-a75a-73a29fdb7228
                   size: 12GiB
                   capacity: 12GiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2010-08-07 01:03:33 filesystem=ext4 lastmountpoint=/&#65533;&#65533;V&#65533;;&#65533;(&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;p&#65533;&#65533;&#65533;&#65533;g &#65533;&#65533;g/&#65533;d&#65533;&#65533;&#65533;&#65533;!&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;j modified=2010-08-07 01:17:29 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2010-08-11 15:57:56 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.1.0,2
                   logical name: /dev/sdb2
                   size: 25GiB
                   capacity: 25GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sdb5
                      logical name: /home
                      capacity: 24GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,barrier=1,data=ordered state=mounted
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sdb6
                      capacity: 952MiB
                      capabilities: no


one said to install a main then install another resizing partitions and letting GRUB do it's discovery.
the other said to install the others under /mount/guest.

Someone have a sure way to go about this?

---

### Post by Kyluke on 2010-08-12
Let grub configure it

---

### Post by zer010 on 2010-08-13
That's what I was thinking. How much space is recommended for a "test OS"? If I really like the new OS, is there a way to later increase it's partition?

---

