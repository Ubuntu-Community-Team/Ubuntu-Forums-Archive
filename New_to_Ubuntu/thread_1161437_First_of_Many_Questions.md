---
title: "First of Many Questions"
date: 2009-05-16
forum: New to Ubuntu
---

### Post by Bigeasy on 2009-05-16
Howdy folks, 

Well after one too many BSOD's from Windows, I decided it was time to wipe the system on my laptop and start anew. This time however, I wanted to take the opportunity to try Linux. So I partitioned my hard drive (60GB) into two 30GB sections. I installed widows XP, and then installed Ubuntu. Windows is going to be for work, and Ubuntu is going to be for learning and play. 

From my brief experience with Linux, its like a Windows machine and a Mac had an offspring that could be considered by many to be the next messiah. Ive never had an easier experience in getting all my drivers to work, and the GUI is more than impressive. However, I've hit my first snag.

It seems that my home directory(the one with my username) has run out of space. I first noticed a problem when Ubuntu would not log me on automatically to my wifi. Also it appears that the navigation buttons on firefox have ben greyed out. Concerning firefox, with the shortcut to the google search up on the tool bar, no entries will search, meaning that whenever I hit enter nothing happens. I have done quite a bit of searching on this and have had little luck even finding what the problem is. Could it be related to the lack of physical memory?  

Now this had me greatly confused at first because there was no way I had installed 30 gigs worth of applications. After a little digging, ive noticed that the bulk of my physical memory is mouted as an external divice. Is this normal for Linux? As it stands now, I cannot do much of anything, not even the janitor application. Is there any way I can allocate more memory to my home folder?

Thank you all for your time,
Bigeasy

---

### Post by mikewhatever on 2009-05-16
I suggest starting by posting the output of **df -h** command from Application->Accessories->Terminal. You can do it either from the Ubuntu installation or the live cd.

---

### Post by Bigeasy on 2009-05-16
Im having to write this from a different computer because firefox on my Linux is not allowing me to log in to this website. 

Filesystem                Size       Used   Avail  Use%  Mounted on
/dev/sda6                2.3G       2.3G              0  100%  /
tmpfs                             750M                0    750M         0%  /lib/init/rw
varrun          750M      100K   750M         1% /var/run
varlock                      750M                 0    750M         0% /var/lock
udev                               750M     160K    750M         1% /dev
tmpfs                            750M        76K    750M         1% /dev/shm
lrm                                   750M       2.4M    750M         1% /lib/modules/2.6.28-11-generic/vola
tile
overflow                     1.0M   160K     864K       16% /tmp
/dev/sda2                27G       5.3G       22G         20% /media/disk

---

### Post by mikewhatever on 2009-05-16
Well, it looks like you root partition is only 2.3 GB and is now full.
> /dev/sda6 2.3G 2.3G 0 100% /

There is also a 27 GB partition you probably intended using.
```
/dev/sda2 27G 5.3G 22G 20% /media/disk 
```

I think it's the easiest to delete all but the first partition and reinstall Ubuntu properly, giving it the available space.

---

### Post by Bigeasy on 2009-05-16
I was hoping this was not the case, but oh well...all part of the learning process I guess. 

Thank you very much for your help

---

### Post by mikewhatever on 2009-05-16
> **Bigeasy said:**
> I was hoping this was not the case, but oh well...all part of the learning process I guess. 

Thank you very much for your help

Perhaps there is a way to merge sda2 and sda6. Are they right next to each other?

---

### Post by sandyd on 2009-05-16
> **mikewhatever said:**
> Perhaps there is a way to merge sda2 and sda6. Are they right next to each other?
do a 
```

sudo fdisk -l

```

---

