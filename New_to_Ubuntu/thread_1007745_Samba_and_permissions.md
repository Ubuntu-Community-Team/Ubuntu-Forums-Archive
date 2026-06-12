---
title: "Samba and permissions"
date: 2008-12-10
forum: New to Ubuntu
---

### Post by MalcolmR on 2008-12-10
Apologies up front if this is a stupid question but I have been using Windows for 15+ years and Ubuntu for 15 hours.

I am setting up a NAS system using Ubuntu 8.10 server (minimal install) and have managed to install Webmin and openssh (using putty on my Windows box).  The system comprises an OS drive and a pair of drives (Raid 1) for my data.  I have mounted the data drive as mnt/data01 and have folders within data01 for music, photos, etc.  I am now trying to use Samba to share these folders to my Windows machines.  My problem is with the permissions: my aim is to have some users with read/write access to these folders and other users (kids) with read only access.  So far all I have been able to do is give everyone either full or no access!

Using Webmin I have setup the permissions for data01 so that "user" and "group" have read, write and list permission but "other" only has read and list.  Ownership is set to nobody and nogroup.  These settings are the same for the music folder.

Again with Webmin, I have set the workgroup to match the name of the Windows workgroup and created a share named music for mnt/data01/music.  I have set the "read only users" to my username and the "read/write users" to another username (account names match those in Windows).

At this point both users can see the share but neither can create files from Windows.  However, if I set the permissions for data01 so that "other" has write permissions than both users can create files.  

Can anyone tell me where I am going wrong.

Thanks

---

### Post by cmnorton on 2008-12-11
It sounds like you'll have to do this with local users and groups.

You would have a bunch of users in the (for example) rwacc group, and the samba shares would belong to that group with group rwx permissions. You could have a bunch of less privileged users in the racc group, and those users would have rx permissions to that samba resource.

Don't forget to add your Windows users via smbpasswd.

---

