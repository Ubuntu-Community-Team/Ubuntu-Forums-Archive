---
title: "problems creating separate partition for /home"
date: 2009-03-04
forum: New to Ubuntu
---

### Post by capnthommo on 2009-03-04
hi everybody.
i finally screwed up courage to make a separate partition for my /home directory.
i have put in the live disk, rebooted, selected to boot using cd/dvd and taken the boot from first disk option (no try ubuntu without installing option apparently) and logged on to the desktop.  i have opened gparted, selected 'swap-off' on the swap partition and then selected the partition to resize  (i only have one partition).  all fine so far - but when i rt click and attempt to unmount my one partition i am told:
```
could not unmount /dev/sda1  the partition could not be unmounted from the following mountpoints  /  most likely other partitions are also mounted on these montpoints. you are advised to unmount them manually. 
```
(sorry about inappropriate code brackets but should i use quote brackets instead? never certain!)
anyway,  i only have the /dev.sda1 partition except for the linux swap.  oh, and the /dev/sdb1 which is where my USB external HDD mounts (currently unmounted and not connected)
could this mounted partition the error refers to be the CD/DVD drive maybe?
i installed with a whole disk option and have all 160Gb under /dev/sda1

so can anybody help here at all?
using 8.10 64bit
cheers
nigel

---

### Post by taurus on 2009-03-04
Can you post the outputs of these commands from a terminal?

```
sudo fdisk -l
df -h
free -m
```

---

### Post by kanikilu on 2009-03-04
If you used the "boot from first disk" option from the CD, that's going to boot up your currently installed OS. You can't resize mounted/in-use partitions, so I believe the correct way to do this would be to boot into the Live CD, choose the "try before installing" option, and then run GParted from there.

I'll see if I can dig up a step-by-step howto...

// Edit - Here ya go: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

// Edit 2 - Just read that you said there is apparently no "try before installing" option on your CD. Not really sure why that would be, but you can always just download the GParted live CD or USB image: [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by jellybaby on 2009-03-04
Hi!

here is a [link to create a gparted LiveCD]("http://gparted.sourceforge.net/livecd.php"). You just boot your PC with this and can access all partitions. This way, you can resize your "/" partition (if you boot into Ubuntu your "/" partitiion is active and cannot be changed).
Guides for creating home partitions:
[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/]("http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/");
[http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html]("http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html").

Hope this helps.
Regards

---

### Post by capnthommo on 2009-03-04
hi folks, can i deal with these one at a time? or i am going to get in a mess.  so taurus, i will be back in a couple of minutes with the results of the code.
thanks kanikilu.  that is the how to i am using.  i am certain i am using my live disk, i shall just check that to be certain, but i am almost sure that's what i am using.  it has the usual options but just doesn't have the 'try before you buy' option - so ??.
anyway, taurus
```


nigel@ubuntunigellaptop:~$ sudo fdisk -l
[sudo] password for nigel: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x939aab47

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18755   150649506   83  Linux
/dev/sda2           18756       19457     5638815    5  Extended
/dev/sda5           18756       19457     5638783+  82  Linux swap / Solaris

nigel@ubuntunigellaptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             142G  7.7G  127G   6% /
tmpfs                 941M     0  941M   0% /lib/init/rw
varrun                941M  308K  941M   1% /var/run
varlock               941M     0  941M   0% /var/lock
udev                  941M  2.8M  938M   1% /dev
tmpfs                 941M   12K  941M   1% /dev/shm
lrm                   941M  2.4M  939M   1% /lib/modules/2.6.27-13-generic/volatile
/dev/scd0             698M  698M     0 100% /media/cdrom0

nigel@ubuntunigellaptop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1881        899        981          0         25        403
-/+ buffers/cache:        470       1410
Swap:          470          0        470
nigel@ubuntunigellaptop:~$ 

```

could the /dev/scd0 that is the cd have anything to do with it?
and thanks for the mind blastingly rapid responses - excellent as usual
nigel

---

### Post by theozzlives on 2009-03-04
If you boot the Live CD the first option is "Try Ubuntu without making any changes to your Hard Disk", Choose that one... you don't have to turn the swap off. Just resize sda1 and make a new partition. your "/" only needs to be 10 or 20 GB (depending on how big your HD is, but you can't get that small cause your home is  there).

---

### Post by taurus on 2009-03-04
Looks like you used the LiveCD to boot Ubuntu from your harddrive.  Therefore, you cannot resize a partition while you are using it.  Try booting from the CD as in live session.

Otherwise, use GParted LiveCD as others have suggested.

---

### Post by kanikilu on 2009-03-04
> **capnthommo said:**
> it has the usual options but just doesn't have the 'try before you buy' option - so ??. If that's the case, don't worry about it too much, just grab the GParted live CD and you can still follow the how-to posted earlier.

---

### Post by Dougie187 on 2009-03-04
I agree with the two unanswered posts. I think you need to burn a new live cd. You probably burned a copy of the alternative cd instead of the live cd. You can either go burn a copy of the live cd version of ubuntu or burn a copy of gparted as there are instructions to do so. Then you will have the "Try without installing" option, and can then use gparted.

---

### Post by capnthommo on 2009-03-04
hi evryone - thanks to all of you. it never fails to knock me out, the degree of support on this forum.  
anyway, i think i might just have to burn a new live cd, looks like i have either lost the real live cd or it is malfumctioning in some way.
thanks again for the help - i shall come back if i have any more problems.  for now i think i will call it solved
cheers again
nigel

---

