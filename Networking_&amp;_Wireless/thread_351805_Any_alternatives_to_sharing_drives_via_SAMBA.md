---
title: "Any alternatives to sharing drives via SAMBA?"
date: 2007-02-02
forum: Networking &amp; Wireless
---

### Post by barney_1 on 2007-02-02
Hi Folks,

I'm running a small home network and am having some trouble with network drives that are shared using samba.  I find that I often cannot: Download a file using firefox directly to a network drive, Edit mp3 tags using easy tag for files on a network drive.

Here is my setup:  I have a box that acts as Mythtv Frontend/Backend that has about 500 gigs of space over two drives in it.  I have several partitions on these drives and use this box also as a quasi-NAS device by sharing those partitions via SAMBA.  This is running Ubuntu Edgy.

My main computer is running Kubuntu Feisty (I know, not stable but I've had the same troubles with Edgy).  I only have a 40gb drive in this box so I have made folders and mounted my samba shares to those folders.

**Here's the question:**  Is there a better way to share these drives than samba?  I would like those network drives to have the same functionality of having those partitions in my main box.

If you think I just have a janked smb setup I'd be happy to post my fstab and some syslog error entries referencing smb.

Thanks!

---

### Post by kidders on 2007-02-02
Hi there,

> **barney_1 said:**
> I find that I often cannot: Download a file using firefox directly to a network drive, Edit mp3 tags using easy tag for files on a network drive.Every so often I see threads that mention problems like this. Can I take you up on your offer to post your /etc/fstab and samba logs? You never know ... it might be something easy to solve.

> **barney_1 said:**
> Is there a better way to share these drives than samba?There is no reason to use samba unless you need Windows compatibility ... in which case, it's the only *truly* reasonable option. Theoretically, I suppose, WebDAV or FTP would also work, but would be a bit daft. Hehe.

Your other mainstream options would be AFP and NFS. NFS is particularly nice in many cases, as you get good permissions support, and so on.

---

### Post by punx45 on 2007-02-02
if you want the shared directories to mount like local directories, i would suggest NFS.

...actually, now that I think of it, NFS is basically mounting over a network isn't it...

---

### Post by kidders on 2007-02-02
> **punx45 said:**
> ...actually, now that I think of it, NFS is basically mounting over a network isn't it...Yep. Most filesharing protocols (Samba, AFP, NFS, WebDAV, sshfs/fuse, and so on) work that way. Not being able to mount a network share would make accessing it a bit impractical, really.

---

### Post by barney_1 on 2007-02-03
Thanks for the advice.  I looked into NFS, got it up and running pretty easily.  I seems that has fixed the problems I was having.

Thanks!

Too bad XboxMediaCenter doesn't support NFS or I could scrap samba altogether

---

