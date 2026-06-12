---
title: "Clone windows xp hard drive using ubuntu"
date: 2009-11-27
forum: New to Ubuntu
---

### Post by lance bermudez on 2009-11-27
I have a friend who wants to know if i could copy her hard drive for her. I have two hard drives of the same size 40 gb One is seagate barracuda ata iv and the other isseagate model st340015a. The first one has windows xp on it and we would like to copy it to the other hard drive. I want to replace the first hard drive with the second so i think what i want to do is what i think is more properly call an image? How do i do this using ubuntu. I'm a complete new bee to this help please.

---

### Post by arochester on 2009-11-27
This might help: "How to migrate an operating system to a bigger hard disk.  " at [http://forums.techguy.org/hardware/633802-how-migrate-operating-system-bigger.html](http://forums.techguy.org/hardware/633802-how-migrate-operating-system-bigger.html)

---

### Post by arochester on 2009-11-27
...also see Using a "Linux Live CD to clone XP " on [http://www.justlinux.com/forum/showthread.php?threadid=134457](http://www.justlinux.com/forum/showthread.php?threadid=134457)

---

### Post by carl.davis on 2009-11-27
If they are exactly the same size you could use dd to copy the bits from one drive to the other. However, you MUST be very careful because it is fairly easy to copy the blank drive to your XP driving. If it were me, I would boot Linux with the source drive and:

```
dd if=/dev/hdc of=source.iso
```

Then, remove the source drive, install the target drive, boot Linux and type:

```
dd if=source.iso of=/dev/hdc
```

MAKE sure know where the targe drive installed to, i.e. hda, hdb, hdc, hdd.

If the drives are of the same bus type, you might want to try Clonezilla.

[http://clonezilla.org/](http://clonezilla.org/)

And lastly, if you want to purchase a commercial product, (or they have a trial version) try Acronis' backup products. I have used them in the past and they work very well.

[http://www.acronis.com/enterprise/download/backup-recovery/advanced-workstation/](http://www.acronis.com/enterprise/download/backup-recovery/advanced-workstation/)

---

