---
title: "not enough disk space"
date: 2009-07-08
forum: New to Ubuntu
---

### Post by andreas.wpv on 2009-07-08
Vista 64 bit, ubuntu 9.04 in different partition, 20 GB incl. swap.

Try to update packages, get the message not enough space. Check space and it shows this:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              19G   18G     0 100% /
tmpfs                 1.5G     0  1.5G   0% /lib/init/rw
varrun                1.5G  104K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G  164K  1.5G   1% /dev
tmpfs                 1.5G  472K  1.5G   1% /dev/shm
lrm                   1.5G  2.4M  1.5G   1% /lib/modules/2.6.28-11-generic/volatile
overflow              1.0M   16K 1008K   2% /tmp
/dev/sdb1              31M     0   31M   0% /media/disk

I see that /dev/sda3 is full, but this is a fresh install? 
I 'imported' windows settings, and files, did it really copy these files? That might be a reason. If it did copy, where do I find these files?

If it did not copy, what can make this partition full? 

How can \ be full if all the directories are empty?
Please help!

---

### Post by philinux on 2009-07-08
Ubuntu takes up about 3.5 gig on a fresh install. 

Have a look through some of these. Many people have fallen foul of this one.

[http://www.google.co.uk/search?q=ubuntu+forums+not+enough+disk+space&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.co.uk/search?q=ubuntu+forums+not+enough+disk+space&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

### Post by andreas.wpv on 2009-07-08
Thanks for the link, I have gone through several searches in google, msft, ubuntu regarding this. That's how I found out about how to get the data I posted. I have seen no real answer out there. 

1. Increase size? No, why does a fresh install take 19 GB? 
I 'imported' windows settings, and files, did it really copy these files? That might be a reason. If it did copy, where do I find these files?
2. If it did not copy, what can make this partition full? 

3. How can root be full if all the directories are empty?

---

### Post by earthpigg on 2009-07-08
> **andreas.wpv said:**
> 
3. How can root be full if all the directories are empty?

well, something is obviously taking up space... lets find out what, and where.

unplug any external hard drives or thumb drives, and:

applications -> accessories -> dusk usage analyser -> scan filesystem.

click around a bit, find out what's taking up your space.

---

### Post by andreas.wpv on 2009-07-18
Cool beans, that has helped a lot. I found that the import actually imported all data instead of building file links. So, I checked and deleted, have wide open space now. 
Thanks!

---

