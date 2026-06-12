---
title: "Launcher does not run command"
date: 2009-03-01
forum: New to Ubuntu
---

### Post by numbatz on 2009-03-01
Hello,

I just installed Jaunty on an ext4 partition and things are working well.
However, I'm trying to create a Desktop launcher to perform an incremental backup of my home folder to my backup drive - so far no luck. When I enter "rsync -vare ssh /home/t/* /media/Data/backup/" in a terminal the the backup works fine.  But when I create a Launcher - (Application in Terminal) running this command the Terminal appears briefly but no backup.   What am I doing wrong?  

Thanks
Tristan

---

### Post by Xiong Chiamiov on 2009-03-01
I believe there is an option to run the command in a terminal?  Try that and see what happens.

---

### Post by numbatz on 2009-03-01
Thank you for your reply Xiong Chiamiov.  
Indeed, I have tried the "Application in Terminal" option.

Tristan

---

### Post by Xiong Chiamiov on 2009-03-01
Try adding the --verbose option to rsync so that you can see a little more what's going on with it.

---

### Post by numbatz on 2009-03-01
I'm not sure how to add --verbose to the command.  I'm strictly cut'n paste. Perhaps you would kind enough to illustrate.

Tristan

---

