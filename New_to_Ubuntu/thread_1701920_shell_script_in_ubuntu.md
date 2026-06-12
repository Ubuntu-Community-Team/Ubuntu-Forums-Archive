---
title: "shell script in ubuntu"
date: 2011-03-07
forum: New to Ubuntu
---

### Post by pmohankumar on 2011-03-07
hi, iam trying to set crontab in my ubuntu9.10 system. Before that, i tried to create a simple backup shell script.

backup_files="/home/dev151/Documents"

dest="/home/dev151/backup"    

and i created script as backup.sh, kept in desktop.

in terminal, i entered into desktop and i typed bash backup.sh, but its not working.

so, i need help to create a backup script to run crontab. kindly help me with a simple example.

---

### Post by cavh on 2011-03-07
You need to set backup.sh as executable. In a terminal, navigate to the folder containing the script, then type this command:

```
chmod u+x backup.sh
```

This sets the script as executable for the user currently logged in to the terminal. If this doesn't work, post the content of backup.sh in your reply.

---

### Post by mcduck on 2011-03-07
> **pmohankumar said:**
> hi, iam trying to set crontab in my ubuntu9.10 system. Before that, i tried to create a simple backup shell script.

backup_files="/home/dev151/Documents"

dest="/home/dev151/backup"    

and i created script as backup.sh, kept in desktop.

in terminal, i entered into desktop and i typed bash backup.sh, but its not working.

so, i need help to create a backup script to run crontab. kindly help me with a simple example.

If that's all you put into your script, then it's not a surprise it's not doing  anything. You are defining two variables, but not actually using them for anything or executing any commands... ;)

---

### Post by SeijiSensei on 2011-03-07
> **mcduck said:**
> If that's all you put into your script, then it's not a surprise it's not doing  anything. You are defining two variables, but not actually using them for anything or executing any commands... ;)

Indeed.  I recommend looking into [rsync]("http://rsync.samba.org/").

---

