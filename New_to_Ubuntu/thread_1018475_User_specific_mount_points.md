---
title: "User specific mount points"
date: 2008-12-22
forum: New to Ubuntu
---

### Post by geekyhawkes on 2008-12-22
HI;

can someone tell me how i can setup logon specific mount points in ubunutu please?  I have set my nas to mount in fstab but it seems to be doing it for all users.  

Thanks

---

### Post by geekyhawkes on 2008-12-22
Anyone??  Im guessing this should be done outside of fstab?

---

### Post by BDNiner on 2008-12-22
Adding the mount point to the fstab file will mount it for all users. I would just use permissions to prevent anyone besides yourself from reading the root of the NAS.
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

Check the section under Automatic mount at boot. You could setup a new group that only you are a member of that has ownership of the mount point of the NAS.

---

### Post by geekyhawkes on 2008-12-23
Thanks, as its only my home network not worried about permissions but i did want to try and auto mount my own documents folder when i log on without cluttering other peoples desktops.   Maybe il suggest this for future releases..

---

