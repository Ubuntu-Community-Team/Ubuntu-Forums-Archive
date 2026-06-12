---
title: "Question about deleting junk files"
date: 2009-05-23
forum: New to Ubuntu
---

### Post by Wackjob on 2009-05-23
With Windows, you have to occasionally run a program like CCleaner to get rid of old registry entries, empty folders, temporary files, etc. Does one need to run any program to delete junk files in Ubuntu, similarly to Windows?

Does Ubuntu also accumulate "junk" files over time that need to be cleaned out?

---

### Post by oldos2er on 2009-05-23
Ubuntu has no registry, and /tmp is cleared on a reboot. If you don't want to keep package files from installed programs, you can run
```
sudo apt-get clean
```
and
```
sudo apt-get autoremove 
```
will delete dependencies for packages which are no longer installed.

---

### Post by zhhansen on 2009-05-23
Check out this particularly informational thread that addresses exactly what you are talking about

[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

---

