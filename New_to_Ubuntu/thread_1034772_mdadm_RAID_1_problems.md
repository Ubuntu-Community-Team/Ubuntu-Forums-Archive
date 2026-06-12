---
title: "mdadm RAID 1 problems"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by triciens on 2009-01-09
Hello!

I'm completely new to Linux and Ubuntu and am having some difficulties setting up RAID 1.

I have 4 hard drives. I'm trying to set them up in RAID 1 like this:

HDD 1: /home
HDD 2: /home

HDD 3 partition a: /
      partition b: SWAP
HDD 4 partition a: /
      partition b: SWAP

I used the Alternate Install CD and followed the instructions here:

[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

The installation completed successfully. However, when installation was complete and my PC restarted, I got a whole lot of text coming up on the screen. Among other things, it said:

[B]"bootdegraded=true"

Alert: /dev/md1 does not exist. Dropping to a shell.[/B]

There was a Y/N option to ignore the degrade and try to load the OS, so I pressed Y and Ubuntu loaded. I know the hard drives are fine. 

Do you have any idea what the problem could be? I checked in the terminal and the raid state is "clean, degraded".


PS: I ran "swapon -s" to see if my swap was working but all I got was an empty table (filename, type, size, used, priority). It shouldn't be like that, should it?

---

### Post by geforce123 on 2009-01-09
What is the output of

```
cat /proc/mdstat
```

---

### Post by triciens on 2009-01-09
Running...

```
cat /proc/mdstat
```

gives...

```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md1 : active raid1 dm-3[0]
      234372160 blocks [2/1] [U_]
      
md0 : active raid1 dm-1[0]
      312568576 blocks [2/1] [U_]
      
unused devices: <none>
```

---

### Post by triciens on 2009-01-09
Running...

```
sudo mdadm --query --detail /dev/md* 
```...gives the following results:

```
/dev/md0:
        Version : 00.90
  Creation Time : Thu Jan  8 18:39:44 2009
     Raid Level : raid1
     Array Size : 312568576 (298.09 GiB 320.07 GB)
  Used Dev Size : 312568576 (298.09 GiB 320.07 GB)
   Raid Devices : 2
  Total Devices : 1
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Fri Jan  9 17:50:58 2009
          State : clean, degraded
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

           UUID : 3387504f:88751b78:2bcfa910:3ab89ab1
         Events : 0.1354

    Number   Major   Minor   RaidDevice State
       0     254        3        0      active sync   /dev/block/254:3
       1       0        0        1      removed
```

```
/dev/md1:
        Version : 00.90
  Creation Time : Thu Jan  8 18:40:21 2009
     Raid Level : raid1
     Array Size : 234372160 (223.51 GiB 240.00 GB)
  Used Dev Size : 234372160 (223.51 GiB 240.00 GB)
   Raid Devices : 2
  Total Devices : 1
Preferred Minor : 1
    Persistence : Superblock is persistent

    Update Time : Fri Jan  9 17:53:02 2009
          State : active, degraded
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

           UUID : 02f0c2a2:78c9c97e:eb13ab47:af3acd60
         Events : 0.881

    Number   Major   Minor   RaidDevice State
       0     254        0        0      active sync   /dev/block/254:0
       1       0        0        1      removed

```

```
mdadm: md device /dev/md2 does not appear to be active.

```

---

### Post by mitanc on 2009-04-25
Ever get a solution for this?

Seems to me as if the system is configured for software raid thru mdadm, but somehow "fakeraid" the intel controller one, is turning on and mucking things up.

I am having the same issue right now, trying to see if there's a solution.

Mitan

---

### Post by triciens on 2009-04-25
I didn't find a solution. This was in 8.10 - are you getting the same problem in 9.04?

---

### Post by mitanc on 2009-04-25
No I haven't... I think actually an older version of ubuntu (8.04) would work better.  I feel the bios turns off the fakeraid, but ubuntu when it loads is loading the drivers. 

What I did now was turn on my server's fakeraid implementation and will be reinstalling tomorrow. It will use dmraid instead of mdadm.

mitan

---

### Post by mitanc on 2009-04-26
Alright,

So I went to the office today to completely redo my server.  A little into, about a month back I purchased a new intel based server for my small business and decided to go the all linux route to act as a fileserver / PDC.  On the first go I used Ubuntu 8.10, while it is a newer version, I can't say it went well.  These were the problems with 8.10:

1.  The fakeraid actually is "supported" in 8.10, but in my case it doesn't work.  I tried implementing RAID-1 config in two ways.

---

### Post by mitanc on 2009-04-26
Alright,

So I went to the office today to completely redo my server.  A little into, about a month back I purchased a new intel based server for my small business and decided to go the all linux route to act as a fileserver / PDC.  On the first go I used Ubuntu 8.10, while it is a newer version, I can't say it went well.  These were the problems with 8.10:

1.  The fakeraid actually is "supported" in 8.10, but in my case it doesn't work.  I tried implementing RAID-1 config in two ways.
    a.  Disable the fakeraid in bios, and go the software based raid (mdadm).  The problem with this is, during install it allows me to configure the software raid and make md mount points, but after the installation and during boot the system gets confused and actually detects the fakeraid and uses software raid.  An example of the issue is that the mapper interface comes up and my partitions are named in dev as /dev/md-1.  It was pretty unstable and I had no idea how to fix it.  

2.  Knowing the above, I tried enabling the RAID in the fakeraid and initiated the array in the bios.  During the install, again, everything works fine.. but during the boot again some kind of issues come up and ubuntu won't boot.  I wish I had more time to document this and submit a bug report, but right now I need to get this system running.  

Anyways, today I backed everything up, and reinstalled ubuntu 8.04 and everything worked out very straight forward with regards to software raid.  Also, I reinstalled openldap and it went much smoother with the 8.04 using the various HOW TO's on the web.. so word of advice, server PDC.. use 8.04, makes life much easier.

Okay, I know a lot of the above doesn't make much sense, so if you need help with anything let me know and I will elaborate more.

Mitan

---

