---
title: "Failure of luckyBackup"
date: 2010-06-07
forum: New to Ubuntu
---

### Post by Chough39 on 2010-06-07
[COLOR=#ff0000][COLOR=Black]I have installed luckyBackup on Ubuntu 10.04 and it worked to start with. On modifying profiles it will not now backup, even though the simulation states that there are no errors. The following message is typical. I have done a complete reinstall of the programme with no success. Some help would be much appreciated please.[/COLOR]
[/COLOR]
[COLOR=#ff0000]
[/COLOR]
[COLOR=#ff0000]r[/COLOR][COLOR=#ff0000]sync: mkdir "/media/BACKUP/luckyBackup" failed: No such file or directory (2) [/COLOR]
 
 [COLOR=#ff0000]r[/COLOR][COLOR=#ff0000]sync error: error in file IO (code 11) at main.c(595) [Receiver=3.0.7] [/COLOR]
 
 [COLOR=#ff0000]r[/COLOR][COLOR=#ff0000]sync: connection unexpectedly closed (9 bytes received so far) [sender] rsync error: error in rsync protocol data stream (code 12) at io.c(601) [sender=3.0.7] [/COLOR]
 [COLOR=#ff00ff]execution of task : [/COLOR][COLOR=#ff00ff]Home[/COLOR][COLOR=#ff00ff], finished[/COLOR] ====================================

---

### Post by Chesamo on 2010-06-07
Are you running the backup as root? (ie. sudo luckybackup)

---

### Post by aeiah on 2010-06-07
does '/media/BACKUP/luckyBackup' exist?

it looks like rsync is trying to make this directory. it shouldn't matter if BACKUP doesnt exist, because rsync should do this recursivley. this leads to the conclusion that rsync doesn't have the rights to create stuff on /media/BACKUP/

in a terminal, can you create the directory yourself with:
```

mkdir /media/BACKUP/luckyBackup

```
???

looks like you may need root privs to create directories on your BACKUP drive. its probably best to change the permissions on the drive rather than run luckyBackup as root ever time.

---

### Post by Chough39 on 2010-06-07
Thanks for your prompt help, the programme now works well.

Chough39

---

