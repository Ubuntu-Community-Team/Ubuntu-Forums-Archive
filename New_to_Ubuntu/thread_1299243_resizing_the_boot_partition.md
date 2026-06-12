---
title: "resizing the boot partition??"
date: 2009-10-23
forum: New to Ubuntu
---

### Post by JamesParnell on 2009-10-23
i currently have a 60gb boot partition, 2gb swap, and 93gb unallocated...but i would like to rezise the boot partition , as i am never going to fill it all...is it possible to resize it?

---

### Post by GimmeCoffe on 2009-10-23
Yes, you can use GParted to resize partition.

~GimmeCoffe

---

### Post by JamesParnell on 2009-10-23
thats the reason i ask, i am staring at the gparted screen now and when i select the boot parition, i have no option to resize it.

---

### Post by GimmeCoffe on 2009-10-23
ok, is your boot partition ext3 or ext4?

---

### Post by GimmeCoffe on 2009-10-23
take a look at this: [http://gparted.sourceforge.net/larry/resize/resizing.htm]("http://gparted.sourceforge.net/larry/resize/resizing.htm")

---

### Post by Dullstar on 2009-10-23
Is your hard drive mounted?  Make sure you are using GParted from your Ubuntu LiveCD, or some other Linux LiveCD to include the program.

---

### Post by Paqman on 2009-10-23
> **JamesParnell said:**
> thats the reason i ask, i am staring at the gparted screen now and when i select the boot parition, i have no option to resize it.

That's because you can't modify a partition while it's in use. You'll have to boot up into a LiveCD or LiveUSB and run Gparted from there.

---

### Post by JamesParnell on 2009-10-23
ok thanks for that..

---

