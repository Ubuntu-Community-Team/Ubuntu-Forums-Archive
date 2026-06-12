---
title: "880515 - map network drive"
date: 2009-08-05
forum: New to Ubuntu
---

### Post by hamidi on 2009-08-05
hi
i've been a Windows user always and don't know how to map network drives. i could connect and see the Windows shares in Ubuntu, but how can i mount an SMB share in the Ubuntu environment?

---

### Post by BDNiner on 2009-08-05
If you mean permanently mount it so that it is mounted when you boot the computer you would have to edit fstab file.

---

### Post by hamidi on 2009-08-05
yeah, i mean that.
1. where is fstab? where is it located?
2. i found that since the file system is of like smb, i have to use smbmount. am i right? if so, do i have still to put it in fstab?
3. is it safe to let ubuntu make changed to an NTFS file system? it's another question, because in the case above the linux doesn't access directly to the NTFS file system and so it's safe to let it ask Windows networkly to do it. i just like to know whether it's safe in case of future use.
4. i may see the shared file system by using smb://... in the location address bar. may i use a Windows share directly without having to mount it somewhere?

---

### Post by BDNiner on 2009-08-05
1. fstab is located in /etc/
2. you can use smbmount to mount the dive. The reason you add settings to /etc/fstab is so that you can mount the share when your computer boots up
3. I don't really understand what you are asking. Ubuntu can access an NTFS share on another computer without causing complications.
4. When you connect to a window share using smb://... is is automatically mounted and appears in the places menu. But that is only for the current session, when you restart the computer the share will no longer be mounted.

---

### Post by BDNiner on 2009-08-05
This is the guide that I used to mount my shares using /etc/fstab

[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

be sure to read the entire thing before attempting to make any changes.

---

