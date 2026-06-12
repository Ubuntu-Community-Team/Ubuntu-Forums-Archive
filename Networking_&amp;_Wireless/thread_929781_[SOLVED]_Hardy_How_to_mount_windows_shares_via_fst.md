---
title: "[SOLVED] Hardy: How to mount windows shares via fstab?"
date: 2008-09-25
forum: Networking &amp; Wireless
---

### Post by Jamie Jackson on 2008-09-25
When I shutdown these days, I have a bunch of CIFS errors from network mounts, and during mounting, I get warnings. 

This style of mounting in fstab used to be error free. I think I need to modify it for newer kernels/hardy. Could you tell me what the modern version of the following is?

//serverA/d$ /media/myMounts/serverA/d smbfs credentials=/home/jamie/.smbcredentials.myDomainA,workgroup=myDomainA,uid=jamie 0 0

The errors look like: ```

mount error 127 = Key has expired
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)
```

---

### Post by Jamie Jackson on 2008-09-25
Never mind, this was a red herring during mounting, as I just had the password wrong. I'll post a more specific thread when I write down the errors I get on shutdown (the CIFS VFS errors).

---

### Post by Iowan on 2008-09-25
Although it's marked [SOLVED], I'll offer some suggestions in the form of a [link]("http://ubuntuforums.org/showthread.php?t=288534").

---

### Post by Jamie Jackson on 2008-09-26
> **Iowan said:**
> Although it's marked [SOLVED], I'll offer some suggestions in the form of a [link]("http://ubuntuforums.org/showthread.php?t=288534").

Good thread, thanks. I've bookmarked it.

---

