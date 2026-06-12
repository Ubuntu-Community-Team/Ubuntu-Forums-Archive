---
title: "backup software"
date: 2010-01-28
forum: New to Ubuntu
---

### Post by Matt26 on 2010-01-28
i'm looking for backup software for ubuntu 9.10 that has the ability to do the following, without having to restart the computer and use a specialized interface/environment:

- back up entire volumes/partitions
- back up data to a shared network drive on a Windows system
- schedule automated backups

does anyone have any suggestions?

---

### Post by HermanAB on 2010-01-28
Howdy,

Rsync is your friend.

Yes there exists a wide variety of complicated and hard to use backup programs, but rsync is a one liner.  So everybody that knows anything about anything, uses rsync.  

Install Cygwin on Windows and do rsync over SSH over the internet in complete safety.

...and if you want to schedule it then you drop your script into /etc/cron.daily.

This is one of those cases where the GUI approach is far more complicated than a script.

---

### Post by ikt on 2010-01-28
> **HermanAB said:**
> Howdy,

Rsync is your friend.

Yes there exists a wide variety of complicated and hard to use backup programs, but rsync is a one liner.  So everybody that knows anything about anything, uses rsync.  

Install Cygwin on Windows and do rsync over SSH over the internet in complete safety.

...and if you want to schedule it then you drop your script into /etc/cron.daily.

This is one of those cases where the GUI approach is far more complicated than a script.

Isn't back in time based on rsync?

---

