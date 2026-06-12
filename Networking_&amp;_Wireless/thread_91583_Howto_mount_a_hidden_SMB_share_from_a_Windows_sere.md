---
title: "Howto: mount a hidden SMB share from a Windows serer"
date: 2005-11-17
forum: Networking &amp; Wireless
---

### Post by Hypatia2 on 2005-11-17
Howdy,
I'm documenting this because it might help someone else.
I wanted to be able to mount a hidden share as a normal user when needed by supplying a password at mount time. To do this, I had to add to my fstab:
> //*10.1.2.3*/*shareName$* /mnt/*winUser* smbfs rw,user,noauto,username=*winDomain*\*winUser*   0   0

I then had to make the smbmnt  command SUID:
> sudo chmod +s /usr/bin/smbmnt
And finally, make the mount point owned by the user:
> sudo chown * linUser * /mnt/*winUser*

Now, when I log in as *linUser*, I use the command:> mount /mnt/*winUser* and enter my windows password to access the windows share.

---

