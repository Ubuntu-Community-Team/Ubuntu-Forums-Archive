---
title: "Complete backup"
date: 2009-11-15
forum: New to Ubuntu
---

### Post by shoaibi on 2009-11-15
I have a VPS server which has almost 5G used all in all. I don't want to put it offline, and i need to create a complete backup and with complete backup i mean:

- home dirs
- all configurations
- all installed programs
- all user/system files

in other words a complete snapshot of the server state. It would be really great if this process could be incremental so i can use crons to make backups and download them to my local machine with only the changes that took place on server.

---

### Post by ZankerH on 2009-11-15
Not incremental, but I normally just leave it running overnight.

sudo dd if=/* of=destination

---

### Post by shoaibi on 2009-11-15
couple of things:
1. should dd be done when a filesystem is either not mounted or mounted in readonly?
2. it would take a lot of space and bandwidth to transfer...

---

### Post by ZankerH on 2009-11-15
> **shoaibi said:**
> couple of things:
1. should dd be done when a filesystem is either not mounted or mounted in readonly?
2. it would take a lot of space and bandwidth to transfer...

1. not mounted
2. I only do it over a local network, and I back stuff up to dedicated 2TB backup disks, so bandwidth and space aren't much of an issue.

Alternatively, look into rsync.

---

### Post by shoaibi on 2009-11-15
good, you are going good...
But my issues is that its a server located in a different continent and i only have 1M connection.

I know about rsync, rdiff, rsnaphot, duplicity, etc, but problem with these is restoration takes long and a lot of manual actions. I am looking for a tool based on dd which takes incremental snapshots.

---

### Post by Penguin Guy on 2009-11-15
I would highly recommend looking into rsync - it will save your hours of time. As for which directories should be backed up, here is my list:
```

- /root/.gvfs
- /home/*/.gvfs
- /root/.local/share/Trash/
- /home/*/.local/share/Trash/
- lost+found/
- /tmp/
- /cdrom/
- /media/
- /mnt/
- /proc/
- /sys/

```

---

