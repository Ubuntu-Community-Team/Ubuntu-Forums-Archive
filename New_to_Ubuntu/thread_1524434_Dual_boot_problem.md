---
title: "Dual boot problem"
date: 2010-07-05
forum: New to Ubuntu
---

### Post by msidhard on 2010-07-05
hi all,
       am using windows xp and ubuntu 9.1 in same hard disk. last time i re-installed the xp and tried to restore  grub in mbr through super grub disk likewise as i do when i am using ubuntu 6.06,8.04. but now the sgd failed to find any grub or linux partition in my hard disk. how to restore the grub back in the mbr  and have a  dual boot

---

### Post by yetiman64 on 2010-07-05
Could you check link #1 in my sig, and follow the guide to download and run the boot_info_script, then post the results back here (in code tags please). 

This will help in troubleshooting your boot issues.

---

### Post by warfacegod on 2010-07-05
Reinstalling GRUB2 isn't done quite the same way as GRUB Legacy.

Section #13 in the second link in yetiman64's sig. will give you the proper instructions for GRUB2 reinstallation. Normally, I'd post a link myself but I can't at the moment.

---

### Post by msidhard on 2010-07-05
thanks i will reply soon

---

### Post by yetiman64 on 2010-07-05
@warfacegod, hi. Is the super grub disk based on grub-legacy? (not familiar with it at all, hence the request for the boot_info_script output).

Edit: just "googled" and noted there is a new version based on grub2. Would be of interest to know which version of sgd you were using msidhard.

---

### Post by warfacegod on 2010-07-05
Getting the bootscript info posted is a good idea.

What I *think* happened was that the old method of reinstalling GRUB (as in Legacy, mention of 6.06 and 8.04) was used to repair GRUB2 (mention of 9.10 installed.

I'm pretty sure that getting the script posted will confirm that GRUB2 is totally absent from the system and reinstalling via section #13 of drs305's guide should be the key to fixing it.

---

