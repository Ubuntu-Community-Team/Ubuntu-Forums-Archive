---
title: "Two hard drives?"
date: 2011-05-03
forum: New to Ubuntu
---

### Post by Old-un on 2011-05-03
I now have 2 SATA hard drives and i would like to install Ubuntu 11.04 on the first hard drive and another OS on the second hard drive. Does anyone know of a very easy to follow tutorial covering this subject please.

---

### Post by Fedz on 2011-05-03
Very easy ... it's what I've done :)

Simply choose which drive is for Ubuntu & done -  no tutorial required :)

My comp was set to boot onto the windows drive 1st but, I changed the boot order to choose Ubuntu drive first as default as very very rarely need windows if at all :)

---

### Post by Mark Phelps on 2011-05-03
To be safe, have only one drive connected at a time when you're installing the OSs.  That prevents accidentally overwriting the wrong MBRs and partitions -- something easily done with the new, confusing, Ubuntu installer.

Then, when done, boot from the Ubuntu drive, open a terminal, and enter "sudo update-grub".  That will regenerate the GRUB menu and add an entry for the Windows OS.

---

### Post by corncob on 2011-05-03
I've done this and I think its the way to go if you have two hard drives.  I disconnected the windows drive when I installed Ubuntu and afterwards reconnected it.  I chose the default boot drive in the BIOS setup or, by pressing ESC, got a menu of boot devices on startup.  As I rarely used Windows I let it default to Ubuntu but Windows was there if somebody needed it.

---

### Post by seawolf167 on 2011-05-03
> **Mark Phelps said:**
> To be safe, have only one drive connected at a time when you're installing the OSs.  That prevents accidentally overwriting the wrong MBRs and partitions -- something easily done with the new, confusing, Ubuntu installer.

Then, when done, boot from the Ubuntu drive, open a terminal, and enter "sudo update-grub".  That will regenerate the GRUB menu and add an entry for the Windows OS.

+1 for this, if you are worried about loosing any data during your installation, a good and very easy to use program is [Clonezilla]("http://www.clonezilla.org")

---

### Post by Old-un on 2011-05-03
Thanks for all the help and advice folks

---

### Post by oldfred on 2011-05-03
If one drive is going to be windows it should be the first. Ubuntu does not care as it uses UUIDs to find the correct partition, but many versions of windows get confused if not sda.

Installing Ubuntu in Hard Disk Two (or more) internal or external
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

---

