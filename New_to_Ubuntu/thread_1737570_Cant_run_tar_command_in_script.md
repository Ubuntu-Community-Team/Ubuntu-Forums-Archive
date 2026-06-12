---
title: "Cant run tar command in script"
date: 2011-04-23
forum: New to Ubuntu
---

### Post by chadbst on 2011-04-23
Hello folks

I am trying to run a backup script.  One of the commands is the tar command.  When I run the script the tar command gives the following error:
[INDENT]Cowardly refusing to create an empty archive
[/INDENT]

When I run the same exact command from the command line, I do not get that error if I run it as sudo.  I will, however, get the above mentioned error if I don't run it as sudo.

Therefore, the problem seems to be that I am not running the command with sudo privileges in the script.  However, I don't know how to fix it.  I googled this problem and can't really find a solution.

The command, exactly as I typed it is:
[INDENT]sudo tar -zcvf /home/chadbst/backups/test3.tar -C /var/www/
[/INDENT]

Any help is greatly appreciated.

---

### Post by chadbst on 2011-04-23
Forgot to mention that I did try:
[INDENT]sudo tar -zcvf /home/chadbst/backups/test3.tar -C /var/www/
[/INDENT]

within the script and it didn't work.  Only works from the command line.

---

### Post by user333 on 2011-04-23
Here is what you have to do:
```

gksudo echo
sudo tar -zcvf /home/chadbst/backups/test3.tar -C /var/www/

```

Just add that gksudo echo command and it will work great ;)

---

### Post by chadbst on 2011-04-23
Hello,

Thanks for the quick reply.  I am running Ubuntu Server and therefore do not have a gui.

Is there something else I can do to get it working?

---

### Post by user333 on 2011-04-23
Can you run the entire script as root? Like sudo sh script.sh ?

---

### Post by chadbst on 2011-04-23
I ran the shell script as follows:
   sudo /usr/bin/backupScript.sh

That did not work.  Also tried your suggestion:
   sudo sh /usr/bin/backupScript.sh

Neither worked.  Tar gives the same error message as I mentioned in the first post.

---

### Post by user333 on 2011-04-23
Sorry I couldn't help. I'll let you know if I figure out anything! Maybe I'll try later to make a dummy script like yours and figure out how to make it work.

---

### Post by ~Plue on 2011-04-23
try without -C, its not necessary for creating an archive from the given directory (its needed when extracting an archive to another folder)
```
tar -zcvf /home/chadbst/backups/test3.tar /var/www/
```

---

### Post by user333 on 2011-04-23
I make a script modeled after yours, and I get the same error. Maybe you have an error in the tar command.

edit: Plue's suggestion fixes the problem.

---

### Post by chadbst on 2011-04-23
Yes, Plue's suggestion did fix the problem.  Thanks to both of you for your assistance.

---

