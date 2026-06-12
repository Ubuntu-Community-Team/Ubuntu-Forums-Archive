---
title: "sbackup file storage question"
date: 2009-06-20
forum: New to Ubuntu
---

### Post by 73ckn797 on 2009-06-20
I ran sbackup but failed to save configuration. I meant to backup to a different drive (sdc) but instead it went to (sda) /var/backup. I deleted the backup but still have lost over 20Gib of drive space. What other folders would be created or where would any additional info be stored? I have looked around but do not want to delete the wrong stuff. I completely removed sbackup prior to deleting the folder referred to above. The disk space is still an issue. I find no info in Community documentation to help beyond what I have stated.

Any suggestions?

---

### Post by michy99 on 2009-06-20
Since you would have deleted them as root, they are probably in root's trash. Try this:```
sudo rm -R /root/.local/share/Trash
```

---

### Post by 73ckn797 on 2009-06-20
> **michy99 said:**
> Since you would have deleted them as root, they are probably in root's trash. Try this:```
sudo rm -R /root/.local/share/Trash
```


YEP, 35Gib in the /root..../Trash. It is a 160GiB drive and I knew there should have been more space.  I ran Nautilus as admin and saw the folder contents prior to running the command you provided.

Thanks!

---

