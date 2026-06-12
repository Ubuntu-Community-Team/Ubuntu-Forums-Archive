---
title: "Triple booting"
date: 2011-08-08
forum: New to Ubuntu
---

### Post by neavynp on 2011-08-08
Would anyone know please how to triple boot a laptop with vista, ubuntu and fedora. Managed to damage my PBR last time I tried!:(

---

### Post by LowSky on 2011-08-08
PBR?? Pabst Blue Ribbon, lol...

install windows, then fedora then ubuntu... simple as that. ubuntu's grub usually finds other linux partitions just fine, if not you will need to update grub after the install.

---

### Post by oldfred on 2011-08-08
Some have suggested creating the partition(s) for Fedora first, so it does not use its default LVM and separate /boot. You can & should install Fedora's old grub to the PBR - Partition Boot Sector/Record. Of course if we drink too many PBR's the quality of help may go down a bit.;)

---

