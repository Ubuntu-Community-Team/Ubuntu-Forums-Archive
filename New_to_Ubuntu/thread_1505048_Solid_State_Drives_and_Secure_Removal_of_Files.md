---
title: "Solid State Drives and Secure Removal of Files"
date: 2010-06-08
forum: New to Ubuntu
---

### Post by sunshinecorp on 2010-06-08
I'll finally replace my netbook's sluggish hard drive with an OCZ Vertex2 solid state one. I was wondering... since the writing on a solid state device is basically random, do shred, srm, sfill etc. work on it as they should or is it futile to try and wipe a file from a solid state device (in other words, do I have to do a full free space wipe to make sure sensitive data is really gone)?

---

### Post by bumanie on 2010-06-08
Basically, if you use trim to keep the deleted NAND memory free for the next write time, any previous data that was deleted should be virtually unrecoverable. [Look here]("http://techgage.com/article/too_trim_when_ssd_data_recovery_is_impossible/"). Those other commands you mentioned should be obsolete if you use trim on your ssd. Trim is supported in linux, you have to make sure the firmware of your ssd is updated for trim.

---

### Post by mlinder on 2010-06-08
TRIM should take care of SSD file 'security' issues for you.

/edit: beat me to it.

---

### Post by sunshinecorp on 2010-06-08
Thanks. So in other words, TRIM is supported out-of-the-box in Ubuntu 10.04? The specifications of the OCZ drive mention native TRIM support.

---

### Post by bumanie on 2010-06-08
I don't think automatic trim will be included until 10.10 - or use a kernel version 2.6.33 or above. Apparently automatic trim will only work on ext4. I'm not sure what you do in the meantime - have seen comments about hdparm, but don't have an ssd myself, so have only got 'general' knowledge about ssd drives.

---

### Post by sunshinecorp on 2010-06-08
Hm. So this is where it gets confusing. :confused:

Could anyone help with this? How would I enable TRIM support in Ubuntu 10.04 for my OCZ Vertex 2 solid state drive? I have no idea how to use hdparm, by the way...

---

### Post by mlinder on 2010-06-08
Apparently does not work (yet).

[http://ubuntuforums.org/showthread.php?t=1432194](http://ubuntuforums.org/showthread.php?t=1432194)

---

### Post by sunshinecorp on 2010-06-08
All your links have been extremely informational and helpful! I know have an understanding of TRIM and its support in linux kernels... Does anyone know of a way to track when/if TRIM support will be backported into 10.04? Is there a tracker link or something? Mainline kernels, as far as I can tell, aren't an option for me since they don't include dev tweaks for Lucid or support for restricted drivers.

*** EDIT ***

I found a way to track availability of TRIM support in 10.04, I think. Subscribe to [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/571476](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/571476) via Launchpad.

This, however, also leads me back to asking my first question until TRIM is sorted out in Ubuntu 10.04. Is wiping a file using shred, srm or wipe futile on a solid state drive? Do I accomplish anything by wiping the free space with sfill or similar?

*** EDIT ***

---

