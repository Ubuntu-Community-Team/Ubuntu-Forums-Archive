---
title: "understanding disk usage"
date: 2011-06-17
forum: New to Ubuntu
---

### Post by Sillywhipper on 2011-06-17
Hi,

I've currently got a mysql db that crashes due to low disk space but I don't understand how to free up space, please see below:


root@leela:/# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/leela-root
                      9.2G  1.4G  7.4G  17% /
none                  4.0G  208K  4.0G   1% /dev
none                  4.0G     0  4.0G   0% /dev/shm
none                  4.0G   80K  4.0G   1% /var/run
none                  4.0G     0  4.0G   0% /var/lock
none                  4.0G     0  4.0G   0% /lib/init/rw
/dev/mapper/leela-home
                      9.2G  183M  8.6G   3% /home
/dev/md0              184M   73M  103M  42% /boot
/dev/mapper/leela-var
                      9.2G  8.8G     0 100% /var

The mysql db is in /var but when I take a look at /var I get:

root@leela:/# du -hs /var/
239M    /var/

Where is the 8GB of disk space for this partition??

Any help would be greatly appreciated.

---

### Post by 3xp10r3r|X13 on 2011-06-17
The problem lies in "/dev/mapper/leela-var" , because it is simply full (100% or 8.8 of 9.2 gb). But I guess you've already noticed that, pointing it out to us :). The thing you want to do now, is to boot from the live cd and extend that specific partition manually by assigning more, currently free, space to it (you've got some left don't you?). You can use any other partitioning tool, but it should be bootable from a cd/usb, because the OS won't let you play around with the partition when it's mounted. 

The /var partition contains your system logs (which can grow rapidly - trust me - that's why it is already filled up). However, this partition can be unmounted (I think), because it contains just all those logs and spools. 

to dismount a partition just open up a terminal, log in as root and type the following:

```

umount /dev/xy

```Just pick the specific partition you need to get rid of. After that you should be able to change it.

---

### Post by gdonwallace on 2011-06-17
Something else you might want to try before extending the /var partition is look at the individual directories under /var and see which one is the largest, and thus eating up all the space on /var partition.

You can use the command **sudo du -h --max-depth=1** The du command will tell you how much space is taken up by each directory, -h will put it in a format that is easier to read (i.e. megabytes instead of blocks) and with max-depth set to 1, it will only scan for the first level of directories.  My first thought is that the /log or /mail may be getting pretty big, so you may want to look at those first.  MySQL puts a large file in /var/log as it tracks the commands issued to MySQL, so that may be causing your problem.

---

