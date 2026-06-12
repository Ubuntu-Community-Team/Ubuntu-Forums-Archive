---
title: "backup download folder before update"
date: 2010-04-27
forum: New to Ubuntu
---

### Post by Phan76 on 2010-04-27
So getting ready to do the upgrade later this week, all things I have downloaded that I might want to keep are in my download folder on my laptop.. Is there away to back up just this folder in case of a problem with the update so that things aren't lost?

---

### Post by mbzn on 2010-04-27
Yes, on external storage...
You could also just keep your home partition (if you have that separate) and do a clean install, this way it always goes smoothly.

---

### Post by Seal Daemon on 2010-04-27
Depends on the size .. DropBox could be one of the easiest solutions if there's no way you could move them anywhere else.

---

### Post by switch10 on 2010-04-27
rsync -auv --progress --stats ~/Downloads /media/external_storage

---

