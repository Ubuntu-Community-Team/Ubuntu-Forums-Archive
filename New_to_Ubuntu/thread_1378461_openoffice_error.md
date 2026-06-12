---
title: "openoffice error"
date: 2010-01-11
forum: New to Ubuntu
---

### Post by kamitsukai on 2010-01-11
getting this error from all openoffice applications
[B]
from terminal[/B]
```
carl@carl-laptop:~$ ooffice -writer %F
[Java framework] Error in function createSettingsDocument (elements.cxx).
javaldx failed! 
```

**and from the application**
```
The application cannot be started. 
The user interface language cannot be determined.
```Thanks in advance!

I'm using ubuntu 9.10

---

### Post by ajgreeny on 2010-01-11
I suggest you rename your hidden home folder **~/.openoffice.org** as **~/.openoffice.orgbak** and open the office application again.  You will need to shutdown the quickstarter icon if you use it as well, or perhaps log out and in again before restarting OOo.

Open office should then start perfectly ok, though you may need to reset all your old configuration for it.  You could always try renaming the sub folders one by one, until you get to the one that causes the problem.

---

