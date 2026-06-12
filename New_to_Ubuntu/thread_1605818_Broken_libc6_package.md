---
title: "Broken libc6 package"
date: 2010-10-25
forum: New to Ubuntu
---

### Post by fleamour on 2010-10-25
I have restored from older Xubuntu image with Clonezilla, 10.10 upgrade not working out very well.  When Update Manager refused to patch new upgrades.

I have used Synaptic which locates broken package as libc6.  I get error when upgrading from 7.2 to 7.5, stating segmentation fault, error when processing man-db.

"E: /var/cache/apt/archives/libc6_2.11.1-0ubuntu7.5_i386.deb: subprocess new pre-installation script killed by signal (Segmentation fault)"

Apport has reported a bug, but other than that I am unsure how to proceed as libc6 is used by almost all the packages on system according to Synaptic overview.

---

### Post by fleamour on 2010-10-25
```
sudo apt-get purge

sudo apt-get -f install
```

Only resets things.  This is error output of Update Manager:

"Segmentation fault
(Reading database ... 110581 files and directories currently installed.)
Preparing to replace e2fslibs 1.41.11-1ubuntu2 (using .../e2fslibs_1.41.11-1ubuntu2.1_i386.deb) ...
Unpacking replacement e2fslibs ...
Setting up e2fslibs (1.41.11-1ubuntu2.1) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 110581 files and directories currently installed.)
Preparing to replace e2fsprogs 1.41.11-1ubuntu2 (using .../e2fsprogs_1.41.11-1ubuntu2.1_i386.deb) ...
Unpacking replacement e2fsprogs ...
Processing triggers for man-db ...
dpkg: error processing man-db (--unpack):
 subprocess installed post-installation script killed by signal (Segmentation fault)
Errors were encountered while processing:
 man-db
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up man-db (2.5.7-2) ...
dpkg: error processing man-db (--configure):
 subprocess installed post-installation script killed by signal (Segmentation fault)
Setting up e2fsprogs (1.41.11-1ubuntu2.1) ...
Errors were encountered while processing:
 man-db"

---

### Post by bioterror on 2010-10-25
Seems like your apt is really really messed up.
There could be some kind of help if it wouldnt segfault.

I might consider a reinstallation from a USB stick or optical media if I were you.

Do you have lots of important files which you cannot move to safe?
Becouse if you do, then we might have to think something ;)

---

### Post by fleamour on 2010-10-26
I was thinking along the lines of re-installation with latest CD image.  

Not sure if have separate home directory or not?  A very light user anyhow, so not that much that cannot be salvaged or downloaded again.

---

### Post by bioterror on 2010-10-26
> **fleamour said:**
> I was thinking along the lines of re-installation with latest CD image.  

Not sure if have separate home directory or not?  A very light user anyhow, so not that much that cannot be salvaged or downloaded again.

In terminal if you say "df -h" it will prompt you something like this:

```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             100M   50M   50M  50% /boot
/dev/sda2             906G  783G   77G  92% /
/dev/sdb1             466G  403G   63G  87% /home/

```

if you have your /home mentioned there, it will be on a whole different partition or even a disk as in my example.

---

### Post by beew on 2010-10-26
I think a reinstallation is probably the way to go. But if you don't want that or just want to experiment you can try downgrade libc6 and then upgrade again and see if it works.  First you need to have a version to downgrade to, so you may add the Lucid repository (check out which one has libc6) to your source list, or any ppa that has an earlier version of the libc6 package. reload and then open Synaptic, locate lib6c and highlight it, then go to package > forced version. Pick a lower version and install that. The program manager would remove a bunch of stuffs, downgrade others and there may be some broken dependencies which you can remove later on if they are still broken after the downgrade (in my experience they often got fixed) then after that  remove the Luicd repository and try to upgrade lib6c again and see what happens.

---

### Post by bioterror on 2010-10-26
I think that those segmentation faults wont disappear.
Even how hard he tries to downgrade his glibc6.

But if you go with that, I'm eager to hear how it went.

---

