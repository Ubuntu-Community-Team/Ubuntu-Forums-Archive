---
title: "Problem/unable to booting after update"
date: 2010-01-19
forum: New to Ubuntu
---

### Post by radamez85 on 2010-01-19
Im still relatively new to Ubuntu but I have been using Ubuntu successfully on my newer computer. 

But recently I gave my brother a 5 year old computer with Ubuntu already on it.

Now when i boot up my bro's laptop i get 7 options.

Ubuntu, Linux 2.6.31-17-generic 
Ubuntu, Linux 2.6.31-17-generic(recovery mode)
Ubuntu, Linux 2.6.31-16-generic 
Ubuntu, Linux 2.6.31-16-generic(recovery mode)
Ubuntu, Linux 2.6.31-14-generic 
Ubuntu, Linux 2.6.31-14-generic(recovery mode)
Microsoft Windows XP Home edition (on/dev/sda1)

My brother 's laptop had always had success running on the 3rd option "Ubuntu, Linux 2.6.31-16-generic", and couldnt run the runs above it. And recently Ubuntu downloaded an update to my brothers computer, and now he has that Ubuntu, Linux 2.6.31-17-generic option and the Ubuntu, Linux 2.6.31-16-generic option no longer worked so now he uses Ubuntu, Linux 2.6.31-14-generic until today when it competely stopped letting him log in.

When we try and go to the first one, it just re boots and brings us back to this screeen with options.

When we try and use 14 option we get a black screen witht he following.

[Linux-bzImage, setup=0x3400, size 0x3b26e0]
[Initrd, addr=0x2f891000, size0x78a47e]
Mount of filesystem failed.
A maintenance shell will now be started.
Control-D will terminate this shell and re-try.
root@ubuntu:~#

---

### Post by LowSky on 2010-01-19
Ah... I have seen this before, what I think has happened is the BIOS Date and Time do not match the last save point of the hard drive causing the failure. Check BIOS to see if the time is Correct and when you boot and  get to root@ubuntu:~#
run this command

```
fsck
```

Also you should be able to use the newer versions, as they are safer. 
If you can boot to recovery mode 

Why your sytem is breaking is becasue those older Kernels might not run because of dependencies. New programs need the newer Kernels.

---

### Post by FitzChivalry28 on 2010-01-19
Hi, I'm the brother of the thread maker. I tried it:

[Linux-bzImage, setup=0x3400, size 0x3b26e0]
[Initrd, addr=0x2f891000, size0x78a47e]
Mount of filesystem failed.
A maintenance shell will now be started.
Control-D will terminate this shell and re-try.
root@ubuntu:~#_** fsck**_
[B]fsck from util-linux-ng 2.16
e2fsck 1.41.9 (22-Aug-2009)
One or more block group descriptor checksums are invalid. Fix(y)?[/B]

Bold, underlined word is what I typed and the bold is what came from that after typing what was recommended. Any ideas?

---

### Post by FitzChivalry28 on 2010-01-19
I pressed y and I got this:

> Group descriptor 24 checksum is invalid. FIXED.
/host/ubuntu/disks/root.disk contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking reference counts
Pass 4: Checking reference counts
Unattached inode 136716
Connect to /lost+found<y>?

Now if do this, they'll ask me about > Inode 136716 ref count is 2, should be 1. Fix<y>?

Unattached inode 136841
Connect to /lost+found<y>? yes

Inode 136841 ref count is 2, should be 1. Fix<y>?

And the question repeats, over and over, with different numbers. Am I saying yes to everything, and for how long? And I'd like to try and resolve any problems with Ubuntu now before I try Windows XP.

---

### Post by FitzChivalry28 on 2010-01-19
Tried fsck, tried runing it manually, pressed y to everything, and it still isn't working. When I reboot it, it actually loaded to XP, which I canceled, proceeded to reboot it again, and I tried booting Ubuntu, only to run into the same problem, and now with a message that says that Windows XP was safely closed. Any other ideas?

---

### Post by radamez85 on 2010-01-19
anything?

---

