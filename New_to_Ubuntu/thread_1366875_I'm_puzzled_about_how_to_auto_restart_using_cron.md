---
title: "I'm puzzled about how to auto restart using cron"
date: 2009-12-28
forum: New to Ubuntu
---

### Post by ptviperz on 2009-12-28
I'm trying to automatically restart my computer everyday at 5 in the morning. I've tried the following in /etc/crontab

```
*  5	* * * 	 root 	 /sbin/shutdown -r now
*  5	* * * 	 shutdown -r now
```

and tried a script....script runs fine but it won't run from cron

```
*  5	* * * 	 root 	 /home/brent/reboot.sh
```

The only error I've gotten in /var/log/syslog is something about 'Bad minute' but nothing is actually wrong with the entry. Everything else in cron works fine. ex: 
```

*/5   *	* * *    brent   /home/brent/scripts/remountpch.pl
*/5   *	* * *    brent   /home/brent/scripts/sabcheck.sh
15  * * * * 	 brent   /home/brent/scripts/yamj.sh
0  */2  * * *    brent   /home/brent/scripts/backup/bkemail.sh
3  */2  * * *    brent   /home/brent/scripts/backup/bkpics2008.sh
45 4	* * * 	 brent	 /home/brent/scripts/rebootpch.pl
```

Can anyone shed any light on why this isn't working? Thanks for your time.

---

### Post by falconindy on 2009-12-28
Look in /var/log/crond for messages about cron.

Also, not that it matters in concept, but the timeframe '* 5 * * *' will match every minute of the 5th hour. Surely, you meant '0 5 * * *'.

---

### Post by ptviperz on 2009-12-29
> **falconindy said:**
> Look in /var/log/crond for messages about cron.

Also, not that it matters in concept, but the timeframe '* 5 * * *' will match every minute of the 5th hour. Surely, you meant '0 5 * * *'.

I also tried it like

15 5 * * *

and I don't have a /var/log/crond

brent@brent-desktop:~$ cat /var/log/crond
cat: /var/log/crond: No such file or directory

---

### Post by glubbdrubb on 2009-12-29
It might be easier if you use a gui for cron like gnome-schedule or webmin. 

Webmin is great for just this sought of thing thogh it is quite big because it does so much more.

gnome-schedule should be in the software centre but webmin will have to be downloaded form form their website [http://www.webmin.com/](http://www.webmin.com/) .

---

### Post by ptviperz on 2009-12-29
> **glubbdrubb said:**
> It might be easier if you use a gui for cron like gnome-schedule or webmin. 

Webmin is great for just this sought of thing thogh it is quite big because it does so much more.

gnome-schedule should be in the software centre but webmin will have to be downloaded form form their website [http://www.webmin.com/](http://www.webmin.com/) .

I can try one of these but I'd really prefer just to throw a simple command in cron since I don't need any of the other capabilities of those programs. Is it really that difficult to do in cron? I can't be the only one who wants to reset the computer at a certain time

---

### Post by glubbdrubb on 2009-12-30
Well, it is confusing enough with a gui, so doing it in text is not going to be any easier. But if you figure out the correct formatting then good on you. Try the cron man pages if you have not already, by typing 

```
man cron
```
into a terminal.


Take a look at gnome schedule. It uses cron as the back end and is small and light so don't worry about being overrun with features.

---

### Post by b0b138 on 2009-12-30
shutdown needs to run as root, so you need put it in roots crontab

```
sudo crontab -e
```
and add ```
01 05 * * * /sbin/shutdown -r now
```

---

### Post by ptviperz on 2010-01-07
> **b0b138 said:**
> shutdown needs to run as root, so you need put it in roots crontab

```
sudo crontab -e
```
and add ```
01 05 * * * /sbin/shutdown -r now
```

I've been running in root's cron the whole time but it wasn't working correctly until I set the time as 

```
01 05 * * *
```

instead of 

```
1 5 * * *
```

Thanks for the solution though I don't see much of a difference between the statements.

---

### Post by lotharmat on 2010-01-07
> **ptviperz said:**
> I've been running in root's cron the whole time but it wasn't working correctly until I set the time as 

```
01 05 * * *
```

instead of 

```
1 5 * * *
```

Thanks for the solution though I don't see much of a difference between the statements.

Computers are pernickety blighters!!

---

