---
title: "storage partition in ubuntu?"
date: 2009-06-18
forum: New to Ubuntu
---

### Post by joe26 on 2009-06-18
i was wondering if i could make another partition so that i have a storage for ubuntu, but not IN the ubuntu partion / Swap, like when you install windows XP you can make new partition ( c ) and another (d ) then format d, and done, i am manly wondering when i make 2nd partition, what do i make it, ext 3, fat, or any other ones

---

### Post by Temposs on 2009-06-18
Yes, you can make another partition. If you're using ext3 on your main partition already, just make the second partition ext3 as well.

You should use GParted to make the partition, here:
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

You can make a LiveCD from that and edit your partitions on there. Alternatively, you can use the Partition Editor on your Ubuntu LiveCD to do the same thing(it's really the same program).

---

### Post by scorp123 on 2009-06-18
Search the package manager for a package called "gparted". Or use the shell and install it that way: ```
sudo apt-get update
sudo apt-get install gparted 
```

Once it's installed you can open it via:
[INDENT]System > Administration > Partition Editor[/INDENT]

You can manipulate partitions if they are currently not mounted and/or not part of your currently running Linux installation.

Do not use the "Partition Editor" on disks and filesystems that are currently a part of your running instance of Linux.

(It should complain if you do that ... but no guarantees here!! THINK twice before you mess with partitions, OK?)

If you want to manipulate partitions that are part of your currently running Linux then you should reboot and use a Live CD that can do this.

---

