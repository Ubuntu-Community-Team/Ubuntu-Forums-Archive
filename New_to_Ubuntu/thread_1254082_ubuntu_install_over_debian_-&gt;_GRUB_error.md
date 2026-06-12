---
title: "ubuntu install over debian -&gt; GRUB error"
date: 2009-08-30
forum: New to Ubuntu
---

### Post by anatak on 2009-08-30
Hello,

I have a laptop with windows and debian installed.
GRUB 1.5 is the bootloader.

I wanted to install Ubuntu instead of debian.
here is what I did in the partition manager.
select debian partition
delete partition
create new partition (same size as debian minus 250 mb) for Ubuntu
create new swap partition 250 mb

continue install
everything went well up till the installation of GRUB there I got a fatal error saying it could not install.

Any help is greatly appreciated.
kind regards
anatak

---

### Post by colau on 2009-08-30
> **anatak said:**
> Hello,

I have a laptop with windows and debian installed.
GRUB 1.5 is the bootloader.

I wanted to install Ubuntu instead of debian.
here is what I did in the partition manager.
select debian partition
delete partition
create new partition (same size as debian minus 250 mb) for Ubuntu
create new swap partition 250 mb

continue install
everything went well up till the installation of GRUB there I got a fatal error saying it could not install.

Any help is greatly appreciated.
kind regards
anatak

Did you select formatting the partition?
What message did it show?

---

### Post by anatak on 2009-08-31
I didn't select formatting the partition
I thought that by installing over it it would be formatted by ubuntu automatically ?

Do I have to format the partition before I install ?

---

### Post by Liolikas on 2009-08-31
Just in case format everything and try again.

---

### Post by anatak on 2009-09-01
indeed
this time I formatted the debian partition and got no more problems
thank you.
anatak

---

