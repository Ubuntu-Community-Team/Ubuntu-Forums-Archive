---
title: "Mac to Ubuntu"
date: 2011-05-17
forum: New to Ubuntu
---

### Post by monkeypigs on 2011-05-17
Hi, 

I've just moved our house over from a mixture of Macs and Windows PCs to Ubuntu and loving it. 

One question though , on a mac, certain cron jobs are run overnight ("sudo periodic daily weekly monthly" in terminal will run them manually)

Does Ubuntu have similar tasks, if so, how can they be run manually?

If not, what maintenance tasks would people recommend to keep things in shape?

---

### Post by r-senior on 2011-05-17
If you look in /etc/cron.*, you'll find a series of directories that contain jobs (some scripts, some programs) that run hourly, daily, weekly and monthly.

There's no need to run these jobs manually.

As far as routine maintenance goes, there's not much to do, apart from keeping updated but Update Manager will do most of that for you.

There's a utility in the repositories called BleachBit that allows you to run various cleanup tasks but, again, that's not strictly necessary.

---

### Post by monkeypigs on 2011-05-17
Many thanks for the swift response. 

The cron jobs on a Mac run daily, weekly, monthly but during the dead of night, which is perfect if you leave your mac on 24/7!

Will investigate BleachBit as I like to tweak things! :p

---

### Post by r-senior on 2011-05-17
The default setup on Ubuntu uses this crontab:

```
17 *	* * *	root    cd / && run-parts --report /etc/cron.hourly
25 6	* * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6	* * 7	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6	1 * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )

```

So, apart from the hourly, they are between 6am and 7am.

---

### Post by monkeypigs on 2011-05-17
> **r-senior said:**
> The default setup on Ubuntu uses this crontab:

```
17 *    * * *    root    cd / && run-parts --report /etc/cron.hourly
25 6    * * *    root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6    * * 7    root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6    1 * *    root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )

```So, apart from the hourly, they are between 6am and 7am.

So I presume if I run

```
sudo  run-parts --report /etc/cron.daily
```That will run the job manually as our machines are rarely on at that time of the morning!

---

### Post by r-senior on 2011-05-17
I think anacron handles that. Without grubbing around I don't recall exactly how, but I believe it makes sure that it runs all the jobs that are scheduled. On my laptop for example, I never run these jobs manually and logs are rotated and so on.

---

### Post by monkeypigs on 2011-05-17
In which case I'll leave well alone! :P

---

### Post by Dondermans on 2011-05-17
> **monkeypigs said:**
> Many thanks for the swift response. 

The cron jobs on a Mac run daily, weekly, monthly but during the dead of night, which is perfect if you leave your mac on 24/7!

Will investigate BleachBit as I like to tweak things! :p

There are three tasks that come to mind that I do periodically:

1. Download system updates, which you can configure -in 10.10- through System -> Administration -> Update Manager -> Settings
2. Check integrity of the file system, this is done automatically after *x* times of booting or after *x* days pass.
3. Make regular backups. I use Déjà Dup Backup.

I only had to pick a program to make backups, the other tasks are automated. Perhaps you would like to share which cron jobs ran on your Mac. When you've done that it is easier to check if there is an Ubuntu equivalent and what steps - if any - you need to take now that you've switched to Ubuntu.

---

### Post by monkeypigs on 2011-05-17
Taken from [http://www.thexlab.com/faqs/maintscripts.html#Anchor-The-11481](http://www.thexlab.com/faqs/maintscripts.html#Anchor-The-11481)

> 

[LIST]
[*]The daily  script removes old log files, "scratch" and "junk" files, backs-up the  NetInfo database (Mac OS X 10.4 Tiger® and earlier), reports a variety  of system and network statistics, and rotates the system.log file. Under Tiger, the daily script also cleans up scratch fax files and prunes asl.log, the log file for the then-new [Apple System Logging]("http://developer.apple.com/documentation/Darwin/Reference/ManPages/man3/asl.3.html") facility.   Under Mac OS X 10.5 Leopard®, the daily script also prunes the asl.db file that replaced the asl.log file for Apple System Logging.
[*]The weekly script rebuilds the [locate]("http://developer.apple.com/documentation/Darwin/Reference/ManPages/man1/locate.1.html") and [whatis]("http://developer.apple.com/documentation/Darwin/Reference/ManPages/man1/whatis.1.html") databases.  Depending on the version of Mac OS X, it also rotates the following log files: ftp.log, lookupd.log, lpr.log, mail.log, netinfo.log, ipfw.log, ppp.log, and secure.log
[*]The monthly script reports per-user usage accounting and rotates — depending on the version of Mac OS X — the wtmp, install.log, and cu.modem.log files.
[/LIST]


---

