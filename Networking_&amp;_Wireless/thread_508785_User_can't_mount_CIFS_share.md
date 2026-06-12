---
title: "User can't mount CIFS share"
date: 2007-07-24
forum: Networking &amp; Wireless
---

### Post by jonboy99 on 2007-07-24
***EDIT - SOLVED, SEE LAST POST***

Aargh, am pulling my hair out over this one.

I have mounted a NAS (synology 207) as a network share, using CIFS, fstab entry as follows:

```
//192.168.1.16/NETfolder	/home/jonboy99/netmount cifs user,username=admin,password=xxxxxx,iocharset=utf8,file_mode=0777,dir_mode=0777
```

I have followed the instructions in the CIFS manual to set uid on both /sbin/mount.cifs and /sbin/umount.cifs, and confirmed this has taken effect.

However, I can still only mount and unmount as root.  The annoying thing is, this was working fine, and then after a reboot it wouldn't, and i'm pretty sure i didn't change anything!

If I try and unmount through the gui I get:
'umount: only root can unmount //192.168.1.16/NETfolder from /home/jonboy99/netmount
Please check that the device is plugged correctly.'

And if I try and umount from the console I get the same:

umount: only root can unmount //192.168.1.16/NETfolder from /home/jonboy99/netmount


Help much appreciated while I have some hair left!

cheers
Jon

---

### Post by reckless2k2 on 2007-07-24
would you consider mounting via smbfs and attaching the sticky bit to smbmount and smbumount...or is it smbmnt..can't remember.

[http://www.mattvanstone.com/2006/06/automatically_mounting_smb_sha/](http://www.mattvanstone.com/2006/06/automatically_mounting_smb_sha/)

---

### Post by jonboy99 on 2007-07-24
Have tried samba, and it's appallingly slow and keeps crashing the system, but the mounting bit was fine.  CIFS ismuch quicker and more stable for me so I want to stick with it.

---

### Post by jonboy99 on 2007-07-24
OK, don't waste any more thought on this - had a system screwup somehow, not sure what I did.  My mount point had somehow become owned by root, and even when unmounted it was still mounted somehow.  After rebooting it was owned by me again despite me not changing anything, and I could mount as normal. 
Whether this was caused by booting with an fstab that didn't include the user option, and this somehow became stuck I don't know, but sorted now.

---

### Post by reckless2k2 on 2007-07-27
i know a day late and a dollar short but i came across this and thought of this post:

[http://www.jejik.com/articles/2007/07/automatically_mounting_and_unmounting_samba_windows_shares_with_cifs/](http://www.jejik.com/articles/2007/07/automatically_mounting_and_unmounting_samba_windows_shares_with_cifs/)

seems like a good how to.

---

