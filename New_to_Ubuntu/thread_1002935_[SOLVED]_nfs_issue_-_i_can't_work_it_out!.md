---
title: "[SOLVED] nfs issue - i can't work it out!"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by emarkd on 2008-12-05
Hello all.  I'm having trouble working out an nfs issue.  It's probably something simple that I'm overlooking.  Here's the setup:

On computer one I have two extra hard disks.  They're both truecrypted.  Disk one mounts at a ~/stuff directory and contains directories:

~/stuff
.....stuff1/
.....stuff2/
.....stuff3/
.....morestuff/

Then disk two mounts at the morestuff/ directory under ~/stuff.

All of this works fine on the computer they're plugged in to.  I can access the second disk through the directory nested on the first.  But I need to be able to access the entire /stuff tree on another computer, so I have this entry in my fstab on the second computer:

192.168.1.101:/home/me/stuff /home/me/stuff nfs rw,rsize=8192 0 0

This mostly works.  The mount works and I can access /home/me/stuff as well as stuff1/ stuff2/ etc from the second computer, but I can't access morestuff/ where the second disk is mounted.  It shows up as an empty directory.  Just as a test, I tried losing the nfs and using sshfs for the mount, but the same thing happens.  Any ideas?

I hope this makes sense.  If this isn't clear, please ask and I'll try to clear it all up.

Thanks for your help!
-Mark

---

### Post by cozmicharlie on 2008-12-05
I believe you will need to mount both disks via nfs even though disk 2 is mounted at ~stuff/morestuff.  Having nfs access to ~/stuff is not giving you access to ~/stuff/morestuff because it is a separate disk.  The problem is if you set up 2 nfs mounts they most likely will not show up in a single tree (try it - maybe it will I am not sure).  I am not sure if their is a way to do that with nfs.  If you want it to show up as a single volume and have access to both from 1 tree you could set up the 2 disks in a raid array or as a single lvm partition (a virtual partition spanning 2 disks).  Then the 2 disks essentially show up as 1 volume that you can mount via nfs.  A raid array also gives you the advantage of redundancy so if 1 disk fails you don't lose all your data.  Setting up raid is fairly easy in Ubuntu.

---

### Post by majickmann on 2008-12-05
cozmicharlie hit the nail on the head.  Never mount an nfs mount point to an exsisting nfs mount point.  Should be separate mount points.

Nothing else for me to say.  :-)

---

### Post by emarkd on 2008-12-08
Thanks guys!  lvm works great and is a much better solution than nesting the two filesystems.

---

### Post by cozmicharlie on 2008-12-08
Excellent - glad it worked out for you

---

