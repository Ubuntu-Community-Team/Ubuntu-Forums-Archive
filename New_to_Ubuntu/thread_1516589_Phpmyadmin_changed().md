---
title: "Phpmyadmin changed(?)"
date: 2010-06-23
forum: New to Ubuntu
---

### Post by dewhite765 on 2010-06-23
Greetings
I am a newbie and have had my trail of tears getting a lamp server running. But this issue has stumped me. So I go to the source of all ubuntu knowledge for help.

I am installing a LAMP server running ubuntu 8.04 at my church. Last night I installed the database and got it running. I used phpmyadmin to install the mysql data. I left the database working.

Tonight I found the database is still running, but phpmyadmin has no trace of the database I installed the night before. 

How can this be? My only conclusion is that maybe more than one phpmyadmin is running.

I remember not finding phpmyadmin initially with this ubuntu version. So I ran "sudo apt-get install phpmyadmin" (some details maybe missing).

Since my database is running, where is mysql and how do I connect phpmyadmin back to it?

Thanks in advance to helping to solve my mystery.

dewhite765

---

### Post by netwarriorwy on 2010-06-24
Try installing MYSQL Administrator, the official administration tool from MYSQL, is not so rich at adding or editing many rows at one time, but it does the same things as PHPMyAdmin. From the administrator you can check on all your databases installed and work with them, if you're afraid something may happen again you can easlily backup your databases runnning this command from the CLI (terminal) 
```
mysqldump -u root -p*yourPassword* *database*  > *anyname*.sql
```

For example:
```
mysqldump -u root -pHello MyDatabase > MyDBbackup.sql
```

This .sql file usually is saved under /home/yourUser/file.sql

To restore a backup just go to the option "Restore Backup" and choose the file you saved. Usually the "Restore Backup" option shows you the .sql files under /home/yourUser/ location but you can change this with the "Change Path" button at bottom, because maybe you decided to move your backup file somewhere else.

I hope It Helps!:popcorn:

---

### Post by dewhite765 on 2010-06-25
I found the solution. 
 
One part I left out earlier. I tend to create an ID for me and save the admin or root ID for special purposes. This time I created my ID from the root, but I forgot to give my ID all the admin priveleges. It only had limited access to everything else; hence, I could not see the database I had installed using my ID.
 
I feel embarrassed, but I now have another story to share.
 
dewhite765

---

