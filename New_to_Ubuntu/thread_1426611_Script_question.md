---
title: "Script question"
date: 2010-03-10
forum: New to Ubuntu
---

### Post by baddnady23 on 2010-03-10
Just looking to verify that this should copy my home directory on computer "A" to the media/data/backup directory on computer "B" so that in the event I needed to retrieve a backed up /home I would be able too...

```
rsync -ave ssh --delete --log-file=/home/andrew/Logs/rsync/$(date +%Y%m%d)_rsync.log /home/andrew/ andrew@192.168.1.70:/media/data/backups/ubuntu_home_backup/home_desktop
```

---

### Post by undecim on 2010-03-10
the "e ssh" part probably isn't needed. The "/" at the end of /home/andrew means that it will copy the files inside of /home/andrew, but not the "andrew" folder itself (for example, your .bashrc file will be copied to /media/data/backups/ubuntu_home_backup/home_desktop/.bashrc, rather than /media/data/backups/ubuntu_home_backup/home_desktop/andrew/.bashrc)

Assuming that is what you want, it loooks good to me.

---

### Post by baddnady23 on 2010-03-10
Yea I think thats what I was going for.  Thanks.  How come I wouldn't need the -e ssh part?

---

### Post by undecim on 2010-03-10
the way you have the destination typed hostname:/path/ rsync will use SSH.

It shouldn't hurt though. There's no harm in defining options explicitly.

---

