---
title: "how to have a program run at shutdown"
date: 2010-01-31
forum: New to Ubuntu
---

### Post by rburkartjo on 2010-01-31
what do i have to do to have the app bleachbit(a file cleaner run at shutdown or reboot) have no idea if this can be done or how to do it/tks

---

### Post by yknivag on 2010-01-31
You can use the @reboot syntax in cron to which will run the script everytime the machine starts up, I'm not sure if there is an @shutdown syntax also, there may be.

---

### Post by rburkartjo on 2010-02-13
tks yk did it this way
You can put in a call to the program for every user at logout. Edit (using sudo) the file

/etc/gdm/PostSession/Default

Probably it looks like this right now:

#!/bin/sh

exit 0

In between those lines, add this line:

/usr/bin/bleachbit

I never used bleachbit, but I installed it to make sure I have the right path.

The script should look like this when finished:

#!/bin/sh
/usr/bin/bleachbit
exit 0

The only downside is it may take logouts and shutdowns a little longer. The upside is it will work without you having to remember to run it.
from sinister midget

---

