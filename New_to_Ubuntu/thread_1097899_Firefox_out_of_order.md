---
title: "Firefox out of order"
date: 2009-03-16
forum: New to Ubuntu
---

### Post by geltonas on 2009-03-16
Hi, I got problem with firefox:
I can't go one page back and forward
It doesn't remember my last visited pages
I unable to make a bookmark

I have check my sda space:
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             178G   39G  131G  23% /
tmpfs                1012M     0 1012M   0% /lib/init/rw
varrun               1012M  224K 1012M   1% /var/run
varlock              1012M     0 1012M   0% /var/lock
udev                 1012M  2.8M 1009M   1% /dev
tmpfs                1012M  876K 1011M   1% /dev/shm
lrm                  1012M  2.0M 1010M   1% /lib/modules/2.6.27-11-generic/volatile

I have tried to reinstall Firefox but it gives me nothing.
So..Where is the problem?
THANK YOU

---

### Post by dje on 2009-03-16
open a terminal (Applications >> Accessories >> Terminal) and run the following command to backup your current firefox settings and then allow firefox to start fresh:
```
mv ~/.mozilla ~/.mozilla.bak
```
then start firefox again and see if it works

dje

---

### Post by geltonas on 2009-03-16
nope, it doesn'twork, whata hell is going on? I dont want to do reinstall ubuntu, it would be like windows thing..

---

### Post by KayakJim on 2009-03-16
In Firefox's address bar type about:config

In the filter box type: backspace

Double-click the browser.backspace_action entry and set it to 0.

---

### Post by dje on 2009-03-16
can you please post the output of:
```
ls -la ~ | grep .mozilla
```

dje

---

### Post by kanikilu on 2009-03-16
I had what sounds like a very similar problem. I believe the problem was fixed by creating a new Firefox profile, which I think dje already suggested.

Try the built-in profile manager:

[http://support.mozilla.com/en-US/kb/Managing+Profiles](http://support.mozilla.com/en-US/kb/Managing+Profiles)

---

