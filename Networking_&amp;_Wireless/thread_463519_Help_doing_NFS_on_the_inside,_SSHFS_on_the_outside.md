---
title: "Help doing NFS on the inside, SSHFS on the outside"
date: 2007-06-03
forum: Networking &amp; Wireless
---

### Post by KjetilK on 2007-06-03
Hi all,

I have a fileserver at home with an NFS server running (it has a SAMBA server running too). On my new laptop, if I'm on the LAN, I'd like to mount the NFS, but if I'm on the outside, I'd like to use SSHFS to mount it. I can do both, of course, they are trivial. 

However, I'd like to make it as transparent as possible, if possible add another line (with "noauto") to /etc/fstab, so that when I feel like it, I can mount it from the command line, or click on it in Konqi. 

And that's the part I don't know how should be done... Anybody else done something similar?

---

### Post by kidders on 2007-06-04
Hi there,

> **KjetilK said:**
> I'd like to make it as transparent as possible, if possible add another line (with "noauto") to /etc/fstabThat's what I would do, I suppose. Then, you might like to create a little script that guesses & manually mounts the right share, depending on where you happen to be. If you arranged it so both shares got mounted in the same place (eg /media/MyStuff), you'd wind up with something reasonably transparent.

[[SIZE=1][COLOR=Silver]UAResolved[/COLOR][/SIZE]]("http://ubuntuforums.org/showthread.php?t=377083")

---

