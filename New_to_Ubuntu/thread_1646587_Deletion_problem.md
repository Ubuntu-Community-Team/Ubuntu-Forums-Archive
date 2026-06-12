---
title: "Deletion problem"
date: 2010-12-16
forum: New to Ubuntu
---

### Post by radmilo on 2010-12-16
I use Simple Backup tool, and it almost filled my HDD.
I opened location of backups (/var/backup) and tried to delete
folders, but I couldn't.
I guess due to privileges level. 
I opened nautilus, and used "open as administrator". 
Then I deleted files & folders from nautilus, but the problem is that there is no increase in free space...
Backups where 100GB, but even after deletion system shows 11GB free....

I would really appreciate help.

---

### Post by Elfy on 2010-12-16
When you deleted them they went to root's trash - you need to empty it :)

Try opening nautilus there

```
gksudo nautilus /root/.local/share/Trash/files
```

Or just open nautilus as root and look in it's trash

```
gksudo nautilus
```

[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)
[https://help.ubuntu.com/community/RecoverLostDiskSpace#Trash%20Folders%20Not%20Empty](https://help.ubuntu.com/community/RecoverLostDiskSpace#Trash%20Folders%20Not%20Empty)

---

### Post by radmilo on 2010-12-16
Thanks.
That was it!!!

---

### Post by Paqman on 2010-12-16
In future you can use shift-delete to delete files without sending them to the trash.

---

