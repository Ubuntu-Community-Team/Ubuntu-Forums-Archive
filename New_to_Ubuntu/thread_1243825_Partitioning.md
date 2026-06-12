---
title: "Partitioning"
date: 2009-08-18
forum: New to Ubuntu
---

### Post by kc9jse on 2009-08-18
I have been running a duel boot on this laptop and am ready to do away with windows. I really need the hd space. I have installed Gparted and think I'm ready. Looking for any advice before I proceed. Do I just format the ntfs partition to ext3? Will this machine boot normally into Ubuntu then? Help!

Thanks,
Al

---

### Post by LewRockwell on 2009-08-18
> **kc9jse said:**
> I have been running a duel boot on this laptop and am ready to do away with windows. I really need the hd space. I have installed Gparted and think I'm ready. Looking for any advice before I proceed. Do I just format the ntfs partition to ext3? Will this machine boot normally into Ubuntu then? Help!

Thanks,
Al

You will need to run the partition editor from the LiveCD to perform adjustments on your hard drive

If you are already dual-booting then you've already got the grub in your master boot record and the rest of the bootloader is located at /boot/grub/menu.lst in your ubuntu partition so you are good there also.

.

---

### Post by kc9jse on 2009-08-18
> **LewRockwell said:**
> You will need to run the partition editor from the LiveCD to perform adjustments on your hard drive

If you are already dual-booting then you've already got the grub in your master boot record and the rest of the bootloader is located at /boot/grub/menu.lst in your ubuntu partition so you are good there also.

.


Is the Live CD the cd that I burned after downloading the iso? If so, can you explain how I would do that. I really want to make sure I don't loose anything that I have in Ubuntu already. 

Thanks,
Al

---

