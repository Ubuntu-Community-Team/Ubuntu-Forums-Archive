---
title: "How to mount a writable Windows share"
date: 2008-02-12
forum: Networking &amp; Wireless
---

### Post by alsorrell on 2008-02-12
Using Ubuntu 6.06LTS trying to mount a share on a Windows XP domain-based computer as writable.
What I've done:
On my WinXP system (mypc), created the share named "temp" and given Everyone all permissions (full, Change, Read). File system on PC is NTFS.

On Ubuntu box, I downloaded latest smbfs package and installed.
Created mount : sudo mkdir /media/alspc-temp
Made mount point world read/write: sudo chmod 0777 /media/alspc-temp
dir of /media shows alspc-temp/ as drwxrwxrwx root:root
create a credentials file in home dir with appropriate  username= and password= lines

Mount the remote share using:
sudo mount -t smbfs //mypc/temp /media/alspc-temp \
-o "rw,credentials=$HOME/.smb_auth,fmask=664,dmask=775"

The share mounts - but if I look at Properties->permissions, it is 755 (drwxr-xr-x). And the mount point has been changed to the same permissions!

How do I get it so I can write to the share?? 
(note I also tried fmask=666,dmask=777 with no better results).

Thanks,
Al

---

