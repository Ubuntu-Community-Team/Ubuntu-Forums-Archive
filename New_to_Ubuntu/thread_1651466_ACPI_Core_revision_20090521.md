---
title: "ACPI: Core revision 20090521"
date: 2010-12-23
forum: New to Ubuntu
---

### Post by preetammn on 2010-12-23
Hi All,

This is my first thread in Ubuntu forums, but I have been using Linux from past 2 years occasionally. The form is too good for me to get into asking any questions as everything had answers already available. Today I couldnt get the answer so starting to post.


My system configuration is as below:

laptop : compaq presario V3425AU
Processor : AMD Athelon 64 bit
RAM : 3GB
Dual boot with windows XP.
Ubuntu : 9.10
Kernal versions:
2.6.31-22-generic
2.6.31-14-generic

I had installed the 9.10 recently after removing my WindowsVista. so with that install I had kernel "2.6.31-14-generic". Things seem to be working.

Then next thing was to update it with newer patches, with that patches newer kernel "2.6.31-22-generic" got installed. After this update I am seeing this issue.

The boot hangs most of the times after : ACPI: Core revision 20090521.

searching in one of the threads said something about updating BIOS which was not successful.

Strange behavior is I am able to boot full Ubuntu some times and then next time it will hang. If i check the message log dont find any info on the hangs.

_____________________________________________________________________________________________________________________________________________
[42-12-2010] 
_____________________________________________________________________________________________________________________________________________
I tried booting with "acpi=off nolapic" and the kernel boots but whole power management is down,the processor fans is running at very high speed, and the system hangs after few hours. As well by booting with this option the sound drivers are going wiered with pulse audio sound(echo sounds ) and video stuck while playing.

The log is as below:

Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
Mount-cache hash table entries: 256
Initializing cgroup subsys ns
Initializing cgroup subsys cpuacct
Initializing cgroup subsys memory
Initializing cgroup subsys devices
Initializing cgroup subsys freezer
Initializing cgroup subsys net_cls
CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
CPU: L2 Cache: 256K (64 bytes/line)
CPU 0/0x0 -> Node 0
tseg: 00abf80000
CPU: Physical Processor ID: 0
CPU: Processor Core ID: 0
mce: CPU supports 5 MCE banks
using C1E aware idle routine
Performance Counters: AMD PMU driver.
... version:                 0
... bit width:               48
... generic counters:        4
... value mask:              0000ffffffffffff
... max period:              00007fffffffffff
... fixed-purpose counters:  0
... counter mask:            000000000000000f
ACPI: Core revision 20090521

And after this it hangs............

I tried with with kernel below given kernel images and the result remains same.

linux-image-2.6.31-14-generic (this was my initial image which I installed now this is also having problems)
linux-image-2.6.31-19-generic
linux-image-2.6.31-21-generic
linux-image-2.6.31-22-generic
_____________________________________________________________________________________________________________________________________________

Can some one help me out understanding this issue and guide me to solution.

Thanks in advance.

- Preetam

---

### Post by fatharraxman on 2010-12-23
Welcome to Ubuntu forums, Happy new year, and Merry Christmas 
this is a bug mostly can you report it and see is this one is close to yours:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/561151](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/561151)

---

### Post by fatharraxman on 2010-12-23
> **preetammn said:**
> Hi All,

in Ubuntu forums everything had answers already available.

Yes, agree. Nothing is like UbuntuForums, I wish you could visit this [thread too]("http://ubuntuforums.org/showthread.php?t=1452368&page=1") 
good luck:P

---

### Post by preetammn on 2010-12-24
These two bugs are not what I am getting But one of them is related to ACPI. but its on a different kernel.

I will attach my logs that I get when booting with recovery mode with the main post.

---

### Post by preetammn on 2011-01-10
After searching for fix I have found that the Linux Kernel has this bug.
I have migrated to OpenSUSE just to check it behavior and its also having same problem.

disabling IRQ 7 is has issues when we turn off ACPI. Looks like we dont have any fix yet for this............... :(

---

