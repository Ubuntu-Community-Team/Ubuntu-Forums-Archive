---
title: "Using Simple Backup Suite if Hard Disk fails."
date: 2011-01-09
forum: New to Ubuntu
---

### Post by OldBoy44 on 2011-01-09
Kindly excuse my lack of knowledge -

I will be installing Ubuntu 10.04 soon and have been reading about using Simple Backup Suite to do my backups. I understand the backups are stored at /var/backup. In the event of a disk failure then I assume that information would be lost. I have several questions -

1. Can a usb flash drive be used to copy the backup file at the time of backup?

2. Can backup be made directly to an external flash drive?

3. What is a practical alternative?

4. I do not expect that my files would ever be very large. 

Thanks in advance for any help.  :)

---

### Post by Zimmer on 2011-01-09
practical alternative is rsync.

Back up what you want to any locations internal or external.

---

### Post by OldBoy44 on 2011-01-09
Thank you very much Zimmer,

rsync may be just what I need!

Cheers,  :D

---

### Post by Zill on 2011-01-09
aussiebean:  I have been regularly using SBackup for years, saving each backup to a *different* PC on my LAN.  You are quite right in that there is little point in saving a backup to the same HDD ;-)

My PCs are connected via NFS and show up as mount points on each PC filesystem.  SBackup can save to remote PCs via these mountpoints and so I guess it would operate in a similar way with a USB flash drive.  All you will need to do is ensure the correct mount point (presumably in /media) is used in the SBackup Config screen.  This *might* be slightly tricky if your USB flash drive name changes, unless you wish to reconfigure SBackup for each run.

One more point to consider is that SBackup runs as root so just make sure your file permissions allow for this when mounting the USB drive and saving/restoring backups.

---

### Post by OldBoy44 on 2011-01-09
Thanks for your alternative Zill,

The only problem is that I am on a rather steep learning curve but I will search for answers when needed.

  :)

---

### Post by Zill on 2011-01-09
> **aussiebean said:**
> ...The only problem is that I am on a rather steep learning curve but I will search for answers when needed.
That's the Linux way ;-)

If you need any more help feel free to ask - there are lots of good folk here willing to assist.  Good luck.

---

### Post by OldBoy44 on 2011-01-09
> **Zill said:**
> aussiebean:  I have been regularly using SBackup for years, saving each backup to a *different* PC on my LAN.  You are quite right in that there is little point in saving a backup to the same HDD ;-)

My PCs are connected via NFS and show up as mount points on each PC filesystem.  SBackup can save to remote PCs via these mountpoints and so I guess it would operate in a similar way with a USB flash drive.  All you will need to do is ensure the correct mount point (presumably in /media) is used in the SBackup Config screen.  This *might* be slightly tricky if your USB flash drive name changes, unless you wish to reconfigure SBackup for each run.

One more point to consider is that SBackup runs as root so just make sure your file permissions allow for this when mounting the USB drive and saving/restoring backups.

Thanks again Zill,

Under what circumstances would the USB flash drive name change?

  :)

---

### Post by Zill on 2011-01-10
> **aussiebean said:**
> ...Under what circumstances would the USB flash drive name change?
If you have multiple USB flash drives then you will need to ensure that you use the same one every time you backup as the name will be saved in the SBackup configuration file.  Alternatively, you could give multiple drives the same name ;-)

---

### Post by OldBoy44 on 2011-01-10
Thanks very much Zill for taking the time to reply - I guess the answer was pretty simple after all!

I will mark the thread as resolved.

Cheers,  :popcorn:

---

