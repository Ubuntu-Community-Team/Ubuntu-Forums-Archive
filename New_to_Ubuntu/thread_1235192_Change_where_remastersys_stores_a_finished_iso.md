---
title: "Change where remastersys stores a finished iso"
date: 2009-08-08
forum: New to Ubuntu
---

### Post by C.A.G. on 2009-08-08
I have a Dell Mini 9 with an 8 gig ssd and 2 gigs of ram in Jaunty.  When I try to backup my system using Remastersys, I run out of room on my ssd.  Is it possible to save the iso to an sd card instead of to my hardrive? Thanks in advance!**C**

---

### Post by aysiu on 2009-08-10
Yes, it's possible.

At the Remastersys backup window, select **Modify**

Then for *Working Directory* pick /media/sdcard (or whatever the mount point is.

Then for *Files to exclude* exclude /media/sdcard (or whatever the mount point is.

---

### Post by C.A.G. on 2009-08-10
Thank you so much! I was under the wrong impression that the "working directory" was just a temporary place where Remastersys stored files.  Thanks for the help.

---

### Post by aysiu on 2009-08-10
> **C.A.G. said:**
> Thank you so much! I was under the wrong impression that the "working directory" was just a temporary place where Remastersys stored files.  Thanks for the help.
Well, actually, it is... but it is also where the .iso and .md5 files are dumped when the process is complete.

---

