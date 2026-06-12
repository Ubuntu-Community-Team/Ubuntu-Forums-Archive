---
title: "ubuntu wont open - cannot mount swap"
date: 2010-03-18
forum: New to Ubuntu
---

### Post by infestor on 2010-03-18
ubuntu cannot mount swap anymore thus wont open!
how can i fix this?

---

### Post by spiderbatdad on 2010-03-18
you can run the live cd, and look at fdisk -l to locate the swap partition.
cd into the ubuntu file system...something like cd /media Run ls to see what directories are there.

You'll need to use ls to determine the directories. Ultimately you'll edit the file /etc/fstab  in the /media/* directory and you can use /dev/sda*, where * is actually the location of the swap partition.

If you need more help, boot the live cd and become root in the terminal with
sudo -i then run fdisk -l and post the results here. Also cd /media and then ls. Post those results.

---

### Post by infestor on 2010-04-15
configuration of grub2 is really tiresome

---

