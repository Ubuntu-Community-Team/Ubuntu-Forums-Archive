---
title: "crontab configuration"
date: 2010-08-09
forum: New to Ubuntu
---

### Post by goldenbough on 2010-08-09
I am having some trouble getting a crontab going on my server.  I would like to have a rake task for ruby on rails application done with cron.  


Here is the command:
*/59 * * * * cd apps/project/current && rake thinking_sphinx:index RAILS_ENV=production



Here is the log:

 CRON[2969]: (user) CMD (cd apps/project/current && rake thinking_sphinx:index RAILS_ENV=production)


I can cut and past the command, excluding the parenthesis, and the rake task runs fine.

---

### Post by john newbuntu on 2010-08-09
```
cd apps/project/current 
```does not look like an absolute path.  It may be a path under your home directory, in which case you will have to full path it. Example: 
```
cd /home/user/apps/project/current
```

---

### Post by goldenbough on 2010-08-09
I changed it to the full path from /  , but still it doesn't actually index the files, I see it running the command in the log though.


cd /home/user/apps/project/current && rake thinking_sphinx:index RAILS_ENV=production

---

### Post by goldenbough on 2010-08-09
I added another line that prints out a message in a log and this works.  So I guess it is something about rails and the rake command.  



*/1 * * * * cd /home/user/apps/project/current && rake thinking_sphinx:index RAILS_ENV=production
*/1 * * * * echo "hello world: $(date)" >> /home/user/log2

---

### Post by goldenbough on 2010-08-09
I added these lines at the top of the crontab file, and now am good to go.

PATH=/usr/local/bin:/usr/bin:/bin 
SHELL=/bin/bash

---

### Post by CharlesA on 2010-08-09
Interesting. You probably would have had better results, if you create a shellscript and ran that in cron instead of adding varibles and whatnot directly to the crontab.

It would have looked cleaner, at least. :)

---

