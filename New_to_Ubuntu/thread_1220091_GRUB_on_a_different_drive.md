---
title: "GRUB on a different drive"
date: 2009-07-22
forum: New to Ubuntu
---

### Post by julian.irwin on 2009-07-22
I just installed ubuntu on an external drive and now my system wont boot without the external. I already had ubuntu and Vista on the internal, so GRUB is there too. I just need to know how to make my system use the GRUB on the internal hard drive instead of GRUB on the external. 

(I already changed the BIOS boot order around a bunch.)

---

### Post by DGortze380 on 2009-07-22
> **julian.irwin said:**
> I just installed ubuntu on an external drive and now my system wont boot without the external. I already had ubuntu and Vista on the internal, so GRUB is there too. I just need to know how to make my system use the GRUB on the internal hard drive instead of GRUB on the external. 

(I already changed the BIOS boot order around a bunch.)

You'll need to add an entry in menu.lst on the internal drive for the external. You'll also want to delete grub from the mbr on the external.

---

### Post by roccivic on 2009-07-22
Open a terminal and run:
```
grub
```
then in the grub shell run:
```
root (hd0,0)
setup (hd0,0)
```
Obviously change "(hd0,0)" to match your Ubuntu partition containing "/boot/grub/" on your internal drive.

Close everything, reboot and enjoy.

---

