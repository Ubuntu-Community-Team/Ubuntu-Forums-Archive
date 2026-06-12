---
title: "Mount share pdc with hardy customer"
date: 2008-05-18
forum: Networking &amp; Wireless
---

### Post by Elberton on 2008-05-18
Hi guys.
I have a lot of computer with ubuntu gutsy, and with the new hardy heron, i'll to upgrade it.
We have a server with samba pdc, and ldap.
So the windows xp pro customer has no problem to connect and to have the share.
With the last ubuntu 7.10 all user can logged and use his share with pam_mount.
We have different group with user. For exemple the group of studient, Admin, Teacher.
On all group they have a folder "Public" and "Share".
When i try to upgrade to the new ubuntu, users can connect with his password, but the share is not mount.
I see hardy use the new pam_mount.conf.xml. So i succeed to mount homes share of user. But the forder "public" and "share" don't want to be mount.
Nautilus say links is brake.
When i try to mount by hand all is ok.
Has somebody have some documentation for the new pam_mount.xml
I try man pam_mount but i don't find any information....
thank for you help

---

### Post by Fitz_the_gap on 2008-05-25
Hi,
You seem to be a few steps ahead, I cannot get pam_mount.conf.xml to mount anything. 
I have a windows 2003 domain to which I want to connect Ubuntu clients. I can currently validate user names and passwords against the domain controller but I am unable to mount network drives.
Previous versions of PAM_MOUNT used pam_mount.conf to achieve this but the latest version uses pam_mount.conf.xml instead.
Using this file I am unable to mount the drives.  
Can somebody please give me a working example of a complete pam_mount.con.xml file so that I might be able to see where I am going wrong.
Ta muchly.

---

