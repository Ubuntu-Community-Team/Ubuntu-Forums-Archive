---
title: "Where in the FS are the network shares mounted?"
date: 2008-05-31
forum: Networking &amp; Wireless
---

### Post by randysparks on 2008-05-31
If I connect to a windows machine via Samba using Nautilus, where in the file system is it mounted? I've checked /media and it doesn't appear to be there.

---

### Post by randysparks on 2008-05-31
> **randysparks said:**
> If I connect to a windows machine via Samba using Nautilus, where in the file system is it mounted? I've checked /media and it doesn't appear to be there.

I've solved it :)

Hardy uses the all-new gvfs, which means that things like samba mounts are created within the virtual file system and accessible to GNOME apps.

There's provision for sharing the mount using fuse, so that any other app can access it, and they are made accessible in ~/.gvfs. 

This applies not only to shared folders but should apply like digital cameras and USB memory sticks -- in theory, anything that gvfs mounts should be made available in .gvfs. But it looks like USB memory sticks, at least, are still mounting in the /media directory, rather than virtually. I understand that gvfs is still a work-in-progress so I wouldn't be surprised if this changed in the next version of Ubuntu and EVERYTHING that's mountable outside of root/swap end-up as gvfs.

---

