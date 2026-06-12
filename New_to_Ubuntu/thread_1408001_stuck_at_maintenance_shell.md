---
title: "stuck at maintenance shell"
date: 2010-02-15
forum: New to Ubuntu
---

### Post by keevill on 2010-02-15
When I start Ubuntu 9.1 now I get the 'filesystem checks are in progress' dialogue - when it reaches 100% I get the following error.
Init mountall main process ..... Control-D will terminate etc....Give root password for maint etc....

If I go the Ctrl-D route, then it just goes thru the file check process again and I end up at the same place.
If I enter the root password for maintenance, I get the command line.
Where do I go from here ?
I prefer not to re-install unless absolutely necessary.

Thx,
-keevill

---

### Post by tom.swartz07 on 2010-02-15
> **keevill said:**
> When I start Ubuntu 9.1 now I get the 'filesystem checks are in progress' dialogue - when it reaches 100% I get the following error.
Init mountall main process ..... Control-D will terminate etc....Give root password for maint etc....

If I go the Ctrl-D route, then it just goes thru the file check process again and I end up at the same place.
If I enter the root password for maintenance, I get the command line.
Where do I go from here ?
I prefer not to re-install unless absolutely necessary.

Thx,
-keevill

Happened to me just earlier today. Fsck failed, so you need to manually run it


```
fdisk -l
```
will show you all of the partitions. 

for example: ```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x98000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3983    31993416   83  Linux
/dev/sda2            3984       38913   280575225    5  Extended
/dev/sda5           38428       38913     3903763+  82  Linux swap / Solaris
/dev/sda6            3985        7631    29294496   83  Linux
/dev/sda7            7632       31568   192273921    7  HPFS/NTFS
/dev/sda8           31569       32054     3903763+  83  Linux
/dev/sda9           32055       38427    51191091   83  Linux

```


You need to run the command 
```
fsck /dev/sdXX
``` where XX stands for what you have listed. XX in the example would be a1, a2, a3, etc

essentially, you need to run 
```
fsck /dev/sda1
fsck /dev/sda2
.......
```

until you find the culprit. It will show you the errors, and ask to fix them, Just hit enter and it will fix everything.


after you ran through all of your partitions (the test wont run on some partitions- thats okay), just type 
```
reboot
```

and youre all set!

---

### Post by keevill on 2010-02-15
> **tom.swartz07 said:**
> Happened to me just earlier today. Fsck failed, so you need to manually run it


```
fdisk -l
```
will show you all of the partitions. 

for example: ```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x98000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3983    31993416   83  Linux
/dev/sda2            3984       38913   280575225    5  Extended
/dev/sda5           38428       38913     3903763+  82  Linux swap / Solaris
/dev/sda6            3985        7631    29294496   83  Linux
/dev/sda7            7632       31568   192273921    7  HPFS/NTFS
/dev/sda8           31569       32054     3903763+  83  Linux
/dev/sda9           32055       38427    51191091   83  Linux

```


You need to run the command 
```
fsck /dev/sdXX
``` where XX stands for what you have listed. XX in the example would be a1, a2, a3, etc

essentially, you need to run 
```
fsck /dev/sda1
fsck /dev/sda2
.......
```

until you find the culprit. It will show you the errors, and ask to fix them, Just hit enter and it will fix everything.


after you ran through all of your partitions (the test wont run on some partitions- thats okay), just type 
```
reboot
```

and youre all set!

You are a star !!!
Just as it says on the tin !!!
-keevill-

---

### Post by tom.swartz07 on 2010-02-15
> **keevill said:**
> You are a star !!!
Just as it says on the tin !!!
-keevill-

AWESOMEEE!!!!
:KS:KS:KS:KS:KS:KS:KS

Im pumped you got it to work!
Kindly mark the thread as [solved] just in case others have the same problem!

Have a rocking awesome day!

---

### Post by blinovitch on 2010-03-01
> **tom.swartz07 said:**
> after you ran through all of your partitions (the test wont run on some partitions- thats okay), just type 
```
reboot
```and youre all set!
I just wanted to throw in and say thanks as well. This got my laptop back up and running.

---

### Post by Mike Yancey on 2010-03-08
> **blinovitch said:**
> I just wanted to throw in and say thanks as well. This got my laptop back up and running.

Ditto here - I was just cleaning up an old laptop (a throwout from work).
Ubuntu 9.10 installed fine; updated fine. But somehow got this same problem.
File system wouldn't mount.

FSCK corrected one of the partitions that had somehow gotten marked with a date in the future (i.e. the system clock had gotten reset during a particular time).

Thank you VERY much.
Now I know what FSCK is for. I'm becoming more and more proficient at Linux (command line).

Mike Y
Dallas, Texas

---

