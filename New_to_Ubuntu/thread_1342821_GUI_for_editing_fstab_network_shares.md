---
title: "GUI for editing fstab network shares"
date: 2009-12-01
forum: New to Ubuntu
---

### Post by Matt26 on 2009-12-01
is there a GUI that supports auto mounting network NTFS shares in ubuntu 9.10?

i know that NTFS Configuration Tool and pysdm can be used for local NTFS drives, but does either support network shares as well?

if not, is there a GUI available that does support network shares?

thanks.

---

### Post by ukripper on 2009-12-01
for samba - [http://ubuntuguide.net/createmodifydelete-samba-shares-with-system-config-sambagui-in-ubuntu-linux](http://ubuntuguide.net/createmodifydelete-samba-shares-with-system-config-sambagui-in-ubuntu-linux)

---

### Post by Matt26 on 2009-12-01
> **ukripper said:**
> for samba - [http://ubuntuguide.net/createmodifydelete-samba-shares-with-system-config-sambagui-in-ubuntu-linux](http://ubuntuguide.net/createmodifydelete-samba-shares-with-system-config-sambagui-in-ubuntu-linux)

thanks for the suggestion- does this tool support both SMB and CIFS?

---

### Post by ukripper on 2009-12-01
> **Matt26 said:**
> thanks for the suggestion- does this tool support both SMB and CIFS?

Practically smb or cifs is same thing. so answer is yes!

More info - [http://msdn.microsoft.com/en-us/library/aa365233%28VS.85%29.aspx](http://msdn.microsoft.com/en-us/library/aa365233%28VS.85%29.aspx)

---

### Post by Matt26 on 2009-12-04
i installed this tool, but from what i can see it appears to only support mounting local shares that are on the PC, and what i'm looking for is a GUI for auto-mounting NTFS shares that reside on a remote windows PC.

if i'm correct here, is there a GUI for auto-mounting NTFS shares that are located on a remote PC?

---

### Post by ukripper on 2009-12-04
> **Matt26 said:**
> i installed this tool, but from what i can see it appears to be the opposite of what i'm looking for, which is a GUI for auto-mounting NTFS shares that reside on a remote windows PC.

Ok in that case this will answer everything you want know about auto-mounting through GUI or without [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by Matt26 on 2009-12-04
> **ukripper said:**
> Ok in that case this will answer everything you want know about auto-mounting through GUI or without [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

that thread is actually where i started before i posted this one... do you know if the Pysdm tool supports remote NTFS shares?

---

