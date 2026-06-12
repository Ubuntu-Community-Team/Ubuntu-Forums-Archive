---
title: "OpenSSH-Client error report"
date: 2011-01-16
forum: New to Ubuntu
---

### Post by Infinitylantern on 2011-01-16
E: Problem parsing dependency Depends
E: Error occurred while processing openssh-client (NewVersion1)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

any Thoughts?

---

### Post by taseedorf on 2011-01-16
Yep...
try rebooting,..then

sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade

If this works, please mark this thread as solved.

---

### Post by Infinitylantern on 2011-01-17
Worked Thanks

---

