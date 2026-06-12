---
title: "Ive tried upgrading to 9.10(again)"
date: 2009-11-03
forum: New to Ubuntu
---

### Post by scottishbloke on 2009-11-03
And so far so good,its crashed when ive tried before but so far its not crashed this time,so im well chuffed,Just one query,im using ext3 and not grub 2.does this matter?or is them bebefits just for faster boot up?):P

---

### Post by ranch hand on 2009-11-03
I think that you should have gone with a clean install and ext4.  It is your box though.  What ever blows your skirt up.

---

### Post by alphacrucis2 on 2009-11-03
> **scottishbloke said:**
> And so far so good,its crashed when ive tried before but so far its not crashed this time,so im well chuffed,Just one query,im using ext3 and not grub 2.does this matter?or is them bebefits just for faster boot up?):P

You can always upgrade partitions from ext3 to ext4 using tune2fs and efsck. Has to be done with the partition unmounted. So you would have to boot from a live CD, or similar, if you want to change your root filesystem to ext4. Note that you don't get the full ext4 performance benefits for files that already existed when you do this. Sticking with grub should be ok as long as you are using the patched version that shipped with Jaunty. Older versions of grub can't boot from ext4 partitions.

---

### Post by philinux on 2009-11-03
> **scottishbloke said:**
> And so far so good,its crashed when ive tried before but so far its not crashed this time,so im well chuffed,Just one query,im using ext3 and not grub 2.does this matter?or is them bebefits just for faster boot up?):P

If it aint broke......

---

### Post by 3rdalbum on 2009-11-03
GRUB 2 is only needed if your partition is Ext4, because GRUB 0.9 can't see Ext4.

---

### Post by alphacrucis2 on 2009-11-03
> **3rdalbum said:**
> GRUB 2 is only needed if your partition is Ext4, because GRUB 0.9 can't see Ext4.

The version of grub shipped with jaunty was specifically patched to support ext4.

---

### Post by kansasnoob on 2009-11-03
> **alphacrucis2 said:**
> The version of grub shipped with jaunty was specifically patched to support ext4.

+1! Likewise with the version in Karmic's repos!

---

### Post by ranch hand on 2009-11-03
My grub-legacy on Hardy has no trouble booting ext4 OS'.

Can't see the files but sure can boot the suckers.

---

