---
title: "Please check my backup script and also how to run as crontab?"
date: 2010-01-31
forum: New to Ubuntu
---

### Post by x C0MMAND0 x on 2010-01-31
Okay, here is my VERY basic backup script

```
#!/bin/bash

rsync -r -t -a --delete /etc/ /media/BGW\ Backup/Brent\'s\ ETC\ Backuptest/

rsync -r -t -a --delete --exclude-from /home/brent/backup.txt /home/ /media/BGW\ Backup/Brent\'s\ Linux\ Backuptest/
```

I want to make sure I have the correct syntax for rsync.  I have 
-r for recursive 
-t to preserve time stamp 
-a because thats what I was told (don't really understand)
--delete because I don't want files on the backup that aren't on my computer anymore
--exclude-from a .txt file that has some huge files that I don't care if they are backed up.

Also, I don't know if I need sudo to run this properly and if so, how do I set that up in crontab?  I know how to set a script to run in crontab no problem, but not if it needs sudo.

Thank you for the help.

---

### Post by x C0MMAND0 x on 2010-01-31
Any ideas?

---

### Post by jd65pl on 2010-02-01
You don't really need -r, -a will take care of recursion. Test your line out and check its doing what you want/expect.

You can check the options you need in the manual. The manual is searchable with vi like syntax.
```
man rsync
```

To add a root executed cron do
```
sudo crontab -e
```

I think you will find this will suffice
```
rsync -avt --delete /target /destination
```

---

### Post by YesSir on 2010-02-01
I added lines like these in crontab:

08 1 * * * root rsync -r -t --delete /source/ /target/

Which runs every day at 1:08 am.

---

