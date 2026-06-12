---
title: "why can't I get crontab to work"
date: 2010-02-07
forum: New to Ubuntu
---

### Post by bnhrobotics on 2010-02-07
I have tried on different computers to no avail. How do I get crontab to work?

I type > crontab -e

Then I add a line like :
*/1 * * * * echo test
or
5 * * * * python /path/to/my/python/script

Then I save the crontab and exit. Nothing ever seems to run. What am I doing wrong?

I have also tried the -u user option to do a root crontab. That doesn't work either.


Nevermind. echoing doesnt show up on the terminal and my python script was actually running...

---

### Post by x33a on 2010-02-07
you can redirect echo to the terminal of your choice (provided it is open).

first open a terminal and note its tty.
```
tty
```

then to get echo to work, try
```
echo "hello" > /dev/pts/1
```

assuming /dev/pts/1 is your terminal.

---

