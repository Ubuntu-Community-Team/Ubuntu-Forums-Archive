---
title: "cmd works in bash, not crontab??"
date: 2010-07-16
forum: New to Ubuntu
---

### Post by three_jeeps on 2010-07-16
I want to write the date & time and a text string to a file from crontab.  
The following line works fine in the CL:
   echo $(/bin/date +"%F %T")" Some text" >> /home/me/foo.txt

I installed in crontab and no text appears in the file that it is redirected to.

The crontab entry looks like:
* * * * * echo $(/bin/date +"%F %T")" Some text" >> /home/me/foo.txt

Tried a version to just write to stdout....

* * * * * echo $(/bin/date +"%F %T")" Some text"

No text appears at the command line.
Shell is bash.
Any suggestion what the problem is and how to fix???
thanks,
-J

---

### Post by Sanjeevtrip on 2010-07-16
cron -- sends you the mail, if fails
you can achieve this by putting it in shell program and calling in cron
 
in your case cron may be having problem with quotes

---

### Post by three_jeeps on 2010-07-16
> **Sanjeevtrip said:**
> cron -- sends you the mail, if fails
you can achieve this by putting it in shell program and calling in cron
 
in your case cron may be having problem with quotes

Using the escape in the date command, in crontab worked:

```
* * * * * echo $(/bin/date +"\%F \%T")" Some text" >> /home/me/foo.txt 
```

Interestingly, using the single quotes did not....hmmm
```


* * * * * echo $(/bin/date +'%F %T')" Some text" >> /home/me/foo.txt 
```

Thank you!

---

