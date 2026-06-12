---
title: "samba maximum 2GB"
date: 2007-01-27
forum: Networking &amp; Wireless
---

### Post by matt91 on 2007-01-27
have samba share mounted through fstab with smbfs. i cannot transfer files bigger than 2gb and nautilus restarts when i do. i have changed smbfs to cifs in my fstab which works but get warnings when i remount, these warnings are:
> 
root@LINUX2:~# mount -a
WARNING: 'dmask' not expressed in octal.
WARNING: CIFS mount option 'dmask' is deprecated. Use 'dir_mode' instead.
WARNING: 'fmask' not expressed in octal.
WARNING: CIFS mount option 'fmask' is deprecated. Use 'file_mode' instead.


does this matter?

---

### Post by GrammatonCleric on 2007-01-27
What version of samba are you using?  Can you post your fstab and possibly your smb.conf form the the server? Are you running this in any kind of virtual environment (i.e. VMWare)? Are both machines linux or is one a Windows box?

-GC

---

### Post by Kjella on 2008-01-19
I just had the same problem and found the solution on google, so adding it to this thread as well. Add the mount option "lfs" to the fstab, and it will work. That large file support isn't on by default is a WTF in my opinion, but I assume they have their reasons.

---

### Post by HermanAB on 2008-01-19
Note that smbfs is deprecated and shout not be used.

You should use cifs instead and of course since it is different, you got to read the man page for the gory details.

Cheers,

Herman

---

