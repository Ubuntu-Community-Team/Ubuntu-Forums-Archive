---
title: "Two copies of intrepid"
date: 2009-04-20
forum: New to Ubuntu
---

### Post by bobin on 2009-04-20
I accidently installed two copies of intrepid . How do i get rid of one of them ?

---

### Post by cariboo on 2009-04-20
Install gparted, it is in the repositories. You can use Add/Remove Programs or Synaptic Package Manager to install it. Then go to System-->Administration-->Partition Editor and delete the partitions of the installation you don't want. Next open /boot/grub/menu.lst and remove the entry for the installation you just removed. Press Alt-F2 and type:

```
gksu gedit /boot/grub/menu.lst
```

To make absolutely sure you are removing the right menu entry, Open an Applications-->Accessories--> Terminal and type:

```
blkid
```

you should see something like this:

```
blkid
/dev/sda1: UUID="7451e251-cb09-4cda-b433-a2768d81affe" TYPE="ext4" 
/dev/sdb1: UUID="7c38c8a9-b0f3-4671-b72b-db3c210988e4" TYPE="ext4" 
/dev/sdb2: UUID="7c109a7f-b7fd-402d-aec5-0ee7dd30d37a" TYPE="ext4" 
/dev/sdb3: UUID="bc7912f5-a427-429d-98cd-7b97312c294d" TYPE="swap"
```

THe partition you just deleted should not show up in the list. Compare the uuid with the entries in /boot/grub/menu.lst, and delete the entries that don't have a blkid.

Jim

---

### Post by bobin on 2009-04-24
when i tried to delete it error came
Unable to delete /dev/sda5
Please unmount any logical partitions having a number higher than 5


when tried to do that: error unable to unmount/dev/sda7.
other partitions are also mounted on these mount points.


HELP

---

### Post by lisati on 2009-04-24
> **bobin said:**
> when i tried to delete it error came
Unable to delete /dev/sda5
Please unmount any logical partitions having a number higher than 5


when tried to do that: error unable to unmount/dev/sda7.
other partitions are also mounted on these mount points.


HELP

You might find it easier if you run the partition manager from the Live CD. If you get the error message while using the Live CD, you can right-click on your swap partition, and the click "swapoff" (depending on your system, this might have the effect of slowing things down slightly, but won't hurt your computer)
You can then "unmount" other partitions as required.

---

### Post by bobin on 2009-04-24
sorry for sounding so DUMB but ummmmmm how do go to the liveCD?

---

