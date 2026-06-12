---
title: "weird crontab problem"
date: 2009-08-21
forum: New to Ubuntu
---

### Post by ptviperz on 2009-08-21
I've got a script that checks to see if sabnzbplus is running, if not, it starts it up.

```
#!/bin/bash

SABCNT=`/bin/ps aux | /bin/grep sabnzb | /bin/grep -v grep | /usr/bin/wc -l`
if [ $SABCNT -eq 0 ]; then
	echo start it;
	/etc/init.d/sabnzbdplus start;
else
        echo dont start it; 
fi

```

This works perfectly well from terminal without sudo priveleges, however it can't start sab up from cron, I get this in the output

start it
 * Starting SABnzbd+ binary newsgrabber
   ...fail!

I have the following in the crontab

*/1 * * * * root /home/brent/scripts/sabcheck.sh 2>&1 >> /home/brent/cronoutput.log

I've also tried it as 

*/1 * * * * /home/brent/scripts/sabcheck.sh 2>&1 >> /home/brent/cronoutput.log

I get the same output in the log either way

Any ideas?

---

### Post by ptviperz on 2009-08-21
I was able to get everything working by adding my command to /etc/crontab instead of using crontab -e

*/1 * * * * brent /home/brent/scripts/sabcheck.sh 2>&1 >> /home/brent/cronoutput.log


Any ideas why this same line wouldn't run out of crontab -e ?

---

### Post by DaithiF on 2009-08-21
Hi,

Hi,
> */1 * * * * root /home/brent/scripts/sabcheck.sh 2>&1 >> /home/brent/cronoutput.log
this wouldn't have worked in your own crontab as individual crontabs to not take a user parameter.  The only crontab which does take the user paramter is the /etc/crontab one.  In your own crontab the root would have been interpreted as part of the command to run, and most likely just errored out.

the second form you tried in your own crontab:```

*/1 * * * * /home/brent/scripts/sabcheck.sh 2>&1 >> /home/brent/cronoutput.log
```
should be equivalent to what you put later in /etc/crontab```

*/1 * * * * brent /home/brent/scripts/sabcheck.sh 2>&1 >> /home/brent/cronoutput.log
``` so i don't see why this wouldn't have worked.

Also, a minor point but */1 is redundant -- to run every minute just * would be fine.  If you wanted to run, say, every 2 minutes, then */2 would be what to use.

---

