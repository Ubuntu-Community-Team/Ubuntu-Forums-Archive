---
title: "nfs mounting, no write permission"
date: 2007-01-26
forum: Networking &amp; Wireless
---

### Post by phoenixy on 2007-01-26
Hi,

I'm setting up nfs access for my laptop. My server exports a directory with the (rw) option. My laptop mounts it using fstab, where the rw option is also explicitly defined

For some reason, I can read the mounted file system just fine, but I am getting permission denied when I tried to write to it.

My guess is that this has something to do with uid? I don't have NIS running. This is a home network, so I just want the server's file system to export to everyone. 

Any pointers will be appreciated

---

### Post by kidders on 2007-01-26
Hi there,

What account are you using to mount the share?

If you haven't specified one, chances are your system is using the root account ... in which case you'd probably have to export the share with the "no_root_squash" flag to stop root from being automatically downgraded to an unprivileged user, for security reasons.

---

### Post by phoenixy on 2007-01-26
wow, that was fast.

no_root_squash did the trick, thanks!

---

### Post by kidders on 2007-01-27
Yep... it'll do the trick alright, but whether it's smart is worth thinking about. Enabling unrestricted root access to an NFS share leaves you open to all manner of disasters!

How paranoid you want to be about this sort of thing is entirely a personal choice though.

---

