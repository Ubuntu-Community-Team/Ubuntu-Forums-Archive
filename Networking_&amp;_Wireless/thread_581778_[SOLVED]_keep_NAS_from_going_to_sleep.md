---
title: "[SOLVED] keep NAS from going to sleep"
date: 2007-10-19
forum: Networking &amp; Wireless
---

### Post by dave37 on 2007-10-19
I'm using a tritton technologies simpleNAS enclosure.  I can access it fine, it automatically mounts via fstab, but I want to let it power down when the connected machine is not in use so in it's settings it's set to 30 minute hdd power down.

My problem is that it takes a little while to wake up, so when selecting a folder to save a download in (even when not wanting to save to the NAS), etc, it has to wake back up before I can do anything.  Can anyone think of a command or simple script I could use to, for example, write a small txt file to it every 31 minutes so that as long as my pc is on, the nas doesn't go to sleep.

Thanks!

---

### Post by oooooops on 2007-10-19
> **dave37 said:**
> I'm using a tritton technologies simpleNAS enclosure.  I can access it fine, it automatically mounts via fstab, but I want to let it power down when the connected machine is not in use so in it's settings it's set to 30 minute hdd power down.

My problem is that it takes a little while to wake up, so when selecting a folder to save a download in (even when not wanting to save to the NAS), etc, it has to wake back up before I can do anything.  Can anyone think of a command or simple script I could use to, for example, write a small txt file to it every 31 minutes so that as long as my pc is on, the nas doesn't go to sleep.

Thanks!

Could you not put a cron job to touch some file every so often?

touch /media/nas/tmp/awake.txt

---

### Post by dave37 on 2007-10-20
Perfect!!  Thank you!!

---

