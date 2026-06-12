---
title: "NFS Shares mounted twice on client (as version 3 and version 4)"
date: 2014-01-14
forum: Networking &amp; Wireless
---

### Post by cscj01 on 2014-01-14
I am running Ubuntu 12.04 on 2 PCs on a home network.  My NFS shares are defined as Version 3 shares and are mounted on the client via FSTAB.  Occasionally they will disappear (by disappear I mean that I can browse to their mount point on the client with Nautilus and it shows no files or folders).  Usually I can issue a mount command for that share via a terminal session and things will reappear.  Today I could not get one of the shares remounted and got the message that it was already mounted or busy.  I then issued a mount command in the terminal session and saw that my shares were mounted twice; once as version 3 shares and once as version 4 shares.  Does anyone have any idea why this would happen?

---

### Post by TheFu on 2014-01-15
If you don't use the  **mount -o remount** command, then you are requested dual mounts. With wired connections on stable networks, the mounts really shouldn't disappear unless the drives spin down or one of the machines "sleeps."  Have you considered using "soft" mounts or autofs?

The great thing about autofs is that mounts happen only when needed, so system resources are only used as needed. I think it handles drive spindown cleaner too.

Usually when I reply, a few really smart people will chime in to correct whatever I got wrong. ;)  Let's hope that works again.

---

### Post by cscj01 on 2014-01-17
If I understand autofs for nfs correctly, I need to do the following on my client:
[LIST=1]
[*]install autofs if not installed;
[*]create an /etc/auto.master file with my mount point (in my case /mnt);
[*]create an /etc/auto.nfs file with my shares defined as in /etc/fstab;
[*]unmount my static nfs shares and comment them out from /etc/fstab;
[*]Reload /etc/init.d/autofs with 'sudo reload autofs'
[*]
[/LIST]
I presume this makes sense.

---

### Post by TheFu on 2014-01-17
Seems correct to me.  I wouldn't use /mnt, but I consider that area for temporary mounts or for use under emergency situations.  There are many options for the auto.nfs mount points. Wouldn't hurt to read about the "soft" option and to decide if you want the security risk of allowing setuid root programs to be run from other storage or not.  Also, if NFSv4 is being used, credentials will need to be included - usually it is best to use an external, locked-down, file for that.

Having the old mount information in the fstab file is a good reminder.

---

