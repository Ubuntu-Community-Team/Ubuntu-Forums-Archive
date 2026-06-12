---
title: "Should I choose CIFS, NFS or AFP for a network drive?"
date: 2014-06-01
forum: Networking &amp; Wireless
---

### Post by leon.lain.delysid on 2014-06-01
Hello,
I bought a new network drive yesterday, and now I'm in the process of setting up a permanent mount.
I have an Ubuntu Desktop and an Ubuntu Server installation on this network. And they both need access to this drive.

I already managed to set up fstab to mount at boot time on both systems. Only,
```
mv folder FOLDER
```
doesn't work. That's because "folder" and "FOLDER" are the same name as far as this file system is concerned. On ext4 / Linux, you can absolutely do that no problem.
Now I'm thinking maybe this file system isn't the best one to use, if it can't handle such simple operations. (I mean, what will be next, huh?...) I've read CIFS is kind of Microsoft related, so maybe I want to stay away from that anyway.

Nautilus, however, mounts the drive using AFP. AFP is Apple's network file system protocol, which is much worse to me...

Now, I'm looking for a file system in the same spirit and performance as ext4. I'd like to use software that's open source, free and built on this same philosophy that what we are all here to adhere to. And that includes file systems and protocols.
I don't know what NFS is. Maybe this is what I'm looking for?

What I'd like to know is what are the differences between CIFS, NFS and AFP?
What are their open source status?
Is there any other file system? Especially one that's open source and built in a spirit of interoperability for as many systems as possible (or at least just Linux, since I don't use anything else).

Thank you for reading!

---

### Post by TheFu on 2014-06-01
NFS.  File permissions work just like locally mounted drives.  However, NFS should only be used over a secured LAN ... though I do recall the old days of read-only mounts to gatekeeper.dec.com to get access to all the GNU software in the world.

I like to use autofs with NFS mounts. Makes life easier in many situations. Mounts only happen when actually needed.

CIFS should only be used in cross-platform environments, but the base file system should still be linux-based (ext4, btrfs, jfs, xfs, ....). File names are case insensitive and real UNIX permissions just aren't possible.

Don't know anything about AFP - why use Apple stuff at all?

Oh ... and NFS is fast compared to other methods.  Be certain that uids/gids match across systems and that you explicitly export using NFSv4 or there can be security issues.  I like to block remote root exports too - so 'root' means nothing on a different machine.

---

### Post by leon.lain.delysid on 2014-06-05
Thanks for your answer! Much appreciated! ;)
So I set up NFS, which is indeed closer to Linux as I know it, and seems to be advertised as being faster and more reliable overall. Unfortunately, my drive doesn't support version 4, but only version 3 (which isn't all that bad at all). That's a bad choice on the constructor's behalf involving complete disregard of Linux-like client systems. (Which in the grand scheme of things is pretty funny since the drive runs on Debian... ^^''' )

Only, now, a question comes to mind. I don't have to authenticate. OK, so, now I get it, NFS just doesn't authenticate. But the default exports on the server read
```
/nfs *
```
What does * allow here? This looks very open. Does it just mean any IP address on my local network or does it mean the scary whole wide Internet has access to my drive as well?
My local network is fine, here. Every last person on the Internet is obviously not.
Now, I feel a little stupid asking such an obvious question, but let's just be that careful.

Concerning AFP, I didn't request for my machine to use it, Nautilus used it by itself. I just browsed the network using Nautilus and opening one shared folder mounted it as an AFP file system. Go figure. I guess the drive must implement this because it advertises working on Windows and Mac. But I don't know how Nautilus operates in choosing protocols for mounting externals file systems... We might never know...

---

### Post by TheFu on 2014-06-05
If you google "ubuntu nfs howto" - the top 3 results are what you need to learn.

---

