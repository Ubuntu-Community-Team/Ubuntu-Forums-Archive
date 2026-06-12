---
title: "File system with errors, check forced"
date: 2009-03-11
forum: New to Ubuntu
---

### Post by Thurgood Stubbs on 2009-03-11
I'll try to be as descriptive as possible.

It may help to know that I am running Ubuntu 8.10 from wubi.

When I tried to start up my computer this morning, before the OS started, I got an error message somewhere along the lines of:

```
System has been started 35 times without file system check.

```
So I shut down by holding the power button and tried again.  This time I was told that

```
/lib/init/rw/rootdev contains a file system with errors check forced
```

The next error message was to long to copy down but it was somewhere along the lines of,

```
An automatic check failed, manual check required
``` 

So I went into Windows and did chkdsk, which came out fine, but I'm still unable to start Ubuntu.  What do I need to do to fix this?

---

### Post by cariboo on 2009-03-11
You should have let the system do what it wanted, it only takes a couple of minutes to check the hard drive for errors. 

You will now have to boot from the LiveCD in order to run fsck. Once booted to the desktop, open an Applications-->Accessories-->Terminal and type:

```
sudo fsck -a /dev/sda
```

Substitute your device label for /dev/sda in the above command. If you aren't sure what the device label is, in a terminal type:

```
sudo fdisk -l
```

you should get something that looks like this:

```
Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x51b6cc16

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       10199    81922048   83  Linux
/dev/sdb2           10200       10964     6144862+  83  Linux
/dev/sdb3           10965       11474     4096575   82  Linux swap / Solaris
/dev/sdb4           11475       30401   152031127+  83  Linux
```

You should be able to tell what the label for your partition is by looking for Linux.

Note: I am running a purely Ubuntu system, I dual boot between Intrepid and Jaunty. So I don't have any ntfs partitions.

Jim

---

### Post by Thurgood Stubbs on 2009-03-11
I did what you said, however after doing ```
sudo fdisk -l
```I couldn't tell which was Linux (as I said, because of the wubi installation, I don't have a seperate partition).  I think i did fsck on the right one, it took very little time then finished.  Now that I have tried to restart, I still have the same problem. I haven't been able to get the OS to start and I have the message```
*An automatic file system check (fsck) of the root file system failed.  A manual fsck must be performed, then the system restarted.  The fsck should be performed in maintenace mode with the root filesystem mmounted in read-only mode.
*The root filesystem is in read only mode.  A maintenance shell will now be started.  After performing sytem maintenace, press CONTROL-D to terminate the maintenance shell and restart the system.
bash: no job control in this shell
root@ubuntu:~#
```

---

### Post by Thurgood Stubbs on 2009-03-20
I'm sill stuck at the same point I was in the last post.

---

### Post by SunnyRabbiera on 2009-03-20
the system is supposed to check for errors, by aborting the check you might have caused more errors.
try the command sudo fsck, that should force another check.

---

### Post by Chemical Imbalance on 2009-03-20
What happened is normal.  Every Ubuntu install does this.

The purpose is to check your filesystem for bad blocks.

Next time it shows up, let it run.

---

### Post by meierfra. on 2009-03-20
To run a File system check on a Wubi install see:

[How can I access my Wubi install and repair my install if it won't boot?]("https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20access%20my%20Wubi%20install%20and%20repair%20my%20install%20if%20it%20won%27t%20boot?")

---

### Post by 123456789123456789123456 on 2009-03-20
if you get to the terminal screen, to type in, use fsck command.  that will check the file system

as far as partitions go.  tell me exactly where ubuntu is stored on the HDD.
for instance, if windows is c:, and ubuntu is the second partition, the ubuntu partiton in ubuntu should be sda2, listed as hd0,1 in its HDD listings.  sda1 should be listed as windows.  To make sure, thorugh live cd, go to the partion manager.  It will tell you, the sda information with what it is used for, windows, ubuntu, swap, so on.

---

### Post by Thurgood Stubbs on 2009-03-20
> **meierfra. said:**
> To run a File system check on a Wubi install see:

[How can I access my Wubi install and repair my install if it won't boot?]("https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20access%20my%20Wubi%20install%20and%20repair%20my%20install%20if%20it%20won%27t%20boot?")

This one worked for me.  Thanks.

---

### Post by randizzle on 2009-07-27
:guitar:

Rocking this thread because it saved me.

---

### Post by grey1beard on 2009-08-07
As a total newbie of considerable age but not wisdom, I managed to fix my 8.04/EMC2 boot up problem by using this.
For others like me, when the bottom line reads something like "Fix<y>?", trust it, and hit the enter key. :)

John

"It's like doing jigsaws in the dark"

---

