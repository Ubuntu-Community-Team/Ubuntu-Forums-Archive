---
title: "How to make a grub partiton for dual booting"
date: 2010-11-13
forum: New to Ubuntu
---

### Post by Adrenaline Rampage on 2010-11-13
Hi!
I'm new to Ubuntu. I'm gonna start my new pc in about 1 week, and i want to dual boot Windows Server 2008 R2 (got it for free from Dreamspark), and Ubuntu 10.10. I used a dual boot setup on my old pentium 3 machine and i had problems with the bootloader when i had to install/reinstall one of the OS. I'd like to have a separate partition just for GRUB.

Can anyone guide me step by step in the creation of the partition / installing grub on that partition? Also where on my hdd should i make the partition (at the beginning/ end / anywhere else). What kind of partition shoud it be (ntfs/ext3/ext2)? Shoud i place other parts of the OS on separate paritions (if so, why)?

---

### Post by Adrenaline Rampage on 2010-11-14
Anyone?

---

### Post by jrev on 2010-11-14
Read the documentation first :
[https://help.ubuntu.com/10.04/installation-guide/i386/install-overview.html](https://help.ubuntu.com/10.04/installation-guide/i386/install-overview.html)

---

### Post by theozzlives on 2010-11-14
/boot (grub), /, /home, swap

or

/boot, Win System, drive C:, extended, /, /home, swap

---

