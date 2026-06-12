---
title: "Cron problems?"
date: 2009-09-13
forum: New to Ubuntu
---

### Post by dorseye on 2009-09-13
```
*/2 * * * * python /home/username/mypy/test/backup.py
```

So, I did $ crontab -e, added that, and it saved ok, but my backup.py file is not running? Anyone know what I'm doing wrong?

---

### Post by yeats on 2009-09-13
What is the "/2"?  You could refer to this:

[http://www.adminschoice.com/docs/crontab.htm#Crontab%20file](http://www.adminschoice.com/docs/crontab.htm#Crontab%20file)

---

