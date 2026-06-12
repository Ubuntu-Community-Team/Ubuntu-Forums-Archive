---
title: "Ubuntu Partition not showing space I allocated it"
date: 2009-09-25
forum: New to Ubuntu
---

### Post by andycullen on 2009-09-25
Hi all.

I set up Ubuntu as a dual boot on my laptop and when i set up the partition I allocated it 30GB of the 250GB hard drive. Ubuntu installed fine and started up. Now tho when I go to do a```
 sudo apt-get update
``` it says that there isnt enough space. 

So I am new to Ubuntu and I can not really find out where I need to go to check what space has baan allocated for my Ubuntu OS. I want it to be 30GB so I wont have the problem of not having enough space for these updates and also enough room to strech its legs. I do have access to the hard disk from Ubuntu.

Any help and time will be very much appriciated. 

Thanks

---

### Post by Liolikas on 2009-09-25
It would be nice to see your hdd layout:
go to terminal and type in:
sudo fidsk -l
copy paste output here.

---

### Post by drs305 on 2009-09-25
Run this command:
```
df -h
```

If it shows less than 3 GB for your Ubuntu partition, you will have to either reinstall or resize the partition. There is a bug in the install program. In Step 4 if you choose "side by side" the default partition is too small to run Ubuntu.

I've written two guides that explain your options:

If you have a 2.5 GB partition and want to reinstall:
[HOWTO: 2.5 GB System Partition - What Went Wrong?]("http://ubuntuforums.org/showthread.php?p=7658271")

If you have a 2.5 GB partition and want to resize the partition:
[Expanding an Ubuntu System Partition]("http://ubuntuforums.org/showthread.php?t=1219270")

If you have a normal partition size (10GB) and want to find out what is taking up so much space, refer to this guide:
[Recover Lost Disk Space]("http://ubuntuforums.org/showthread.php?t=1122670")

---

### Post by Cypher on 2009-09-25
Also on the teriminal type
```

df -h

```
to see your disk usage..that will quickly show you what's going on..

---

### Post by andycullen on 2009-09-25
Cool. Yeah it seems I got duped by the same thing as others. I did a re-install and I have my 30GB now. It is handy to know how to re-do the partitions as well.

Thanks to all for you help. 

When I do a df -h now this is what I get.

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              32G  2.4G   28G   9% /
tmpfs                1003M     0 1003M   0% /lib/init/rw
varrun               1003M   80K 1003M   1% /var/run
varlock              1003M     0 1003M   0% /var/lock
udev                 1003M  144K 1003M   1% /dev
tmpfs                1003M   76K 1003M   1% /dev/shm
lrm                  1003M  2.4M 1001M   1% /lib/modules/2.6.28-11-generic/volatile

```

Thanks again.

---

### Post by drs305 on 2009-09-25
andycullen,

Yes, that looks like a normal install.

If you don't mind, you can mark the thread SOLVED by clicking on the *Thread Tools* link at the top right of the first post. You can also remove the SOLVED tag from the same place - hopefully that won't be necessary.

Anyway, sorry it took two installs, but welcome to Ubuntu and the Ubuntu Forums.  :P

---

