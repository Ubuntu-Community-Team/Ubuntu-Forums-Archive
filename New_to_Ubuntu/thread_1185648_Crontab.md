---
title: "Crontab"
date: 2009-06-12
forum: New to Ubuntu
---

### Post by aabrego on 2009-06-12
Hi:

I've been using crontab to run a perl script which basically is used to download data from an NetRS receiver and once is downloaded automatically Rinex the data. I've tested the script from the terminal window and it run perfectly.

However, when using crontab, the script does download the data but it does not do anything else. I even corrected the symlink from the /bin/sh file (originally linked to the /bins/dash) and made a new link to the corresponding /bin/bash/ but still no good. 

Any ideas?

Regards,
Antonio

---

### Post by northern lights on 2009-06-12
How does the cronjob look like exacty?

Please copy/paste verbose command.

Try to run it via a terminal for instance, i.e. ```
time gnome-terminal script
```

Further does the script require root rights?

---

### Post by aabrego on 2009-06-15
Hi:

The cronjob that I run is as follows:

00 06 * * * perl /home/aabrego/ACP-GPS/Programs/NetRSDSAC01

From the terminal window I run the following command:

"aabrego@ipig:~$ perl /home/aabrego/ACP-GPS/Programs/NetRSDSAC01", and it runs perfectly executing all commands included in the script.

If you look at the script attached it seems that when the scripts runs using crontab, it ignore some commands or change the variables. For instance, the variable "$back" tells the script to go back X days and retreive the data from that day on. But with crontab it only goes back one day no matter what number I specify here; and the second flu is the variable "convert" which it seems that under crontab is changed to "no" since the script does not execute this portion.

Regards,

---

### Post by MrWES on 2009-06-15
> **aabrego said:**
> Hi:

The cronjob that I run is as follows:

00 06 * * * perl /home/aabrego/ACP-GPS/Programs/NetRSDSAC01

From the terminal window I run the following command:

"aabrego@ipig:~$ perl /home/aabrego/ACP-GPS/Programs/NetRSDSAC01", and it runs perfectly executing all commands included in the script.

If you look at the script attached it seems that when the scripts runs using crontab, it ignore some commands or change the variables. For instance, the variable "$back" tells the script to go back X days and retreive the data from that day on. But with crontab it only goes back one day no matter what number I specify here; and the second flu is the variable "convert" which it seems that under crontab is changed to "no" since the script does not execute this portion.

Regards,

Not an expert here, but I see the script loading some modules as root; maybe you need to use the root crontab:
```
sudo crontab -e
```
vs. the users crontab.

~Bill

---

### Post by aabrego on 2009-06-15
Hi:

I used "sudo crontab -e" and included the same line as in the "user crontab"; however I can't get crontab to run this way. Do I have to change something somewhere?

Regards,

---

### Post by unutbu on 2009-06-15
The NetRSDSAC01 script you posted has Windows-style line endings (CR/LF) instead of Unix-style line endings (LF). I'm not sure if this could cause the problem you are experiencing, but it would not hurt to install the tofrodos package and then run
```

dos2unix NetRSDSAC01
```

This will convert the file to unix-style line endings.

Maybe more likely to help would be this:

Change the crontab entry to 
```

* * * * * /usr/bin/perl /home/aabrego/ACP-GPS/Programs/NetRSDSAC01 1>/tmp/cron.out 2>&1
```

Wait a minute so the cron job will run, and then look in /tmp/cron.out for error messages.
If it isn't clear what the problem is after that, please post /tmp/cron.out and we can work from there.

---

### Post by aabrego on 2009-06-15
It seems that there is another problem on top to the original one. When running the cronjob using sudo I cannot CRON to work and therefore no cron.out file can't be created. When looking the system log it reads:

Jun 15......ipig-wks /usr/sbin/cron[5784]: (root) RELOAD (crontabs/root)
Jun 15......ipig-wks CRON[10010]: User account has expired 

and this goes on every time it try to run crontab.

However, if I run the same cronjob under "user" I get the following:

Jun 15......ipig-wks /usr/sbin/cron[9936]: (aabrego) RELOAD (crontabs/aabrego)
Jun 15......ipig-wks /USR/SBIN/CRON[10010]: (aabrego) CMD (usr/bin....../cron.out 2>&1)

---

### Post by unutbu on 2009-06-15
Regarding the error message
```

CRON[10010]: User account has expired 

```
see [http://www.teknynja.com/2008/09/obscure-ubuntu-tip-cron-user-account.html](http://www.teknynja.com/2008/09/obscure-ubuntu-tip-cron-user-account.html)

---

### Post by aabrego on 2009-06-15
Thank you very much for the tip.

Antonio

---

