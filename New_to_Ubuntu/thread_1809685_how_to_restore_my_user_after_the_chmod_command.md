---
title: "how to restore my user after the chmod command"
date: 2011-07-21
forum: New to Ubuntu
---

### Post by chrislo2004 on 2011-07-21
Hi,

  I was testing the chown command. Under its help it says 

Examples:
  chown root /u        Change the owner of /u to "root".

...And so I tried chown root /home/user ...done but now i got a problem...it seems like root cannot change to user with the 'su user' command.

[root@server ~]# su user
bash: /home/user/.bashrc: Permission denied
bash-3.2$ whoami
user

---

### Post by chrislo2004 on 2011-07-22
oh dear silly me... lolz...and...smart me... i found the way to restore it...just simply... 

chown user /home/user
[root@server ~]# su user
[user@server ~]$

...come to think of it ...what happens was the user's /home/user/.bashrc was changed to root and so all the things needed by user cannot be processed...as such it goes back to the basic bash shell of bash-3.2$

...I got a new question now... is there any chances if I find myself in the simple bash-3.2$ i can go set the changes without using root to change the chown back to user for /home/user directory?

---

### Post by The Cog on 2011-07-22
If I understood the question properly, the answer is no. Only root can change the ownership of files/folders. If you are unable to get a root prompt after logging in, you will need to use recovery mode (from the boot menu) or boot a live CD and use the root account from there.

---

