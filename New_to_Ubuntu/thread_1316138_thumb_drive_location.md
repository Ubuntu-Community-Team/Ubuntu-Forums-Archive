---
title: "thumb drive location"
date: 2009-11-05
forum: New to Ubuntu
---

### Post by Messyhair42 on 2009-11-05
I installed Karmic on a thumb drive and i cant get it to boot. the disk itself doesn't have a boot sector so i'm trying to modify the /boot/grub/menu.lst of my desktop Jaunty installation to point to the disk. here is the output of fdisk -l
```
Disk /dev/sdc: 4007 MB, 4007657472 bytes
255 heads, 63 sectors/track, 487 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002489b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         458     3678853+  83  Linux
/dev/sdc2             459         487      232942+   5  Extended
/dev/sdc5             459         487      232911   82  Linux swap / Solaris

```

what i can't find through code is the location ID i.e. SCSI 1 (X,X,X) which is all i think i need. thank you

---

### Post by RedSingularity on 2009-11-06
Have you tried using the "mount" command?

For example,

sudo mount /dev/sdc /media/disk-1

---

### Post by Joe Ker1086 on 2009-11-06
had a similar problem with an sd card, try dmesg|tail and post the output

---

### Post by Messyhair42 on 2009-11-07
i dont think that command helps me, it gives me stuff related to wlan when all i'm trying to find is the drive location USB (x,x,x)

---

### Post by Joe Ker1086 on 2009-11-07
But it should show you if it is trying to load, i used it earlier to locate a sd card that wouldnt boot.....at least showed that it was seeing it.

---

### Post by Messyhair42 on 2009-11-10
output of dmesg|tail
```
[362770.198412]  sdc: sdc1 sdc2 < sdc5 >
[362770.704198] sd 6:0:0:0: [sdc] Attached SCSI removable disk
[362770.704265] sd 6:0:0:0: Attached scsi generic sg3 type 0
[362772.085326] EXT4-fs: barriers enabled
[362772.108771] kjournald2 starting.  Commit interval 5 seconds
[362772.112932] EXT4 FS on sdc1, internal journal on sdc1:8
[362772.112937] EXT4-fs: delayed allocation enabled
[362772.112938] EXT4-fs: file extents enabled
[362772.113070] EXT4-fs: mballoc enabled
[362772.113073] EXT4-fs: mounted filesystem with ordered data mode.

```

---

### Post by Messyhair42 on 2009-11-13
bumping

---

### Post by RedSingularity on 2009-11-13
Have you tried the "mount" command?

---

### Post by Messyhair42 on 2009-11-14
i can mount it just fine, I'm trying to find the location of the drive i.e. USB (0,0,0) so i can add the entry to /grub/menu.lst in order to boot to the Karmic installation

---

### Post by RedSingularity on 2009-11-14
If you want the location of the drive do 

sudo fdisk -l

---

### Post by Messyhair42 on 2009-11-14
fdisk -l gives me the location in /media but not the how grub or the bios sees it, i know there is another command but i cannot remember or locate it

---

### Post by quixotic-cynic on 2009-11-14
I did this a while ago by cheating. Press e when the grub menu appears and just experiment with the partition to boot from until it works. It's probably hd(1,0) if you only have one hard disk (which would be hd(0,0) obviously).

Making a note of where the kernel and initrd are located on the USB is probably a good idea first.

Try it if you don't mind kludges. ;)

---

### Post by QLee on 2009-11-14
[QUOTE=Messyhair42]fdisk -l gives me the location in /media but not the how grub or the bios sees it, i know there is another command but i cannot remember or locate it[/QUOTE]

Well, dmesg gave you the device node for the unit, that is how it is seen by the system for the current attachment.

However, what you *might* be thinking of is "blkid". If you sudo blkid you would get a list of the UUIDs for the partitions on your system and you could mount the unit by UUID in the GRUB. That way it could mount regardless of the device node assigned.

On the other hand, are you trying to boot an ext4 formatted partition from legacy GRUB? What choices did you make for Karmic when you installed?

---

