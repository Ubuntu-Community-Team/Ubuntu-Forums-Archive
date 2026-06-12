---
title: "Cron task confusion"
date: 2009-03-07
forum: New to Ubuntu
---

### Post by blairm on 2009-03-07
Hi,

Have a Python script I want to run as a cron task but failing miserably.
To test it I'm running every minute; eventually would run every 30 minutes. The output of crontab -l is

```
blairm@orpheus:~/Documents$ crontab -l
PATH=/usr/sbin:/usr/bin:/sbin:/bin
* * * * * /home/blairm/Documents/rsscollect2.py
blairm@orpheus:~/Documents$ 

```

It runs fine from the terminal with the command python rsscollect2.py

Looking in the system log, I'm getting the following:

```
2009-03-08 15:52:01	orpheus	/USR/SBIN/CRON[25267]	(blairm) CMD (/home/blairm/Documents/rsscollect2.py)
2009-03-08 15:52:01	orpheus	sSMTP[25269]	Unable to locate mail
2009-03-08 15:52:01	orpheus	sSMTP[25269]	Cannot open mail:25
2009-03-08 15:52:01	orpheus	/USR/SBIN/CRON[25261]	(blairm) MAIL (mailed 66 bytes of output but got status 0x0001 )
2009-03-08 15:53:01	orpheus	/USR/SBIN/CRON[25450]	(blairm) CMD (/home/blairm/Documents/rsscollect2.py)
2009-03-08 15:53:01	orpheus	sSMTP[25452]	Unable to locate mail
2009-03-08 15:53:01	orpheus	sSMTP[25452]	Cannot open mail:25
2009-03-08 15:53:01	orpheus	/USR/SBIN/CRON[25444]	(blairm) MAIL (mailed 66 bytes of output but got status 0x0001 )
2009-03-08 15:53:58	orpheus	dhclient	DHCPREQUEST of 10.1.1.3 on eth0 to 10.1.1.1 port 67
2009-03-08 15:53:58	orpheus	dhclient	DHCPACK of 10.1.1.3 from 10.1.1.1
2009-03-08 15:53:58	orpheus	dhclient	bound to 10.1.1.3 -- renewal in 148 seconds.

```

Can anyone give me a hint as to what I'm doing wrong?

Cheers,

Blair

---

### Post by blueridgedog on 2009-03-08
Is there something in the file that lets the system know to run it with the python interpreter?

Perhaps you can change your crontab to:

* * * * * python /home/blairm/Documents/rsscollect2.py

---

### Post by blairm on 2009-03-08
Thanks for that, works perfectly. 

Cheers,

Blair

---

