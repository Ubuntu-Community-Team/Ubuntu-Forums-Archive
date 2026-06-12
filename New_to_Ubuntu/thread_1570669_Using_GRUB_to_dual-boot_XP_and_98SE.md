---
title: "Using GRUB to dual-boot XP and 98SE?"
date: 2010-09-08
forum: New to Ubuntu
---

### Post by Dark-Star on 2010-09-08
Trying to move old HD with previous installation of 98SE over to working XP machine and dual-boot. Can I use GRUB without installing Ubuntu itself? If so, how?

---

### Post by oldfred on 2010-09-08
I have a FAT32 windows recovery USB. Just as a test I installed grub to it and it still boots the windows partition and lets me boot ISOs that I installed since I had lots of room on the USB flash drive.

If You have two drives you may have to experiment with drivemap.

```
This works for my Flash drive:
menuentry "Microsoft Windows Recovery" {
      set root=(hd0,1)
      chainloader --force +1
}

menuentry " " {
set root= 
}

Other windows entries I saved If you leave search line in you have to use your UUID, but you do not need search line at all if set root is correct:

menuentry "Windows XP" {
       insmod ntfs
       set root=(hd1,1)
       search --no-floppy --fs-uuid --set EC0CEE940CEE595A
       drivemap -s (hd1) (hd0)
       chainloader +1
}

menuentry "Microsoft Windows XP" {
      set root=(hd0,8)
  
      chainloader --force +1
      
}





```

---

### Post by jtarin on 2010-09-08
You can dual boot just by editing your boot.ini in the C:\ folder if Win XP was installed as Fat 32. I assume (* is on a Primary partition marked as bootable? [Here's a read on it.]("http://www.computing.net/answers/windows-95/adding-win98-dual-boot-to-xp/167931.html")

---

### Post by Dark-Star on 2010-09-09
XP was installed as NTFS.

The drive with XP is a clone of the original one it had, which was reporting bad sectors on scans. New one works fine.

The drive with 98se was rescued from a box with a MB that was hopelessly flaky. (IDE controllers died, then random screwiness, now random lockups. needless to say I've had quite enough of that monkey business.)

That link lead me to a 3rd-party boot app called GAG...looks pretty good, might use that. Either of you tried it?

---

### Post by jtarin on 2010-09-09
Great boot loader...Ugly interface...LOL :)

---

### Post by Dark-Star on 2010-09-09
Pffft. If I had a dime for every ugly interface I'd ever encountered, I could hire Bill Gates to be my butler.

EDIT: How should I jumper the drives? Master-slave? Both set as Master?

---

### Post by oldfred on 2010-09-09
PATA/IDE drives can have primary and secondary channels (two cables) and master and slave drives. Old systems only booted from primary master as BIOS was not smart enough to do more than jump to MBR of primary master.

If you have older 40 wire cables one drive must be master and the other slave. Some have a master with slave jumper setting. If you have the newer cable 80 wires then you jumper both as cable select.

with pictures:
[http://en.wikipedia.org/wiki/Parallel_ATA](http://en.wikipedia.org/wiki/Parallel_ATA)
Some history:
[http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html](http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html)
If you have the more modern 80 conductor 'cable-select' type of IDE ribbon cables, make sure the blue plug is connected to the motherboard, the grey plug is plugged into your slave drive (if any), and the black plug is plugged into your master hard drive. Jumpers on drives must be set to cable select.

---

### Post by Dark-Star on 2010-09-09
> **oldfred said:**
> PATA/IDE drives can have primary and secondary channels (two cables) and master and slave drives. Old systems only booted from primary master as BIOS was not smart enough to do more than jump to MBR of primary master.

If you have older 40 wire cables one drive must be master and the other slave. Some have a master with slave jumper setting. If you have the newer cable 80 wires then you jumper both as cable select.

Just the cable matters, not the hard drive?

---

### Post by egalvan on 2010-09-09
(probably) more than you needed to know
includes graphics

[http://ubuntuforums.org/showthread.php?p=9825549#post9825549](http://ubuntuforums.org/showthread.php?p=9825549#post9825549)

---

### Post by jtarin on 2010-09-09
Did this thread hiccup???? :)

---

