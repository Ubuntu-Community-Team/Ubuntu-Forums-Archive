---
title: "Routine Hard Drive Checks | Change Frequency"
date: 2010-07-15
forum: New to Ubuntu
---

### Post by EnigmaticCoder on 2010-07-15
After a certain number of boot-ups, Ubuntu automatically checks the disk drives for errors. Unlike the typical Linux user, I shutdown my computer when it's not in use, so the disc drives are checked more often than usual. While I see the need for the disks to be checked, I don't want them to be checked all that frequently.

One option would be to increase the number of boot-ups before the disk check is triggered, but there's a problem -- I sometimes boot up the computer several times a day and sometimes not at all. There isn't a strict pattern to my computer usage.

There is, however, a desired solution. What would be ideal is to make the disk check adhere to a *schedule*. I'd like the checks to be run every three weeks. Is it possible to configure the automatic disk checks to run that way?

---

### Post by CharlesA on 2010-07-15
You can use **tune2fs **to adjust when the disk is automatically checked.

I've got all mine to check once every month. :-)

---

### Post by ajgreeny on 2010-07-15
That's the way to do it!
```
sudo tune2fs -i 21d /dev/sd#x
``` where sd#x is your ubuntu root partition.

I use it to set my system to check every 60 boots.
See ```
man tune2fs
``` for all the options etc etc.

---

### Post by EnigmaticCoder on 2010-07-15
Thanks!

---

