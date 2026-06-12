---
title: "backup using rsync"
date: 2010-08-02
forum: New to Ubuntu
---

### Post by lance bermudez on 2010-08-02
I have a samba share to a windows 7 computer I do not know if I will be able to use backintime or not so I want to know how to have rsync do my backup.

I read the man but I'm not sure if I understand the it.

on same computer different hard drive to run every hour in a script. Leanne is windows 7 share and backup is the other hard drive in the computer
rsync -arvRzEP /media/leanne /media/backup

run mounthly
rsync -arvRzEPe ssh  /media/backup pete@1.2.3.4:/home/backupmonthly

---

### Post by mapes12 on 2010-08-02
[http://www.psychocats.net/ubuntu/backup](http://www.psychocats.net/ubuntu/backup)

I add the GUI and install grsync from Synaptic. Works great for me.

---

### Post by soldier1st on 2010-08-03
Grsync also works great for me so try that.

---

### Post by jmszr on 2010-08-03
lance bermudez,

Back-in-time uses rsync (along with diff and cp) to backup your directories, so if rsync is usable then back-in-time _should_ be usable.

Here is an rsync tutorial - just in case: [http://everythinglinux.org/rsync/](http://everythinglinux.org/rsync/) and grsync: [http://www.makeuseof.com/tag/grsync-simple-gui-rsync-easily-linux/](http://www.makeuseof.com/tag/grsync-simple-gui-rsync-easily-linux/)  and: [http://www.dedoimedo.com/computers/grsync.html](http://www.dedoimedo.com/computers/grsync.html)

---

