---
title: "sbackup -- where's the backup?"
date: 2009-12-08
forum: New to Ubuntu
---

### Post by palmettoj on 2009-12-08
I'm trying to test run sbackup. When I click backup now, a window says "a backup run is initiated in the background. the process id is 2551" but when I look at my system monitor, there is now process 2551 (maybe that's what's meant by 'background'?). Nor is there a file listed under available restore files in sbackup's restore function. what's up?

---

### Post by Sir Jasper on 2009-12-08
Hi,

It runs in the background and it may take a few minutes to finish or it may take an hour or more. It will not tell you when it has finished. So you can look at your process monitor or you can view the target area.

My regards

---

### Post by sgosnell on 2009-12-08
Look at [this diagram](http://migas-sbackup.sourceforge.net/images/backup.jpg).  It shows the sbackup steps.  There will be no file in the destination until the backup is complete and it is copied there.  Sbackup uses a tmp directory while making the backup, then copies the backup file.  You should see it in the directory you specified when the backup is complete, which may take some time, as it's a background process, and foreground processes take priority, thus the background process yields to them when they request CPU time.  Be patient, grasshopper.

---

### Post by palmettoj on 2009-12-09
> **palmettoj said:**
> ..., there is now process 2551 (maybe that's what's meant by 'background'?)....
just realized that should be "no" not "now." I guess not seeing the process in the system monitor ->processes tab made me wonder. But I also thought it could be my impatience ;)
thanks for the help

---

### Post by sgosnell on 2009-12-09
What should show up eventually, in the folder you specified, is a folder named something like 2009-12-08_20.51.30.018364.your-computer-name.ful, where 'your-computer-name is the name of your computer.  The first part of the folder name is the date and time, the final group I don't know.  Inside this folder is your backup, consisting of several files.  The actual backup is files.tgz, the rest are configuration and information files.

---

### Post by hobo14 on 2009-12-10
This is what turned me off sbackup too; no visual indicator of it's progress.

I was doing huge backups that it couldn't handle, and would die in the middle of, but I wouldn't realise until much later.

It may be a great backup tool, but it's human interface is poor.

---

### Post by freesitebuilder on 2009-12-10
I agree with hobo14 - I was "running" backups that weren't actually working, but no error messages, fails, anything to tell me it hadn't worked.

I use grsync now.

---

