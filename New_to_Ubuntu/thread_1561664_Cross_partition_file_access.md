---
title: "Cross partition file access"
date: 2010-08-26
forum: New to Ubuntu
---

### Post by MontrealMike on 2010-08-26
I am planning to install Ubuntu this weekend.  It will share my Windows 7 PC in a separate partition with a dual-boot configuration.  The question is: will Ubuntu apps be able to access files in the Windows partition?  How about the reverse: will Windows 7 apps be able to access Ubuntu files?

Thanks for any help

---

### Post by ezsit on 2010-08-26
Ubuntu will have access through NTFS drivers to your Windows partition. Windows will not see Ubuntu. If you have enough space, setup a shared partition, do this in Windows and format the partition NTFS since that will work for both OSes.

Look here for install help. It should answer most any question about installation:

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

For help with dual booting Ubuntu and Windows:

[https://help.ubuntu.com/10.04/switching/C/dualboot.html](https://help.ubuntu.com/10.04/switching/C/dualboot.html)

---

### Post by MontrealMike on 2010-08-26
Thanks ezsit, that answers my question and removes my last doubt about going forward.

---

