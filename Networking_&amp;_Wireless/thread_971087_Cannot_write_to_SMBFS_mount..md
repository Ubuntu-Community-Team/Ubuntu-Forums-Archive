---
title: "Cannot write to SMBFS mount."
date: 2008-11-04
forum: Networking &amp; Wireless
---

### Post by zackf on 2008-11-04
I am using something called andLinux on my Vista installation which uses ubuntu 7.10 as it's OS (it's a pretty cool thing). I have mounted a shared folder that I mount like this:

mount -t smbfs -o credentials=/etc/smbpasswd,iocharset=iso8859-1,codepage=cp437,
fmask=775,dmask=775,gid=1002 //windows-host/andLinux /mnt/win

(I am part of a samba group whihc is 1002).

The permissions on /mnt/win are drwxrwxrwx so I don't think that's issue. Does anyone have a suggestion? If you need more info please let me know!

---

### Post by cariboo on 2008-11-04
What about the permissions of the directory that you are trying o write to. Just because you have world read/write set on the share, you also have to have the same permissions on the directories within the share.

Jim

---

### Post by zackf on 2008-11-04
Hi Jim,

Thanks for suggestion, the files within also have the same permissions. I'm just in the testing phase right now so there's only a couple text files. I can see things within that directory, I just can't write it to it, so it would seem to me that maybe I'm mounting it wrong?

---

