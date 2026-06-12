---
title: "Crontab - not sending emails"
date: 2008-02-19
forum: Networking &amp; Wireless
---

### Post by SumnerBoy on 2008-02-19
I have a cron task configured to run a backup routine every night at 3am. I know that the backup is generating errors (some of my NTFS filenames I am backing up have invalid characters). 

Cron isn't sending any emails however - is there something I need to do to configure this? I only want to receive emails if there is an error.

This is the crontab entry for my user...

0 3 * * * /etc/backup/backup > /home/ben/cronlogs/backup.log

I get all non-error output routed to backup.log and any error output will be sent to stderr - which I thought should be sent to the executing users email - is this right?

This job is being run as myself however I still don't see emails being generated/sent/received.

I have just installed PostFix but am unsure if it is correctly installed. What should I be checking to see why the cron emails are not being sent? 

Any help is warmly received!

---

### Post by jhetrick62 on 2008-02-19
I don't believe cron itself sends the emails, it's the process itself that should send the emails meaning such as rsync or tar which ever you are using.

Secondly, I believe most of these use sendmail so I'm not sure if they will use postfix.  I also am not running postfix so I'm not sure if it uses sendmail or uninstalls it and replaces it, sorry.

Jeff

---

### Post by erginemr on 2008-02-19
> **jhetrick62 said:**
> I don't believe cron itself sends the emails, it's the process itself that should send the emails meaning such as rsync or tar which ever you are using.

Secondly, I believe most of these use sendmail so I'm not sure if they will use postfix.  I also am not running postfix so I'm not sure if it uses sendmail or uninstalls it and replaces it, sorry.

Jeff

No no... I am no expert in crontab either, but AFAIK, crontab itself is supposed to send e-mails to a local mail server (maybe through sendmail) but there is none installed in a default Ubuntu installation, so this part is non-functional. 

Please refer to these pages and check for the keyword "mail":
[http://www.hmug.org/man/8/cron.php](http://www.hmug.org/man/8/cron.php)
[http://unixhelp.ed.ac.uk/CGI/man-cgi?crontab+5](http://unixhelp.ed.ac.uk/CGI/man-cgi?crontab+5)
[http://www.ss64.com/bash/cron.html](http://www.ss64.com/bash/cron.html)

Meanwhile **SumnerBoy**, you can redirect errors with:
```
0 3 * * * /etc/backup/backup > /home/ben/cronlogs/backup.log 2> /home/ben/cronlogs/errors.log
```
or both to the same log file with:
```
0 3 * * * /etc/backup/backup > /home/ben/cronlogs/backup.log 2>&1
```

---

### Post by SumnerBoy on 2008-02-19
I am a little embarassed to say that cron does actually email me the error log! I was testing it by forcing cron to run the job (via Webmin) and the output was just being displayed in the web page. I figured this was equivalent to running the job via the daemon - but alas that was not the case.

So now I have an email being sent to my user account with the backup error log - perfect. What I now want to do is forward these emails onto my GMail account so I actually see them in my inbox in the morning.

I have come across a few posts that detail how to set this up but I have not been able to get things working. The config seems very complicated (with the need for client/server certificates etc) - is there a simple method for acheiving this sort of thing?

---

### Post by Dr Eigen on 2008-03-12
Put a .forward file in $HOME with the address you want stuff sent to in it.  The permissions may need to be set to something specific for this to be honoured.

---

### Post by SumnerBoy on 2008-03-12
Thanks - someone else sent me the same tip which helped.

---

