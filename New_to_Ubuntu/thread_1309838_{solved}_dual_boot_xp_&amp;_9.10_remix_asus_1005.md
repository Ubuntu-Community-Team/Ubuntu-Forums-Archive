---
title: "{solved} dual boot xp &amp; 9.10 remix asus 1005"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by frankelr on 2009-11-01
Tried to install 9.10 remix on newish asus 1005. Could not do dual install because Asus already used all four primary partitions. The standard installer won't install, deleted the drive D: partition, now I could get an ext3 partition, but there was still no room for the swap partition,  Finally had to delete the drive D: partition and in windows turn its space into an Extended partition, now the auto installer will split the former drive d: space in half and format the last half as ext4 + swap.  I really did not want to use ext4 but after the first battle I gave up.  Perhaps someone can offer a better solution for asus 1005 owners.

---

