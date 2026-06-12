---
title: "boot error."
date: 2011-03-16
forum: New to Ubuntu
---

### Post by SRamsey313 on 2011-03-16
Hello I have done some searching on this subject before I decided to register and post. I found some things on the subject however the set-ups differ in my situation.   First let me state that im super new to Linux.  After reading some stuff about commands and such its like reading a foreign language. So I do appreciate anyone willing to help me tackle my issue.

I'm not dual booting, I have a small hard drive for testing. 40gb 
I install ubuntu 10.10 maverick everything works great. I play around a few hours shut down.  Turn the PC back on and I get the following:

Killed
Begin: Running/scripts/local-bottom...done
done.
Begin: Running/scripts/init-bottom....mount: mounting /dev on/root/dev failed: no such file or directory.
done.
mount: mounting /sys on/root/sys failed: no such file or directory 
mount: mounting /proc on/root/proc failed: no such file or directory
Target filesystem dont have requested /sbin/init.
no init found. Try passing init= bootarg.

Now so far i have had to reinstall 4 times. It appears I only get this error after installing security updates that says its available.  now when i start up i have many options which all give the above error.

load 2.6.35.22  (i may be wrong about the kernals numbers slightly going from memory.)
load 2.6.35.22 Safe mode
load 2.6.35.27
load 2.6.35.27 Safe mode
memtest
memtest with serial something blah blah blah. 

Again Thank you in advance for your help. I will be monitoring this post so i can nip this in the bud.

---

### Post by SRamsey313 on 2011-03-16
Also ran the following commands as seen in another post,

sudo e2fsck -C0 -p -f -v /dev/sdb1
sudo e2fsck -f -y -v /dev/sdb1


 the results:
ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sdb1
/dev/sdb1: The filesystem size (according to the superblock) is 9357824 blocks
The physical size of the device is 8256650 blocks
Either the superblock or the partition table is likely to be corrupt!


/dev/sdb1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
    (i.e., without -a or -p options)
ubuntu@ubuntu:~$ sudo e2fsck -f -y -v /dev/sdb1
e2fsck 1.41.12 (17-May-2010)
The filesystem size (according to the superblock) is 9357824 blocks
The physical size of the device is 8256650 blocks
Either the superblock or the partition table is likely to be corrupt!
Abort? yes



I guess what im really asking is: 
What is causing my problem?
How do i fix my problem rather constant install?
How do I prevent this problem in the future?

---

