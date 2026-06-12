---
title: "/media folder contains extra cdroms"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by klemperal on 2009-01-09
After I installed Ubuntu this last time my /media folder contains 4 cdroms (cdrom, dcrom0, cdrom1 & cdrom2) when I only have 1 cdrom installed.  When I was running the AMD64 version of Ubuntu I don't remember having this issue.  Please let me know what you think the problem is and how I might go about trying to fix it.

Thanks in advance.

---

### Post by jpkotta on 2009-01-10
It shouldn't be a problem.  You will probably always have 2: cdrom and cdrom0.  cdrom is a link to cdrom0. as is /cdrom.
```
ls -l /media
```

You can always delete the extra ones.  
```
sudo rmdir /media/cdrom[1-9]
```

---

### Post by billgoldberg on 2009-01-10
> **klemperal said:**
> After I installed Ubuntu this last time my /media folder contains 4 cdroms (cdrom, dcrom0, cdrom1 & cdrom2) when I only have 1 cdrom installed.  When I was running the AMD64 version of Ubuntu I don't remember having this issue.  Please let me know what you think the problem is and how I might go about trying to fix it.

Thanks in advance.

Nothing to worry about, those are just mount points.

I have 2 cdrom mount points in /media on my eeepc and it doesn't even have a cd rom drive.

If you want you can delete those, but why bother?

---

### Post by klemperal on 2009-01-10
Thanks for the replies.  The reason I was wondering about this is because certain programs in wine weren't detecting my cdrom properly.  I wasn't sure if it was a problem with wine or Ubuntu.

---

