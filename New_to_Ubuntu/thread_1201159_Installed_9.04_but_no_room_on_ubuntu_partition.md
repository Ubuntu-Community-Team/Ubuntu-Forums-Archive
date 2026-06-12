---
title: "Installed 9.04 but no room on ubuntu partition"
date: 2009-06-30
forum: New to Ubuntu
---

### Post by skywalkrNCSU on 2009-06-30
I just installed 9.04 to have another run at trying to make ubuntu my primary OS.  When going through the installation it asks how you want to do the partition and I selected the first option of install it side by side with windows.  Problem is, it installed it with basically no room on the ubuntu partition.  Is there a way to alter the partition to give it more space from my windows partition?

Thanks

---

### Post by raymondh on 2009-06-30
> **skywalkrNCSU said:**
> I just installed 9.04 to have another run at trying to make ubuntu my primary OS.  When going through the installation it asks how you want to do the partition and I selected the first option of install it side by side with windows.  Problem is, it installed it with basically no room on the ubuntu partition.  Is there a way to alter the partition to give it more space from my windows partition?

Thanks

hope this helps

[http://ubuntuforums.org/showthread.php?t=1201159](http://ubuntuforums.org/showthread.php?t=1201159)

Some tips. 
**Back up files first**.  
**Defrag windows before resizing**.  
**On the link, pay attention to #2 (Resizing NTSF)**.

Depending on how you move ubuntu, and _just in case_ you lose GRUB (or booting gives you errors) ...

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Good luck.

EDIT : just out of curiosity, could you post the command outputs of both

sudo fdisk -l  (small L, not number 1)
df -h

---

