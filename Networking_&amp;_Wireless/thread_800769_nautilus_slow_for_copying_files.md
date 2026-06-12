---
title: "nautilus slow for copying files"
date: 2008-05-20
forum: Networking &amp; Wireless
---

### Post by SpaceTeddy on 2008-05-20
Hi Folks, 

i've been wondering why nautilus is slow when copying files to network shares. For example, if i copy a file to my server via ssh/sftp through nautlius i usually cap around 700K (which is way slow). If i connect via the commandline through sftp and do the same copy with the same file i usually get 2-3 Megs a second (which is normal since this is a wifi and we have a LOT of interference. 

if if i conect via cable, nautilus will cap at 2,7 Megs a second, while sftp will go for about 9,5 Megs (100Mbit ethernet).

So anyone got any idea why this is so slow ?

---

### Post by jetsam on 2008-05-20
> So anyone got any idea why this is so slow ?

Some idea, albeit vague.

Nautilus uses an extra abstraction layer to access network file systems.  Before Hardy, this was called gnome-vfs.  With Hardy, gnome-vfs is being replaced by gvfs, an updated gnome-vfs that works with the fuse user-space filesystem.  

I've always understood this performance difference as just the extra overhead from this abstraction layer.  

It's not quite the same test, but I had similar speed results to yours when I  compared cifs mounted samba shares to gnome-vfs samba shares in post #2 of this [thread]("http://ubuntuforums.org/showthread.php?t=635255").  I just now tried to repeat this test with scp vs. gnomevfs-copy, but I can't figure out how to get it to not ask for a password and mess up the time results.

---

### Post by SpaceTeddy on 2008-05-20
thanks for the explanation. This is another reason to switch back to gutsy, i guess, since the old gnome-vfs does not have this problem.

One thing strikes me odd tho. Since gnome-fs uses fuse, i would think that if i use the commands sshfs (which ultimativly uses fuse) to mount a share, i still get double the speed by going via sshfs than going via gvfs... although they both use fuse ???

where is that huge performance drop comming from ? half the speed for what... a gui ? very odd...

---

### Post by jetsam on 2008-05-20
I just found this bug report in the gnome bug tracker:
[http://bugzilla.gnome.org/show_bug.cgi?id=532951]("http://bugzilla.gnome.org/show_bug.cgi?id=532951")

There seem to be a lot of gvfs related issues.  Other than a test partition, I may delay upgrading myself until 8.04.1.

---

