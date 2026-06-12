---
title: "Access shared directory with Debian system in LAN"
date: 2007-08-02
forum: Networking &amp; Wireless
---

### Post by rockymaxsource on 2007-08-02
Hey list,

I installed nfs-common and nfs-kernel-server on my Debian Etch box. In the /etc/exports  and /etc/hosts I made the corresponding configurations. From Ubuntu's shell I install and started the nfs-common and created a directory /mnt/private. But mount rocky-desk:/home/lover/shareTest /mnt/private/ makes owner and group of the /mnt/private to nagios. The permission for that is 644. My user name for the Ubuntu box is not nagios. I do not even use root to change /mnt/private 's permission. Can any of you tell me how I can make the ubuntu box's /mnt/private directory with correct user & group so I can read and write the files stored on Debian Etch box please?

 Blessings,
 Rocky

---

### Post by kidders on 2007-08-03
Hi there,

What UID are you using to mount the NFS share, and what user does that map to on the box serving it?

---

