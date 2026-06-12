---
title: "[SOLVED] .smbcredentials not visible by fstab when moved into Intrepid's 'Private' di"
date: 2008-11-03
forum: Networking &amp; Wireless
---

### Post by tatsuno on 2008-11-03
Hi,

I wanted to take advantage of Intrepid's new 'Private' directory feature by moving my .smbcredentials file into it. The problem is that the Samba shares seem to be mounted before the Private directory, so the .smbcredentials file cannot be read at the time the Samba shares are supposed to mount.

Looking for different solutions, I tried to forget about credentials and use pam_mount instead of editing /etc/fstab, which sounds like a better alternative to me, but according to [https://wiki.ubuntu.com/MountWindowsSharesPermanently#Mount password protected network folders without credentials file using libpam_mount](https://wiki.ubuntu.com/MountWindowsSharesPermanently#Mount password protected network folders without credentials file using libpam_mount), you have to make sure "your username and password are the same on the Ubuntu machine and on the network drive", which is not the case, so I gave up this solution.

Could anybody please tell me either how to use pam_mount with different usernames on the network drive and local machine (preferably) or how to mount the Samba shares once the Private directory has been mounted?

Any feedback greatly appreciated.

---

### Post by tatsuno on 2008-11-04
Anybody, please?

---

### Post by tatsuno on 2008-11-07
I finally changed my local username to match that of the network drive and pam_mount worked.

---

### Post by theriesproject on 2009-07-02
I was having a similar issue with this. fstab was mounting a share at boot, and after upgrading to Jaunty, it no longer worked. A little research, and I discovered that the format of the .smbcredentials file changed from Intrepid to Jaunty. You now need to add = signs:
```

username=USER
password=PASSWORD
workgroup=WORKGROUP
```

My login name is already the same as the share's authentication name, so this might be a different issue.

See man mount.cifs for details.

---

