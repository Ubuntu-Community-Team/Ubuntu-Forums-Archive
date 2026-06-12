---
title: "Making mount wait for NFS"
date: 2007-07-11
forum: Networking &amp; Wireless
---

### Post by bevis on 2007-07-11
I have NFS set up fine on a laptop, mounting drives on a server.
The fstab entry options are currently "rsize=8192,wsize=8192,rw,soft".
However, it seems that the NFS mounting on bootup happens in the background, such that the laptop boots up and logs the user on before the NFS mounts are ready.  This is a real problem - is there a way to stop it happening, ie not log on until the NFS mounts are ready?
There's a 'waitnfs.sh' script in (I think) /etc/rcS.d, and I tried putting a link in /etc/rc5.d, but to no avail.
I'm surprised that I can't find anything on this searching the forums!

---

