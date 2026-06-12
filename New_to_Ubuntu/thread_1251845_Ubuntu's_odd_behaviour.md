---
title: "Ubuntu's odd behaviour"
date: 2009-08-28
forum: New to Ubuntu
---

### Post by Sapfeer on 2009-08-28
Hi!

My system seems to going crazy... Yesterday it flushes some settings, some settings it leave... I can't find the link between the settings it had reset: some of these settings I made two days ago and system was working fine and some more than a month ago. System's log says nothing. Moreover, there is some strange record:
```
/var/log/syslog:Aug 27 23:13:06 lenovo-y510ka kernel: [    0Aug 27 23:17:01 lenovo-y510ka /USR/SBIN/CRON[7584]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
```A big term of time system did not record it activity... How I can find out what's going on?..

Any comments and advices are appreciated

Thanks in advance

---------------------------------------------------------------------------------------------------------------------------------------------
[ lenovo-y510ka@user Fri 28 Aug 2009 01:07:07 PM MSD ]
/home/user $ uname -a
Linux lenovo-y510ka 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 19:25:34 UTC 2009 x86_64 GNU/Linux

---

### Post by ptn107 on 2009-08-28
That log output is normal.  Cron (scheduler) is just doing it's job, in this case running all the scripts contained in /etc/cron.hourly.

---

### Post by QIII on 2009-08-28
It might be helpful to know specifically what "settings" or behavior has changed.

---

### Post by Sapfeer on 2009-08-28
> **ptn107 said:**
> That log output is normal.  Cron (scheduler) is just doing it's job, in this case running all the scripts contained in /etc/cron.hourly.
Did you notice two timestamps in the output?.. I suppose there should be at least two records instead one, but first message is cuted, begins at 23:13:06 and says something about kernel, but the next one begins after about 4 minutes, at 23:17:01 and it says about cron job... What happend between 23:13 and 23:17?..

---

### Post by Sapfeer on 2009-08-28
> **QIII said:**
> It might be helpful to know specifically what "settings" or behavior has changed.
For instance, 

[LIST]
[*]I've lost all my file-system bookmarks, which are stored in $HOME/.gtk-bookmarks file
[*]my torrent client (transmission) resets all the torrents I've downloaded and it starts to download them again and put it in the $HOME/Desktop directory instead the directory I specified in the client settings
[*]my terminal profile has changed a bit, but I quickly configured it again
[*]system monitor applet preferences was reset to its defaults
[*]weather setting in time applet was turned off and I lost my location so that I have to add it again
[*]preferences of battery applet had reset to its defaults
[*]firefox-3.0 package was broken so that I needed to reinstall it
[/LIST]
I think that's enough, but this can be not the full list of reset settings, I can miss something...

---

### Post by QIII on 2009-08-28
Have you recently:
Upgraded to a new version or installed a new version clean from disc?
Installed a new package?
Installed updates?
Had an update fail for any reason?
Been notified that you have broken packages or missing dependencies?
Installed anything as a back-port?
Deleted a package?
Installed third-party software that recompiled the kernel?
Added memory or made other hardware modifications?
Changed drivers?

What were you doing just before you noticed the changes happening?

What version of Ubuntu are you using?

---

### Post by jocko on 2009-08-28
I would guess you have a damaged file system, so you have lost some files. Schedule a fsck for the next boot by typing this in a terminal:
```
sudo touch /forcefsck
```
Then reboot and see if the fsck finds any errors.

---

### Post by Sapfeer on 2009-08-28
> **QIII said:**
> Upgraded to a new version or installed a new version clean from disc
Ten days ago...
> **QIII said:**
> Installed a new package
> **QIII said:**
> Installed updates
Maybe, but system worked fine some time after it...
> **QIII said:**
> Had an update fail for any reason
No
> **QIII said:**
> Been notified that you have broken packages or missing dependencies
Yes
> **QIII said:**
> Installed anything as a back-port
> **QIII said:**
> Deleted a package
> **QIII said:**
> Installed third-party software that recompiled the kernel
> **QIII said:**
> Added memory or made other hardware modifications
> **QIII said:**
> Changed drivers
No
 > **QIII said:**
> What were you doing just before you noticed the changes happening
I can't remember what I did before, but I noticed the changes after the system boot...
> **QIII said:**
> What version of Ubuntu are you using?
/home/user $ uname -a
Linux lenovo-y510ka 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 19:25:34 UTC 2009 x86_64 GNU/Linux

---

### Post by Sapfeer on 2009-08-28
> **jocko said:**
> I would guess you have a damaged file system, so you have lost some files. 
Nice idea... I will check my file systems at next reboot

---

