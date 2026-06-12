---
title: "expanding v-box harddrive"
date: 2009-08-16
forum: New to Ubuntu
---

### Post by misswham on 2009-08-16
Windows did an automatic update and the harddrive space on the windows part of vbox is almost used up. Is there a way to make vbox bigger on harddrive? I have the xp set to 7mbs and I would like to enlarge it to 20mbs. Is this possible without messing anything up?

---

### Post by nhasian on 2009-08-17
1. Create new VM-Harddisk
2. Attach this disk as second disk to VM
3. Boot VM with clonezilla liveCD
4. Clone old VDI to new VDI (see 1+2)
5. Boot VM with gparted liveCD
6. Resize new VDI
7. Swap VM-Harddisk (New VDI -> Old VDI)

---

### Post by lkraemer on 2009-08-18
Here is a link to what nhasian has posted with a little more detail.

[http://ubuntuforums.org/showthread.php?t=723219&highlight=VDI](http://ubuntuforums.org/showthread.php?t=723219&highlight=VDI)
Post #5.

lkraemer

---

