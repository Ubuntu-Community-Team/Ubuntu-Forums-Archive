---
title: "What's the diff between &quot;cp -ruv&quot; and &quot;rsync -azvv&quot;"
date: 2010-08-23
forum: New to Ubuntu
---

### Post by raf-kig on 2010-08-23
After using "cp -ruv" for my backups I decided to switch to "rsync -azvv" as described in 

[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)

However, I notice the following peculiar behavior: After a backup up with one command, I can immediately issue another backup with the same command and no files are copied, as expected. But if after a backup with either one, I immediately issue another backup with the other it recopies all the files as if they had changed, even though they are exactly the same files with identical date/time stamps. Can someone explain the reason for this?

---

