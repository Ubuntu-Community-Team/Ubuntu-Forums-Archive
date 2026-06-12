---
title: "hard drive gymnastics"
date: 2010-11-23
forum: New to Ubuntu
---

### Post by ByteOneZero on 2010-11-23
i have a 320 gb intrnal hd that has corrupt windows vista on 159 gb of drive.i am using ubuntu on 161 mb partition.i have a 250 gb seagate ext hd,and a 500 gb micro external drive.the micro is clean and empty.the seagate has some backed up files and an unloaded copy of win 7.how can i transfer everything on internal drive to either external drive,then reformat(wipe completely the internal hd) and install the windows 7 on the resulting internal drive.i then could have my ubuntu on an external hd and win7 on my internal.is this doable for a noob?

---

### Post by bananas4370 on 2010-11-23
> **ByteOneZero said:**
> i have a 320 gb intrnal hd that has corrupt windows vista on 159 gb of drive.i am using ubuntu on 161 mb partition.i have a 250 gb seagate ext hd,and a 500 gb micro external drive.the micro is clean and empty.the seagate has some backed up files and an unloaded copy of win 7.how can i transfer everything on internal drive to either external drive,then reformat(wipe completely the internal hd) and install the windows 7 on the resulting internal drive.i then could have my ubuntu on an external hd and win7 on my internal.is this doable for a noob?

Boot off a live cd. Mount the internal drive as well as the external drives. Use rsync or cp to get the files across.

Use this [article]("http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/") as a guide.

Hope that helps

Cheers
Patrick

---

