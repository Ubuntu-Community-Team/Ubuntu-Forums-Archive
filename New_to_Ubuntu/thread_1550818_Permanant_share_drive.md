---
title: "Permanant share drive"
date: 2010-08-11
forum: New to Ubuntu
---

### Post by ombhosle on 2010-08-11
i have partition on hard disk. I shared h drive. But share disappears on reboot. How to make permanent share which will not disappear on restart.

---

### Post by SpockVulcan on 2010-08-11
Its probably just not Mounted. Look in Computer (Places> Computer) it should be there.:popcorn:

---

### Post by Dsafire on 2010-08-11
Is it an NTFS Drive? If it is, use the NTFS Configuration Tool (under System --> Administration).

 I've found that I had to not just set the drive to mount at boot, but it has to have a manually specified mount point. When I didnt set a mount point, it looked like Ubuntu set one with a random character string name, which means it's in a "different" location every time you boot, which makes the share disappear.

Once I set the mount point it stayed present and shared.

---

### Post by ombhosle on 2010-08-12
:confused:My method of sharing
i go to propeties >share
Share name : local disk   (h:)
it gives following message
'net usershare' returned error 255: net usershare add: share name local disk   (h:) contains invalid characters (any of %<>*?|/\+=;:",)

so i change
Share name : local disk h
Then it establishes share.
I am changing name of the drive from (h:) to h
is this the reason share disappears on reboot

---

