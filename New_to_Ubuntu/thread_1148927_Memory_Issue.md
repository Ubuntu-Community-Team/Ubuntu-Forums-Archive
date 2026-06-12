---
title: "Memory Issue"
date: 2009-05-04
forum: New to Ubuntu
---

### Post by Alexn78666 on 2009-05-04
I'm new to Ubuntu, and Linux in general. I literally just set up a dual-boot for my computer, using Vista (grr.) and, obviously, Ubuntu.. (9.04)
 And, go figure, I have a question..
Upon booting Jaunty for the first time, the Update Manager opened up with some updates.. When I try to download the updates, I get a message saying I don't have enough free space. I checked the File Browser, and it shows I have 550+ gigs free space, so i'm wondering why I "don't have enough free space".. Do the updates automatically go on my hard drive, or are they set to go somewhere else where I should have free space? If the latter, I probably screwed up the partitioning..

---

### Post by taurus on 2009-05-04
What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
df -h
```

---

### Post by Alexn78666 on 2009-05-04
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             2.3G  2.3G     0   100% /
tmpfs                 2.3G      0      2.3G   0% /lib/init/rw
varrun                2.3G   108K   2.3G   1% /var/run
varlock               2.3G     0      2.3G   0% /var/lock
udev                  2.3G    164K   2.3G   1% /dev
tmpfs                 2.3G     76K    2.3G   1% /dev/shm
lrm                   2.3G      2.7M    2.3G   1% /lib/modules/2.6.28-11-generic/volatile
/dev/sda2              12G   10G   1.6G  87% /media/FACTORY_IMAGE
/dev/sda1             685G  118G  568G  18% /media/HP

---

### Post by taurus on 2009-05-04
> **Alexn78666 said:**
> Filesystem            Size  Used Avail Use% Mounted on
**[COLOR="Red"]/dev/sda5             2.3G  2.3G     0   100% /[/COLOR]**
tmpfs                 2.3G      0      2.3G   0% /lib/init/rw
varrun                2.3G   108K   2.3G   1% /var/run
varlock               2.3G     0      2.3G   0% /var/lock
udev                  2.3G    164K   2.3G   1% /dev
tmpfs                 2.3G     76K    2.3G   1% /dev/shm
lrm                   2.3G      2.7M    2.3G   1% /lib/modules/2.6.28-11-generic/volatile
/dev/sda2              12G   10G   1.6G  87% /media/FACTORY_IMAGE
/dev/sda1             685G  118G  568G  18% /media/HP

Well, you only give yourself 2.3GB for root filesystem so basically you would max it out with the default install.

Meanwhile, you've got a bunch of free space on /dev/sda1.

---

