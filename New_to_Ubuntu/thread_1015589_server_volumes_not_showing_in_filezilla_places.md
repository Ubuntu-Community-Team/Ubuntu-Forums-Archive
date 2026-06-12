---
title: "server volumes not showing in filezilla places"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by bobstovall on 2008-12-18
I am new to Ubuntu 8.10 and have a file system issue I can't figure out and can't find any info on.

I store files on a Mac OS X server. Both NFS and Windows services are turned on.

I've bookmarked shares and they show up in my "Places" menu. Most applications have no trouble locating files on the system. But, FileZilla doesn't show the Share in it's places dialog.

Does anyone have any idea why this is and what I can do about it?

Thanks,
Bob

---

### Post by Hospadar on 2008-12-19
I don't know why filezilla doesn't see your bookmarks, I suspect it's just not a thing that it does.  But I do know that on an osx machine shares are mounted in /Volumes/the_name_of_your_share (or /Volume?).  So if you point your filezilla at that you should see your shares.

---

### Post by bobstovall on 2008-12-19
Thanks, Hospadar.

I tried it but it didn't work. I also have noticed that GIMP won't read the server share unless it is mounted. Tried that with FileZilla - still no go. I installed gFTP, but I have the same problem there. :confused:

---

