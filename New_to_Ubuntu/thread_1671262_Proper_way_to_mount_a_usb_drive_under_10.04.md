---
title: "Proper way to mount a usb drive under 10.04"
date: 2011-01-19
forum: New to Ubuntu
---

### Post by dsmryder on 2011-01-19
):P
I have a HDD that I'd like to use as a backup location for my server. I have found that rsync should work to run my backups, but I would need it to automatically mount my drive. I went into my fstab and have added the drive by it's UUID. But when I reboot the server, it doesn't auto mount it. I have tried to use auto instead of ntfs-3g. but that didn't work either.
I would also know how to properly use rsync to run my backup. I may have come close to figuring that one out, though.
 
I have included my fstab entry, and my script
UUID=168d39e18d37b67 /media/AllTheBackup ntfs-3g user,rw,nosuid 0 0
 
#!/bin/sh
while [ 1 ]
do
if [ -e "/media/AllTheBackup" ]
then
rsync -c /home/media/emu /media/AllTheBackup/
rsync -c /home/media/music /media/AllTheBackup/
rsync -c /home/media/pics /media/AllTheBackup/
else
sleep 15
fi
done

---

### Post by uriel1998 on 2011-01-19
> **dsmryder said:**
> ):P
I have a HDD that I'd like to use as a backup location for my server. I have found that rsync should work to run my backups, but I would need it to automatically mount my drive. I went into my fstab and have added the 

To be fair, I'm partially replying so that I see answers to the above myself!  As it stands, I'm having to run Nautilus just to mount the external HDD, but testing for a file in the root of the external HDD before backing up.

> **dsmryder said:**
> 
I would also know how to properly use rsync to run my backup. I may have come close to figuring that one out, though.
 

I **almost** used rsync - then I found [rdiff-backup]("http://www.nongnu.org/rdiff-backup/").  The diff files save me LOTS of time, space, and disk activity.  Otherwise my backup script looks very similar to yours - here's one chunk:

```
if [ -f /media/backup/testfile.sh ]
    then
rdiff-backup --remove-older-than 20B /media/backup/usr/
sudo rdiff-backup -v5 --print-statistics --exclude '**log' --exclude '**vdi' /usr /media/backup/usr
fi
```

---

