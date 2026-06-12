---
title: "How to remove Ubuntu from a Vista box and restore Vista bootloader to original state"
date: 2009-05-19
forum: New to Ubuntu
---

### Post by swarup on 2009-05-19
I need to remove Jaunty from a laptop which originally came as a Vista machine, and I have since set up as a dual boot using GRUB i.e. Vista/Jaunty. Is there a way to safely remove Jaunty and also GRUB, and restore the Vista boot loader to its original condition?

---

### Post by louieb on 2009-05-19
lots of ways [IDBS Remove/Replace/Uninstal Grub]("http://www.users.bigpond.net.au/hermanzone/p18.htm") Good luck.

---

### Post by billgoldberg on 2009-05-19
> **swarup said:**
> I need to remove Jaunty from a laptop which originally came as a Vista machine, and I have since set up as a dual boot using GRUB i.e. Vista/Jaunty. Is there a way to safely remove Jaunty and also GRUB, and restore the Vista boot loader to its original condition?

Format the Ubunt partition and use the Vista repair cd to fix the boot issue.

---

### Post by swarup on 2009-05-19
Thanks to both of you for your tips.
@billgoldberg: I tried using the Vista repair cd once before in this situation, and it could not fix the boot problem-- at least, not if you just let it do its thing. It has an "auto repair" option. But that could not diagnose or fix the boot problem. See the thread I started on this at [http://ubuntuforums.org/showthread.php?t=1153560](http://ubuntuforums.org/showthread.php?t=1153560).

I found that if one has to break the boot and then fix it, the following does actually work perfectly well: 

> Boot up your Vista Recovery CD that you downloaded and do following in the recovery console:
```

bootrec /fixmbr
bootrec /fixboot

```
That will replace the MBR with the Vista boot loader. 

I was just wondering whether there was a way to do this cleanly, without ending up with a temporarily non-bootable computer that you have to fix the bootloader on as I detail here. I've done it, and it's easy enough to do-- I just wondered, as I say, whether there is a way to do things without first "breaking" the boot system and then having to fix it.

...Perhaps the link louieb has given contains some good tips in this regard. I'll take a look there now.

EDIT: Yes, it looks like louieb's link is the perfect find. Thank you! :p

---

