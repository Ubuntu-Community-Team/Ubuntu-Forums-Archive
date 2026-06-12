---
title: "Ecryptfs (Swap) question"
date: 2010-08-09
forum: New to Ubuntu
---

### Post by Rumpletumbler on 2010-08-09
Following this guide [http://bodhizazen.net/Tutorials/Ecryptfs/](http://bodhizazen.net/Tutorials/Ecryptfs/) I encrypted my swap and went to this part:

> 
A new entry for your encrypted swap is automatically generated in /etc/fstab ,  but unfortunately as of this writing ,the old entry is not removed and you must remove it manually  (or suffer error messages when you boot).


 Using any editor, edit fstab as root (gksu gedit /etc/fstab)
 The old swap starts with either UUID=xxx-yyy-zzz or /dev/sdxy, remove that line.
 The new swap is identified by /dev/mapper/cryptswap , keep this line.
 That's it, your swap is now encrypted and will mount automatically when you boot.


The UUID was commented out on the swap. The only other UUID was for ext4. 

So I rebooted and sure enough got the error that /dev/mapper/cryptswap wasn't ready or some such but it went away before I could get something to write it down with and the machine finished booting. 

I rebooted several more times and the error never came up again.

In the syslog I've got this > Adding <insertsize>k swap on /dev/mapper/cryptswap1  so I guess it's mounting. 

I don't think things just magically correct themselves though. What is likely going on here?

---

### Post by Rumpletumbler on 2010-08-21
Anyone know why this would mount on one reboot and not the next, etc? 

Thanks.

---

