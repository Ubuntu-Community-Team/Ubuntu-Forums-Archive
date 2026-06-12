---
title: "Permissions and owner in NTFS drives"
date: 2009-04-29
forum: New to Ubuntu
---

### Post by me.translucent on 2009-04-29
Every directory and every damn file in ntfs foramtted drives has root as the owner and 777 as the permission !! Any Idea how to change it ?

---

### Post by northern lights on 2009-04-29
As for the owner, edit [/etc/fstab]("http://www.tuxfiles.org/linuxhelp/fstab.html").

As for permissions, the octal code you've given only applies to *nix file systems. ntfs permissions cannot be set like that.

---

### Post by Didius Falco on 2009-04-29
This Help file will give you two ways to fix this, either by installing a GUI tool to do it for you or by walking you through how to manually edit your fstab file:

[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

I hope this helps...

---

