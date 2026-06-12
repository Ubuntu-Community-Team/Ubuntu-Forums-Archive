---
title: "Guide to network sharing..."
date: 2009-11-06
forum: New to Ubuntu
---

### Post by pablolie on 2009-11-06
Please? Why is this so hard?

I supposedly have both Samba and NFS services on this machine, yet I can make absolutely no sense of why it seems to be impossible to share anything on my simple home workgroup.

I am using 9.04 and this does not work between Ubuntu, XP or Windows 7. I have entered consistent worgroup info everywhere. The Windows stuff sees each other, the Ubuntu machines see each other, the twain don't meet in any way of shape. Same workgroup info.

Please - where is good reading material here? I must get this to work. It did work under 8.04.

---

### Post by Iowan on 2009-11-06
[Here]("http://ubuntuforums.org/showthread.php?t=1169149") is one to start with.

---

### Post by frenchn00b on 2009-11-22
> **pablolie said:**
> Please? Why is this so hard?

I supposedly have both Samba and NFS services on this machine, yet I can make absolutely no sense of why it seems to be impossible to share anything on my simple home workgroup.

I am using 9.04 and this does not work between Ubuntu, XP or Windows 7. I have entered consistent worgroup info everywhere. The Windows stuff sees each other, the Ubuntu machines see each other, the twain don't meet in any way of shape. Same workgroup info.

Please - where is good reading material here? I must get this to work. It did work under 8.04.

Forget all those nano and complicated things:

use my [installer]("http://yellowprotoss.ye.funpic.org/website/ubuntuinstallers/ubuntu_server_logins.jpg") : 
Here guys I made what I want for installers:

```
  cd /tmp 
wget http://yellowprotoss.ye.funpic.org/website/ubuntuinstallers/ubuntu-samba-nfs-installer.sh
cat ubuntu-samba-nfs-installer.sh  
# in case: sudo apt-get install xdialog
sudo su 
sh ubuntu-samba-nfs-installer.sh  
```
 
 
--
edit:
It is a beta version, and you have no warranties

---

