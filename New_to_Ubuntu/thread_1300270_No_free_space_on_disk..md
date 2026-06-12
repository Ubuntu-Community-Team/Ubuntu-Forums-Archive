---
title: "No free space on disk."
date: 2009-10-24
forum: New to Ubuntu
---

### Post by s-jwagone2 on 2009-10-24
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              16G   15G     0 100% /
tmpfs                 1.5G     0  1.5G   0% /lib/init/rw
varrun                1.5G  104K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G  2.8M  1.5G   1% /dev
tmpfs                 1.5G   12K  1.5G   1% /dev/shm
lrm                   1.5G  2.2M  1.5G   1% /lib/modules/2.6.27-15-generic/volatile
overflow              1.0M   32K  992K   4% /tmp

This is what I get in terminal when I put in df -h. 

I can't download flash player, new themes or anything else for that matter. 

I installed Ubuntu on a 16 GB partition. The ISO disk I used was from April, and I had 352 updates to do. I downloaded and installed them all. There is no way that they used up 16 Gigs! 

I keep getting messages that say "Not enough free space on disk".  
If you look above, under /dev/sda5 there is 0 Available, but under each category below there is free space. What does this mean?

---

### Post by cilynx on 2009-10-25
```
/dev/sda5 16G 15G 0 100% /
```

That shows that the partition is indeed pretty much full.  If you haven't cleaned up after your updates, try: 

```
sudo apt-get autoclean
```

That will dump all of the outdated packages that you don't need anymore from the archive.

If you want to see where your space is going, you can do:

```
du -hs /*
```

That will show you how much space each directory is taking up.  You can walk up the tree from there, investigating what's eating up space.

---

### Post by laidback on 2009-10-25
Have a look via Partition Editor ( System>Admin>Partition Editor ) to get a visual impression of the usage, my fresh install of 9.04 with updates took about half your drive as far as I remember and just recently I've also installed 9.04 on a 10Gb drive with no problems.

Applications>Accessories>Disk Usage Analyser might also help with a visual impression.

---

### Post by s-jwagone2 on 2009-10-25
Thanks for all the help!

---

