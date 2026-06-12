---
title: "Can't boot ubuntu, stuck with blank screen"
date: 2011-05-17
forum: New to Ubuntu
---

### Post by wjkraymond on 2011-05-17
Hi,

I've been using ubuntu and windows7 fine till recently. 

Yesterday i post a question in this forum and got an answer within a day. (thanks everyone for helping me)
[http://ubuntuforums.org/showthread.php?p=10822495#post10822495](http://ubuntuforums.org/showthread.php?p=10822495#post10822495)
Its about wanting a trash folder in my other partitions.

after i tried out the solution, my problem is solved. my deleted files were able to sent to trash instead of instantly deleted permanently.

I was so happy, i even implemented solution it on my 2nd pc, which is a netbook.

Before i shut down my laptop yesterday, it kindda hang.
usually it shuts down in around 5 seconds, but yesterday it  hang and a bunch of geeky text appears.
i did not understand them and waiting for it to shutdown. but it remains the same after 5 minutes. so i force shutdown it by pressing the power button for 5 seconds.

I was using window7 this morning on my laptop and everything was fine.
Then i wanted to use ubuntu. I select it in the grub menu, but the ubuntu doesn load.

I was just left with a blank screen after choosing it at the boot menu.
I had no choice but to force shut down it (press and hold power button), and try again.
But the problem persist.

So i use a live USB which contains ubuntu and boot from it.

Here is a screen shot of gpart

[IMG]http://i.imgur.com/itiSp.png[/IMG]

I am able to mount my other drives, but when i want to mount the partition that has ubuntu, this error message appears.

"Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sda5,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so"

When i open a terminal, and type a command to list all disk, this is what i get:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x2589b089

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13        8950    71780352    7  HPFS/NTFS
/dev/sda3            8950       35441   212789248    7  HPFS/NTFS
/dev/sda4           35441       38914    27896833    5  Extended
[COLOR=Red]Partition 4 does not start on physical sector boundary.[/COLOR]
/dev/sda5           35441       38663    25883648   83  Linux
/dev/sda6           38663       38914     2012160   82  Linux swap / Solaris

Disk /dev/sdb: 1048 MB, 1048313856 bytes
33 heads, 61 sectors/track, 1017 cylinders
Units = cylinders of 2013 * 512 = 1030656 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d8c95

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1017     1023580    c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$ 




```

I have no idea why my ubuntu partition just fail to mount. I cant boot into my ubuntu.
I'm not sure whether its because i tried to make a trash folder for my other partition.
but my netbook which i've tried the same method, did not have any problems at all.
(not sure this is related or not, but i just want to give as much info as i can)


I really spend alot of effort to customized it. I really dun feel like reinstalling my ubuntu again.
Please help me, is there anyway i can use my ubuntu again?

---

### Post by Hedgehog1 on 2011-05-17
wjkraymond,

The warning message: 

[COLOR="Red"]Partition 4 does not start on physical sector boundary.[/COLOR]

Is nothing to be concerned about.  It is also not the cause of your current pain.

Please use gparted from your LiveCD/LiveUSB, right click on the partition that will not mount and select the 'check' option.  

[IMG]http://img810.imageshack.us/img810/3612/chrckparion01.png[/IMG]

This option really means 'check and repair':

[IMG]http://img818.imageshack.us/img818/4900/chrckparion02.png[/IMG]

Then press the 'check mark' button on the gparted mens bar to run the 'check and repair'

If it yields any 'unrepairable' messages, please post these.  If it fixes your partition and you can boot into Ubuntu again, then please mark this thread 'solved'. :D

***The Hedge***

:KS

---

### Post by wjkraymond on 2011-05-17
Dear Hedgehog1

Thank you so so so much for your help.

Your advice worked!

I was so depressed that my ubuntu is lost, 
but now it is back and fully functioning again.

I cant thank you enough.

May you be well and happy always.

---

### Post by Hedgehog1 on 2011-05-17
Glad I was able to help - and thanks for marking the thread solved, too!

***The Hedge***

:KS

---

### Post by wjkraymond on 2011-05-18
Hi Hedgehot1,

i was wondering what could've cause this issue.

i usually have the habit of shutting the computer down when there are applications running.

example, chromium is on, some file browser on.
then i press power button and select shut down.

i assume the system will close all open programs and proceed to shutdown, just like windows. is this not encouraged in linux?

could this be the root cause of my partition suddenly become unaccessible?

---

### Post by Hedgehog1 on 2011-05-18
> **wjkraymond said:**
> Hi Hedgehot1,

i was wondering what could've cause this issue.

i usually have the habit of shutting the computer down when there are applications running.

example, chromium is on, some file browser on.
then i press power button and select shut down.

i assume the system will close all open programs and proceed to shutdown, just like windows. is this not encouraged in linux?

could this be the root cause of my partition suddenly become unaccessible?

If you are using the 'power' menu and selecting shut down, you are doing things the correct way. So I don't think that is the cause.

Something was running that was mid-write that did not get the 'system going down' message that one time, and left things damaged on the drive.

You could go nuts trying to figure it out, or not worry too much and only take more time with it if it starts happening often.

At least you know the trick to fixing it now!

***The Hedge***

:KS

---

