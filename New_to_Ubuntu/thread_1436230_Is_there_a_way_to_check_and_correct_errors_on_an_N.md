---
title: "Is there a way to check and correct errors on an NTFS partition while running Ubuntu?"
date: 2010-03-22
forum: New to Ubuntu
---

### Post by diablo75 on 2010-03-22
I like to use Live CD/USB drives to run Ubuntu on machines for either demonstration purposes or for technical troubleshooting and repair purposes.  Accessing an NTFS drive is easy in the system, unless there is an error on that drive.  I've been having to use Windows Recovery CDs to boot into a Recovery Mode terminal and run chkdsk from there a couple times before Ubuntu will auto-mount it.  Is there a way to scan for and correct errors on a drive while running Linux so I wouldn't have to reboot under those particular circumstances?

---

### Post by bodhi.zazen on 2010-03-22
You can try ntfsfix

[http://manpages.ubuntu.com/manpages/lucid/en/man8/ntfsfix.8.html](http://manpages.ubuntu.com/manpages/lucid/en/man8/ntfsfix.8.html)

In my limited experience, however, ntfsfix is not as good as the repair tools in windows.

---

