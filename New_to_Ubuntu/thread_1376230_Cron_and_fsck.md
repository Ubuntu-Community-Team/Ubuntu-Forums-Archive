---
title: "Cron and fsck"
date: 2010-01-08
forum: New to Ubuntu
---

### Post by CharlesA on 2010-01-08
Hi all,

I've been neglecting running fsck on my backup drives (since they are mounted before rsync runs, and unmounted after it's finished)

My crontab looks like this:

```

#Sync RAID Array to External 1.5TB Drive hourly
0 */1 * * * /home/charles/docbk >/dev/null 2>&1
#Sync DVD folder to External 2.0TB Drive daily
0 0 * * * /home/charles/dvdbk >/dev/null 2>&1
#Update AV signatures for BitDefender
0 */8 * * * /home/charles/bdupdate >/dev/null 2>&1

```

I want to do a fsck (set to notify me of the results)) on the 1.5TB drive every 2 days (since it's mounted and unmounted 24 times a day...) and the 2.0TB drive every 20 days.

Is this possible, and if so, how could I go about it?

Here's the backup script I use for the 1.5tb drive, if it helps any.

```
if ! mountpoint -q /docback
then
   mount -t ext3 UUID=f00c8f27-7a11-42b0-96f9-0e04a261d682 /docback
fi
rsync -ai --delete --progress /array/charles /array/clone /array/guildwars /array/isos /array/karen /array/music /array/servicepacks /array/shared /array/testout /array/win7stuff /docback
umount /docback

```

Would it be a good idea to add the rsync command after mounting the drive using "&&" so that it will only run if the device is successfully mounted? (if it's running fsck when unmounted, it is marked as busy, right?)

I'd be running fsck -n so that it only reports corruption.

Thanks for any advice.

---

