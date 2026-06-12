---
title: "END_REQUEST: I/O Error, DEV SR0, Sector...."
date: 2010-06-25
forum: New to Ubuntu
---

### Post by Chim Chim on 2010-06-25
OK I'm fed up with Ubuntu and I may have to stay with the evil empire that is MS if I can't resolve this!

Having lost everything on my C drive when I initially tried to load Ubuntu I've now got a working system with XP on. (see my previous thread!)

To make things simple I decided that I would install Ubuntu from the LiveCD (which works as a trail on a borrowed laptop).  All went well and I entered my details till it came to reboot when it came up with the above message for a load of sectors ending with 508320.  The PC then reboots and starts Ubuntu but then it asks for my password even though I had said to ignore that and then does not recognise the password.

The PC is 6yrs old and runs an AMD XP 2000 chip, 80GB hdd and 1256mb of RAM so it seems to meet the minimum system requirements.

---

### Post by Rubi1200 on 2010-06-25
Take a look at this:

[http://ubuntuforums.org/showthread.php?t=1015569](http://ubuntuforums.org/showthread.php?t=1015569)

Also, if you can, post the output from:

```
sudo fdisk -l
```

Lowercase L not 1

---

