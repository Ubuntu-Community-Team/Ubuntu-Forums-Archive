---
title: "sudo shutdown -h question"
date: 2010-12-15
forum: New to Ubuntu
---

### Post by rburkartjo on 2010-12-15
if i log onto my daughter's desktop and enter sudo shutdown -h 22:00 in the terminal. this will shutdown the computer at 10pm. okay question if both of us are logged in and i am using my desktop at 10pm will the command stilll be enabled. tks

---

### Post by TeoBigusGeekus on 2010-12-15
Yes I believe.
It will first kill your processes, log you out and then power off the pc.

---

### Post by wep940 on 2010-12-15
I have never tried a timed shutdown in Ubuntu, so not sure how it will work.  In the old Unix world, it would come up and tell you "The System Is Going Down In xx Minutes" warnings.  When the time was reached, it would then kill everything and shutdown.

---

### Post by NCLI on 2010-12-15
Yes, it will. Since it runs as root, it has permission to log off all other users.

It's no different from running "sudo shutdown -h now", all users will be logged off.

---

### Post by nothingspecial on 2010-12-15
Yes,

I, the evil father, do this all the time to my kids.

Have a look a timekpr

[https://launchpad.net/timekpr](https://launchpad.net/timekpr)

---

### Post by rburkartjo on 2010-12-16
tks ya'll i was about 95% sure i was right. also a big tks to not. just installed the app he suggested

---

### Post by Paqman on 2010-12-16
You might also want to take a look at Gnome Nanny, it's in the repos for Maverick and later.

---

### Post by rburkartjo on 2010-12-17
paq, tks will check that out

---

### Post by rburkartjo on 2010-12-18
not that timekpr program is great

---

