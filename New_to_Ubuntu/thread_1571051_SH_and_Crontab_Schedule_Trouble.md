---
title: "SH and Crontab Schedule Trouble"
date: 2010-09-09
forum: New to Ubuntu
---

### Post by jaya28inside on 2010-09-09
Greetings everyone...
Seems I already follow the good instruction given
by the thread from the previous thread located at our 
ubuntu forum. But unfortunately my crontab seems doesnt execute 
my SH.

My purpose was setting it to be executed at the night time
day changed.

Please take a look,
and revise it,,,


FileName: **backupScript.sh**
> 
#!/bin/sh
tarikh=""$(date +%F_%R);
nama="crm_";
fileHasil=""$nama$tarikh.tar.bz;
targetLoc="/usr/share/myPlace/backup/";
targetWeb="/var/www/myWeb/";
echo "Processing Backup for $tarikh";
echo "Backing up in progress...";
tar cvjf $targetLoc$fileHasil $targetWeb;
echo "Backed up Success! Saved on $targetLoc$fileHasil";


so at the crontab I did;

```

$> crontab -e

```

and I entered this:

```

0 0 * * * /usr/share/myPlace/backupScript.sh

```

Done!
I check it via command

```

$> crontab -l

```

Everything seems okay.
But, why there's no the end result for this?
The more strange is,
If i do executing the SH file manually without CRON,
it is okay, no problem. But once I used it with CRON, no-one execute it.


My Reference:
> 
[http://www.cyberciti.biz/faq/how-do-i-add-jobs-to-cron-under-linux-or-unix-oses/](http://www.cyberciti.biz/faq/how-do-i-add-jobs-to-cron-under-linux-or-unix-oses/)

> 
[http://ubuntuforums.org/showthread.php?t=102626](http://ubuntuforums.org/showthread.php?t=102626)


:KS

---

### Post by Peter09 on 2010-09-09
No expert here but my experience is that this sort of error is normally to do with different environments. Make sure that all your path names, including those to executables are full/complete and that access rights are O.K as well.

---

### Post by bredman on 2010-09-09
Agree with Peter09.

You are using unqualified versions of the commands, but cron does not execute in your environment and therefore needs the fully-qualified names.

For example, you refer to tar, but if you enter the command
which tar

you will find that the fully-qualified name is
/bin/tar

Therefore, you need to change your references to echo and tar. Cron just can't find them the way you have specified.

You missed this important warning in your first reference link...

*First, the environment must be defined. If the shell line is omitted,  cron will use the default, which is sh. **If the PATH variable is omitted,  no default will be used and file locations will need to be absolute.***

---

### Post by jaya28inside on 2010-09-09
Thanks peter09, yes I'm also not the expert here.
Anyway, permission case.
Hmm... I did already giving the **backup** directory
to be written and read by everyone. User, group, and all can write/read 
that location...

Well, bredman ... "references"?

hold on, let me see...
at the time I check the Path and Shell reference
is pointing to the default one, seems okay.

Here the command to check;

```

$> cat /etc/crontab

```

and the content is of course default;

> 
SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin



so, is there any
another suggestion?
 ;)

---

### Post by bredman on 2010-09-09
I copied the warning from your first reference link
[http://www.cyberciti.biz/faq/how-do-...-or-unix-oses/]("http://www.cyberciti.biz/faq/how-do-i-add-jobs-to-cron-under-linux-or-unix-oses/")

You can specify a path at the top of the cron file, or you can replace "echo" with "/bin/echo" and replace "tar" with "/bin/tar".

The basic problem is that even though you have a PATH defined, it is not available to cron.

Note: please don't use an editor to edit /etc/crontab, always use the command crontab -e

---

### Post by jaya28inside on 2010-09-09
okay2... i follow ur advice bredman,

those echo command and tar command
now i change the previous SH file to this one;

Please revise it.

file Name: **backupScript.sh**
> 
#!/bin/bash
tarikh=""$(/bin/date +%F_%R);
nama="crm_";
fileHasil=""$nama$tarikh.tar.bz;
targetLoc="/usr/share/myPlace/backup/";
targetWeb="/var/www/myWeb/";
/bin/echo "Processing Backup for $tarikh";
/bin/echo "Backing up in progress...";
/bin/tar cvjf $targetLoc$fileHasil $targetWeb;
/bin/echo "Backed up Success! Saved on $targetLoc$fileHasil";


Another strange thing again happened.
The tar seems doing something.
At the time I check it at **backup** directory
I found there is a single result... but unforunately,
it didn't do compressing perfectly, it just got a few bytes only.
Actuall target should be more than a few bytes, it should be a MEGA BYTES.

gosh. Is there any other thing Forgotten?

---

### Post by bredman on 2010-09-09
It looks like your cron problems are fixed, but you now have scripting problems.

Have you tried to execute the script from the command line to make sure it works correctly?

I suggest you add diagnostics to your cron script to dump all variables to a file, for example
/bin/echo $fileHasil >> /var/log/mylog.txt

I am very suspicious about the assignment to tarikh. To add the results of date to the variable, you should enclose it in reverse quotes.
tarikh=$(`/bin/date`+%F_%R);

---

### Post by jaya28inside on 2010-09-12
hello again bredman,
I just returned from holiday 2 days...

okay, now let's continue this discussion.

I'm using single quotes at the /bin/date command I used
And the result was fine. The date and time were obtained.
If you're asking me to execute it manually via command.
Of course no problem. I used 
> 
$> ./backupScript.sh


and everything run smoothly. Executed and result obtained there.
The missing thing is that 
It can't be proceed by crontab scheduler.
my crontab seems never call it.

o yeah, the dump that you request on 
here's the result;

> 
Processing Backup for 2010-09-13_10:34

see? it's working, if only i manually execute it.
sigh... ooo gosh. 
probably either crontab or my scripting probs.

Anyway why bredman, you just said to me using reverse quote instead of single quote?

what are the other possibility which I may forgot?

---

### Post by jaya28inside on 2010-09-12
for this purpose I change my crontab with this one
> 
* * * * * /usr/share/myPlace/backupScript.sh


now I'm hoping it's executing every minutes...

aha! Yes!
I knew it now... bredman!
I got it, what should I do is omit the VERBOSE mode from tar command.
Now everything is fine. crontab execute it!

I'm glad this is done now.

---

