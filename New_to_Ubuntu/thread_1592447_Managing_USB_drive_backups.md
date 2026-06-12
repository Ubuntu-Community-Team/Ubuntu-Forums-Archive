---
title: "Managing USB drive backups"
date: 2010-10-10
forum: New to Ubuntu
---

### Post by echo314 on 2010-10-10
I can easily backup a few USB drives to the hard disk through rsync, luckybackup, or similar. However, if I'm trying to back up weekly, I'm worried that the scripts or saved configs won't work because as I'm plugging in and unplugging stuff throughout the week, and cycling power for the computer, the locations of the USB drives won't be the same next time I plug them in. Thus, I save no time by saving a configuration. 

Does this actually happen? Is there a good way to manage backups of multiple USB drives on a weekly basis, without worrying about whether a drive will show up in the same directory?

---

### Post by echo314 on 2010-10-17
I still have not found a solution to this through searching. Can anyone address methods of handling backups from different USB flash drives, that are not always plugged in at the same location? Otherwise, I have to do it manually, which is really not the point of an automatic backup.

---

### Post by papibe on 2010-10-18
You can try to set the drive to mount always at the same location. To do that you can create an entry in /etc/fstab with the noauto option.

In order to reference the drive you'll need the universally unique identifier for a device (UUID). If when you plug the drive it's mounted on /dev/sdb1, you can get the UUID like this:

```
$ sudo blkid -o value -s UUID /dev/sdb1
```

Regards.

---

### Post by echo314 on 2010-10-31
Thank you, this addresses my problem nicely. Too bad I can barely comprehend "How to fstab" tutorials! I can try to follow the procedure found at [http://linux.derkeiler.com/Mailing-Lists/Ubuntu/2008-05/msg02837.html](http://linux.derkeiler.com/Mailing-Lists/Ubuntu/2008-05/msg02837.html)

Can someone confirm that this info is still relevant? After 2 years, I worry that changes may have been implemented.

---

### Post by papibe on 2010-11-01
I think replay #6 of this thread can give you more recent links and tutorials to understand how to use ntfs and fstab:

[http://ubuntuforums.org/showthread.php?t=1610503](http://ubuntuforums.org/showthread.php?t=1610503)

Good Luck!

---

