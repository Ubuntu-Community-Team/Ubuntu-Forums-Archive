---
title: "Can't Get Gparted Working"
date: 2009-01-12
forum: New to Ubuntu
---

### Post by djk21108 on 2009-01-12
Hi I'm very new to this whole game.  I have a 160 GB hard drive, of which linux is taking up 10gb.  I'm trying to make a new partition for windows, but i can't resize my /dev/sda1.  It won't unmount either.  And there's a little key next to the name.


HELP!1!

---

### Post by nhasian on 2009-01-12
your not trying to resize the partition your currently using are you?  boot off the LiveCD instead and then run gparted.  now you will be able to resize the partitions because they are not mounted.

---

### Post by dragos240 on 2009-01-12
try parted magic, it's a bootable cd that has many features for resizing and moving partitions. Oh and don't try to unmount your linux partition while in linux, if you do that, disaster will strike!

---

