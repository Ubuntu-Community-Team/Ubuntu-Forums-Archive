---
title: "[SOLVED] AutoMount a PArtition"
date: 2009-01-02
forum: New to Ubuntu
---

### Post by joey-elijah on 2009-01-02
I've searched the forum but i can't seem to get an auto mount to work!

I want to automount an NTFS drive that is shared between two windows installs and, now, Ubuntu. (Only one accessing it at a time, obviously!) 

can anyone give me some advice?

---

### Post by jerome1232 on 2009-01-02
You can use ntfs-config, install it via synaptic.

Or you can manually create an fstab entry for it.

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by SuperSonic4 on 2009-01-02
ntfs-config is probably easiest for ntfs ```
sudo apt-get install ntfs-config
``` and then run it as root ```
gksu ntfs-config
``` and it should be detected and automounted. Otherwise you might have to edit your fstab

---

### Post by joey-elijah on 2009-01-02
awesome, it seems to have done the trick! many thanks!

---

