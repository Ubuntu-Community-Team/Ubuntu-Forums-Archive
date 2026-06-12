---
title: "Adding an ext. HDD to Ubuntu File Server"
date: 2010-09-26
forum: New to Ubuntu
---

### Post by Randy Wells on 2010-09-26
I just built a Ubuntu File Server.  Works Great!  Win7 and XP machines on my network see it just fine!  Whoo...Hooo.. Now I want to add more storage.  

In a perfect world I'd add a SATA card to the old clunker and do a RAID 5.  But since I'm, (1)retired, (2)short on the funds to lay out for 3 1TB SATA drive plus controller, and (3)somewhat rusty with the Linux(Unix)command line, I want to pop on an external HDD for the time being.

I had some UNIX/Linux experience when I was actively involved in the IT business (40 years of involved).  Needless my command line expertise is weak now at best.  It's coming back slowly but surely.

So... What's the best way to add an ext HDD, mount it, and configure the system to use it for my Samba shares?

Thanks!!
Randy Wells
](*,)

---

### Post by robsoles on 2010-09-27
Welcome to UF Randy.

Maybe just a refresher on /etc/fstab is all it will take for you: [How to fstab](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by jtarin on 2010-09-27
If it's USB it's essentialy a done deal. Plug it in and boot up. It should be on your desktop if it has a filesystem formatted on it. I have a 1TB external and it's formatted  and partitioned as NTFS and it auto mounts. If yours doesn't its best then to add the blkid entries to your /etc/fstab as suggested above.

---

### Post by Randy Wells on 2010-09-27
> **robsoles said:**
> Welcome to UF Randy.

Maybe just a refresher on /etc/fstab is all it will take for you: [How to fstab](http://ubuntuforums.org/showthread.php?t=283131)
Thanks robsoles,  I can always use a refresher on just about anything UNIX/LINUX.  fstabs it is!

Randy

---

### Post by Randy Wells on 2010-09-27
> **jtarin said:**
> If it's USB it's essentialy a done deal. Plug it in and boot up. It should be on your desktop if it has a filesystem formatted on it. I have a 1TB external and it's formatted  and partitioned as NTFS and it auto mounts. If yours doesn't its best then to add the blkid entries to your /etc/fstab as suggested above.
jtarin, thanks for the info.  Since I'm tryin' to stay away from the GUI desktop (mainly to force myself back to using the command line effectively), I'm not sure how things will work.  I haven't gotten the external HDD yet (remember... broke and retired).  If it comes unformated, I'll hang it on a Windows machine and format it with NTFS.

Thanks for the info and I appreciate the help!!

Randy

---

