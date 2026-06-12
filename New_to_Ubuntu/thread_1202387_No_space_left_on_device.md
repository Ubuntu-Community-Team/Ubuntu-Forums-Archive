---
title: "No space left on device"
date: 2009-07-02
forum: New to Ubuntu
---

### Post by ltwinner on 2009-07-02
Ive just installed ubunu and followed all the default options during installation. However when I try to create a folder I get the following message "Error creating directory, no space left on device". I am able to create an empty file, however if I type even one letter into it and then try and save it I get a similar 'not enough space on device' type message. Anyone able to tell me what is going on as I presumed if I followed the default options when installing ubuntu everything would work fine?

---

### Post by frunns on 2009-07-02
Hmm... What's the output of df -h?

---

### Post by ltwinner on 2009-07-02
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             2.3G  2.2G     0 100% /
tmpfs                 1.5G     0  1.5G   0% /lib/init/rw
varrun                1.5G  112K  1.5G   1% /var/run
varlock               1.5G  4.0K  1.5G   1% /var/lock
udev                  1.5G  152K  1.5G   1% /dev
tmpfs                 1.5G   84K  1.5G   1% /dev/shm
lrm                   1.5G  2.4M  1.5G   1% /lib/modules/2.6.28-11-generic/volatile
overflow              1.0M   16K 1008K   2% /tmp

---

### Post by frunns on 2009-07-03
Well, yeah... You're drive is full, so no wonder you're experiencing problems. There are ways to change a current installations partitions, but I think you're better off re-installing and giving it some extra room during the partitioning.

---

### Post by XCan on 2009-07-03
> **ltwinner said:**
> Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             2.3G  2.2G     0 100% /


As seen your total ubuntu partition is 2.3 GB large. I guess the installer's default option fails it again.

---

