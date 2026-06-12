---
title: "[SOLVED] delete old quickstart backups"
date: 2008-12-22
forum: New to Ubuntu
---

### Post by capnthommo on 2008-12-22
hi.  can anybody tell me a simple terminal command to delete old quickstart backup files.  eg (tar_home_backup_2008.12.18_home_backup_tgz)  i cant move the file to trash using file browser - when i try using nautilus file manager  i get 
(Error while moving "tar_home_backup_2008.12.18_home_backup.tgz". there was an error moving the file into /backup/.trash-0   details  permission denied).
it seems i dont have permissions to clear old backups off the (/ ) directory and cant see how to do it with quickstart (i'm sure there must be a way) so is there a eg (sudo......) command. i have looked through my notes and come up blank.  help much appreciated.
nigel

---

### Post by taurus on 2008-12-22
```
sudo rm tar_home_backup_2008.12.18_home_backup_tgz
```

---

### Post by M4rotku on 2008-12-22
If you want to do it within the graphical environment then you could simply use "sudo nautilus" to launch nautilus with sudo privileges.

---

### Post by capnthommo on 2008-12-22
thanks to both of you taurus and M4rotku.  i think that was just what i want.  i am trying to gradually wean myself away from the need for GUIs but it's nice to have both ways. thanks v much
nigel

---

