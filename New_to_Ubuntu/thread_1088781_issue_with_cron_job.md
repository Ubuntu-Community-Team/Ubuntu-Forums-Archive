---
title: "issue with cron job"
date: 2009-03-06
forum: New to Ubuntu
---

### Post by jmd9qs on 2009-03-06
hi all,

i recently created a really simple script to generate a "report" about system information. I wanted to learn more about cron jobs, so I tried to set my crontab up so that this report would generate every day at 1AM and save to a timestamped file. For some reason it isn't working... please take a look at my cron entry and let me know if i'm doing something wrong...
```

{09-03-06 -- 09:46 AM } jmd9qs: ~/Reports -$: echo $PATH; crontab -l
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/home/jmd9qs/Scripts
# m h  dom mon dow   command
 01 1  *   *   *     /home/jmd9qs/Scripts/REPORT1
```

by the way, i seem to have 2 crontabs... the other one resides in /etc/crontab and looks like this:

```
{09-03-06 -- 09:46 AM } jmd9qs: ~/Reports -$: cat /etc/crontab 
# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin:/jmd9qs/Scripts

# m h dom mon dow user	command
17 *	* * *	root    cd / && run-parts --report /etc/cron.hourly
25 6	* * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6	* * 7	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6	1 * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
#
01 1   * * *   jmd9qs  /home/jmd9qs/Scripts/REPORT1


```

also, i have tested the script and it works as planned... i just cant seem to execute it via the crontab.

any suggestions?

---

### Post by geirha on 2009-03-06
Two things you can do to debug. One is to install [mailx](apt:mailx). Once that is installed, cron will mail you the output of the command, which is hopefully a useful error message. To read such system mail that cron sends, run the command ```
mail
``` in a terminal

The other thing is to make sure your script uses the full path to the commands it uses. Cron uses a much smaller environment, with shorter PATH etc. You can view the environment by adding a cronjob like this:
```
* * * * * env >/tmp/cron-env
```
Then look at /tmp/cron-env and compare it with the output of the env command in your current shell.

---

### Post by lovinglinux on 2009-03-06
Try this:

```
USER=jmd9qs
HOME=/home/jmd9qs
SHELL=/bin/bash
PATH=/sbin:/bin:/usr/sbin:/usr/bin:/home/jmd9qs/Scripts
DISPLAY=:0.0
MAILTO=jmd9qs

 01 1  *   *   *     /home/jmd9qs/Scripts/REPORT1  [COLOR="Red"]>/dev/null 2>&1[/COLOR]
```

Please notice that without the declarations in the top and the code in red, the script probably won't work via cron.

---

