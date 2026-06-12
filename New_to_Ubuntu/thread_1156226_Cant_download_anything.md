---
title: "Cant download anything"
date: 2009-05-11
forum: New to Ubuntu
---

### Post by chrisKr on 2009-05-11
Hi, i have a problem.  I cant seem to be able to download anything.  If i attempt to download in mozilla the message comes up:
[B]
There is not enough room on the disk to save /tmp/hjsavspJ.part.

Remove unnecessary files from the disk and try again, or try saving in a different location[/B]

If i try to change the download location in Edit,Preferences,Main Download TO: i cannot write anything in the field, the cursor does not blink in there.  Everything else seems to work fine but the download field does not work.

I tried using arora but i get a network error and it does not download.  
I tried using opera but once i go to a download page opera changes into text only and i cant download.

Any ideas?  This is the second time this happened to me last time i reinstalled Ubuntu the problem went away but after a few hours came back.  Ps. i am using Ubuntu 9.04, Jaunty Jackapole.

Help, frustraded

---

### Post by tdreyer1 on 2009-05-11
How much free space do you you have on your / partition? Sounds like the drive or partition you installed to is a little too small.

---

### Post by Eisenwinter on 2009-05-11
How much free space does your /home partition have?

---

### Post by dje on 2009-05-11
please post the output from the terminal (Applications >> Accessories >> Terminal) of:
```
df
```

dje

---

### Post by chrisKr on 2009-05-11
I think you may be right.  I went to Places, Computer and it seems my Ubuntu installation is a 2.5GB partition.  I right clicked on it , went to properties and it says 2.3GB used, 0 bytes free.

Ok i understand that bit.  But i am an absolute beginner to Ubuntu but i am very enthusiastic to use it.

I need to know how to increase the partiotion - not too keen on deleting anything because i havnt downloaded much yet apart from a few essentials - to free up space.  

If someone could tell me how to do that.  In simple terms please

---

### Post by chrisKr on 2009-05-11
Output:

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda7              2403388   2361784         0 100% /
tmpfs                   250680         0    250680   0% /lib/init/rw
varrun                  250680       104    250576   1% /var/run
varlock                 250680         0    250680   0% /var/lock
udev                    250680       152    250528   1% /dev
tmpfs                   250680       300    250380   1% /dev/shm
lrm                     250680      2392    248288   1% /lib/modules/2.6.28-11-generic/volatile
overflow                  1024       548       476  54% /tmp
/dev/sda5              2403420   2351832         0 100% /media/disk

---

### Post by tdreyer1 on 2009-05-11
> **chrisKr said:**
> Output:

"
/dev/sda7              2403388   2361784         0 100% /
"

There it is! Your / partition is full. You will need to either reinstall or rejigger your partition scheme so you have more space. (that or get a bigger hard drive!)

---

### Post by tdreyer1 on 2009-05-11
Here are some articles on partitioning:
[LIST]
[*][http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[*][http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)
[*][https://lists.ubuntu.com/archives/ubuntu-users/2007-September/122978.html](https://lists.ubuntu.com/archives/ubuntu-users/2007-September/122978.html)
[*][https://help.ubuntu.com/9.04/installation-guide/i386/index.html](https://help.ubuntu.com/9.04/installation-guide/i386/index.html)
[/LIST]

---

