---
title: "Updating clamav antivirus?"
date: 2009-04-15
forum: New to Ubuntu
---

### Post by st4 on 2009-04-15
How do I update my outdated version of clamav antivirus?

---

### Post by gandaran on 2009-04-15
do you have the clam antivirus gui installed (clamtk)?
run clamtk as root and you'll be able to update.

---

### Post by MrWES on 2009-04-15
> **st4 said:**
> How do I update my outdated version of clamav antivirus?


The warning you're getting is for the database engine only. The copy in the repositories runs perfectly fine. Freshclam daemon (clamav updater) should be running, and a
```
ps aux | grep freshclam
```
should show something like this:
```
clamav    5235  0.0  0.0   2984  1220 ?        Ss   Apr07   0:00 /usr/bin/freshclam -d --quiet

```
By default it checks for updates 24 times a day; once every hour.

Bill

---

### Post by st4 on 2009-04-15
This is what it shows

bill@bill-desktop:~$ ps aux | grep freshclam
clamav    7347  0.1  0.0   3264  1388 ?        Ss   13:07   0:04 /usr/bin/freshclam -d --quiet
bill      8245  0.0  0.0   3236   792 pts/0    S+   13:56   0:00 grep freshclam
bill@bill-desktop:~$

---

### Post by st4 on 2009-04-15
I ran another scan and it still says it's outdated.;)

---

### Post by MrWES on 2009-04-17
> **st4 said:**
> I ran another scan and it still says it's outdated.;)

Post the outdated message here; it's the engine that drives the defs that is outdated, not the defs themselves.

Also from the terminal try
```
sudo freshclam
```
It should return this:
```
administrator@ubuntu:~$ sudo freshclam
ClamAV update process started at Fri Apr 17 06:49:05 2009
WARNING: Your ClamAV installation is OUTDATED!
WARNING: Local version: 0.92.1 Recommended version: 0.95.1
DON'T PANIC! Read http://www.clamav.net/support/faq
main.inc is up to date (version: 50, sigs: 500667, f-level: 38, builder: sven)
daily.inc is up to date (version: 9250, sigs: 41314, f-level: 42, builder: ccordes)

```
Version 0.92.1 is the stable version from the repositories, it works fine.

Bill

---

