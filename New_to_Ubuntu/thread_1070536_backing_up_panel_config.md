---
title: "backing up panel config"
date: 2009-02-15
forum: New to Ubuntu
---

### Post by rburkartjo on 2009-02-15
i would like to backup my panel config to /media/ray
separate partition i have for my files
what would be the proper command to do so 
and what would be the proper command to reinstall the backup
/tks cheesemaker

---

### Post by ajgreeny on 2009-02-15
Your config is in *~/.gconf/apps/panel* folder, so you need ```
cp /home/username/.gconf/apps/panel/* /media/ray/panel/
``` but you must make the folder */media/ray/panel* first or you will get an error.  If */media/ray* is not owned by you *sudo* will be needed in front of the command.  To restore the config just reverse the folder pathways shown.

---

### Post by rburkartjo on 2009-02-15
aj . tks/cheesemaker

---

