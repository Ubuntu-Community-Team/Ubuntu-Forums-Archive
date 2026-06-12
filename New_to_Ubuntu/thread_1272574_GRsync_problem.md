---
title: "GRsync problem"
date: 2009-09-22
forum: New to Ubuntu
---

### Post by cmcanulty on 2009-09-22
Day 3 of attempted backup. GRsync goes fine for a while then stops. It stops because after a few minutes my external hard drive disappears from the computer, what is causing this, it is driving me crazy! Also I can't delete all these small failed backups from the external drive how can I enable these deletes? Thank you. Here is the ;latest error message again as the light goes out and it disappears from my computer, aggravating!

rsync: writefd_unbuffered failed to write 4 bytes [sender]: Broken pipe (32)
rsync: connection unexpectedly closed (42444 bytes received so far) [sender]
rsync error: error in rsync protocol data stream (code 12) at io.c(600) [sender=3.0.5]

---

### Post by esalnoj on 2009-09-22
I have no experience with GRsync, but...

As far as deleting the small failed backups from your external, have you tried the following code in terminal with external hdd plugged in?

```
cd /media/"external_hdd"
cd "path/where/failed/backups/at"
rm "failed_backup"
```

replacing qoutation mark sections with what's indicated inside qoutes.

---

