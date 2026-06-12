---
title: "Partitioning inside ubuntu?"
date: 2009-03-09
forum: New to Ubuntu
---

### Post by Gp. on 2009-03-09
Hi,
I'd like to resize/change my partitions inside Ubuntu.

What's good to use?
or is there only some kind of terminal command?

Thanks.

---

### Post by kanikilu on 2009-03-09
If you want to use a GUI, just use GParted (System > Administration > Partition Editor) or ```
gksudo gparted &
``` from the terminal. Just note that you cannot modify mounted partitions, so if you intend to resize the partition that Ubuntu is installed on, you'll need to do that from the Ubuntu Live CD or the GParted Live CD.

---

