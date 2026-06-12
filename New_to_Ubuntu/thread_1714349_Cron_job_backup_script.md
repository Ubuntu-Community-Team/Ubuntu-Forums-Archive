---
title: "Cron job backup script"
date: 2011-03-25
forum: New to Ubuntu
---

### Post by GrouchyGaijin on 2011-03-25
Hi All,

I made a script to copy all the files from several folders to an external drive.

```

#!/bin/bash
cp /home/john/Documents -r /media/Elements/ubuntu/
cp /home/john/scripts -r /media/Elements/ubuntu/
cp /home/john/conkys -r /media/Elements/ubuntu/
cp /home/john/Pictures -r /media/Elements/ubuntu/
cp /home/john/.bash_aliases /media/Elements/ubuntu/

```

I gave this script the Bash alias mybackup.

It works fine if I type mybackup in the terminal.  It also works fine if I double click the script and choose run.

It does not work, however, when I try to set this as a job with the task scheduler.

When I set the path to the script in the command field I get this:

```

cp: omitting directory `/home/john/Documents'
cp: cannot stat `-r': No such file or directory
cp: omitting directory `/home/john/scripts'
cp: cannot stat `-r': No such file or directory
cp: omitting directory `/home/john/conkys'
cp: cannot stat `-r': No such file or directory
cp: omitting directory `/home/john/Pictures'
cp: cannot stat `-r': No such file or directory
Press ENTER to continue and close this window. 

```

If I set the command as simply mybackup I get an error that the command is unknown.

I've tried with the command listed as default behavior and as an x application.

Does anyone know what I can do to fix this problem?
I really appreciate the help.

---

### Post by blind2314 on 2011-03-25
For what it's worth, it's usually convention to put flags for a command before the arguments.
 
I.e.,
 
```
cp -r <source> <dir>
```
 
Instead of
 
```
cp <source> -r <dir>
```
 
It seems that it's interpreting the -r as an additional folder, and skipping the directories (since it doesn't see the -r option as a switch). Make the switch I mentioned above and see if that fixes it.

---

### Post by GrouchyGaijin on 2011-03-25
> **blind2314 said:**
> For what it's worth, it's usually convention to put flags for a command before the arguments.

That is worth a lot.  I should have read more carefully when I looked at the Bash for Dummies guide. 

Thank you!

---

### Post by freak42 on 2011-03-25
Hi

just wanted to give you some tips concerning backups:

you really should look into rsync ( with -avz options) for backing up your things: It will only copy new files and files that have changed which makes the backup process usually a couple of magnitudes faster.

or

you can look into a mac-timemachine like backup tool such as backintime which timestamps your backup, automatically creates cronjob entries and allows you to go back to an older version should you acidentially overwrite your (good) backup with corrupt data or something.

hth

---

### Post by oklokl on 2011-03-25
luckyBackup 
synaptic install
Programs
It is recommended
Are all set to feature ..

[http://luckybackup.sourceforge.net/](http://luckybackup.sourceforge.net/)

[http://cafe.daum.net/candan/C2qK/24](http://cafe.daum.net/candan/C2qK/24)
setting view image

---

### Post by GrouchyGaijin on 2011-03-25
Thanks Guys,

I'll check those out.
I appreciate the help and advice!

---

