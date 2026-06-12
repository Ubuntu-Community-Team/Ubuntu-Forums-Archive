---
title: "Is my swap working?"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by Corey4666 on 2009-01-19
I have a swap setup but I don't think its working... on suspicion. How do I test if my swap is working? I didn't see anything about it in my system monitor.

---

### Post by logos34 on 2009-01-19
cat /proc/swaps

---

### Post by taurus on 2009-01-19
Or 

Applications -> Accessories -> Terminal
```
free -m
```

---

### Post by Damage. on 2009-01-19
system monitor should show it under resources

---

### Post by DariusS on 2009-01-19
What if system monitor doesn't show your swap being used at all? ever?

---

### Post by ChildOfMana on 2009-01-19
It may be that you're not using swap at all because you don't need to.

How much RAM do you have installed in your rig?

I have 2Gb installed and I don't remember ever seeing my swap usage go above 0%.

At the end of the day the fact that your computer is still running correctly (I'm assuming anyway, seen as you haven't said otherwise) means that there is likely nothing to worry about.

---

### Post by DariusS on 2009-01-19
that's prolly it, which I had suspected. I have 3gb on my laptop and never really do anything memory-intense.

---

### Post by Corey4666 on 2009-01-19
Yeah my swap is working.... It was using a small amount when I was running world of warcraft and listening to music. I have 1 gig of ram shared.

---

### Post by ChildOfMana on 2009-01-19
DariusS: That's your answer then. With 3Gb of RAM installed and no memory-intensive programs running I'd be worried if you *were* using swap space.

Corey4666: That sounds pretty normal. With only 1Gb and a memory-intensive app like WoW running you're bound to use some swap. But even if you weren't using any swap and your system was still stable and acting correctly then again; nothing to worry about. :)

---

### Post by DariusS on 2009-01-19
Ok, so this is most likely a noob question (and I've been using linux for a number of years now...still learning) but is swap used kind of like virtual memory? is that it's purpose? this is what I've always surmised, but never actually got around to investigating.

---

### Post by ChildOfMana on 2009-01-19
Yeah, basically. It works on the same principle (but in a slightly different way) to the Windows paging file (virtual memory).

---

### Post by laurielegit on 2009-01-19
> **DariusS said:**
> Ok, so this is most likely a noob question (and I've been using linux for a number of years now...still learning) but is swap used kind of like virtual memory? is that it's purpose? this is what I've always surmised, but never actually got around to investigating.

Yes it is. My system dosn't recognise that it has a swap partition. Can someone explain this:

```
laurie@Edgar:~$ cat /proc/swaps
Filename				Type		Size	Used	Priority
laurie@Edgar:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2000       1391        609          0        146        477
-/+ buffers/cache:        767       1233
Swap:            0          0          0
laurie@Edgar:~$ 
```

Thanks,

Laurie

EDIT: And I do have a swap partition: see my fdisk:

```
laurie@Edgar:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x05740573

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1           38404       38913     4096575   82  Linux swap / Solaris
/dev/sda2   *         487         498       96390   83  Linux
/dev/sda3             499        6577    48829567+  83  Linux
/dev/sda4            6578       18735    97659135   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x10f453aa

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30214   242693923+   b  W95 FAT32
/dev/sdb2           30215       30401     1502077+   5  Extended

```

---

### Post by ChildOfMana on 2009-01-19
can you post the output of:

```
sudo fdisk -l
```

NOTE: that's a lower case L, not a 1

---

### Post by laurielegit on 2009-01-19
> **ChildOfMana said:**
> can you post the output of:

```
sudo fdisk -l
```

Just did :P (sorry for not including it first time)

---

### Post by ChildOfMana on 2009-01-19
Ah well, problem solved! :)

EDIT: Just realised I read you original post wrong. Sorry. Not sure why you're not getting an output from cat /proc/swaps.

Bump?

---

### Post by b0b138 on 2009-01-19
You have it partitioned, but its not being recognized.

---

### Post by laurielegit on 2009-01-19
> **b0b138 said:**
> You have it partitioned, but its not being recognized.

Yes, that seems to be the problem. My conky states that I have "No swap%" free :P.

---

### Post by mcduck on 2009-01-19
Ok, the swap partition is not recognized, but at least there is one. Now we'll just need to get  Ubuntu to use it.

I bet the problem is with your fstab, most likely with the UUIDss for your partitions. Simply because that has been the reason every single time I've seen somebody with swap that doesn't work..

Could you post here your /etc/fstab file, and output of "blkid" command? (The command lists UUIDs for all your partitions).

(what you'll have to do is to compare UUIDs reported by "blkid" with the ones in /etc/fstab, and if there's any differences then edit the fstab to use correct UUIDs. After that you can reboot the machine and test if the swap is recognized. If not, run "sudo mkswap /dev/sda1" and "sudo swapon -a" and now the swap should be recognized. But before you do any of that please post the information I asked for so we can confirm that this really is what you need to do.)

---

### Post by jerome1232 on 2009-01-19
---edit--- mcduck beat me to it

What does your fstab look like? Might as well post your uuid's.
```
cat /etc/fstab
sudo blkid
```

---

### Post by b0b138 on 2009-01-19
and the output of ```
cat /etc/initramfs-tools/conf.d/resume
```

---

### Post by laurielegit on 2009-01-19
Here you are.

```
laurie@Edgar:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=cf299d0d-a69e-4c9e-bb8d-c78a599fea7d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=a14a7e40-88ae-4900-89bc-c0ba02294d65 /boot           ext2    relatime        0       2
# /dev/sda4
UUID=6d1acef4-52da-4110-ac73-5cf8b0f4d482 /home           ext3    relatime        0       2
# /dev/sda1
UUID=f900d341-207f-447d-b204-72d9ad6e24da none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
laurie@Edgar:~$ sudo blkid
[sudo] password for laurie: 
/dev/sda1: TYPE="swap" UUID="3bb75e9b-88b3-410c-814e-966df0cd137f" 
/dev/sda2: UUID="a14a7e40-88ae-4900-89bc-c0ba02294d65" TYPE="ext2" 
/dev/sda3: UUID="cf299d0d-a69e-4c9e-bb8d-c78a599fea7d" TYPE="ext3" 
/dev/sda4: UUID="6d1acef4-52da-4110-ac73-5cf8b0f4d482" TYPE="ext3" SEC_TYPE="ext2" 
/dev/sdb1: UUID="48B5-36E4" TYPE="vfat" 
/dev/sdc1: UUID="48B5-36E4" TYPE="vfat" 
laurie@Edgar:~$ cat /etc/initramfs-tools/conf.d/resume
RESUME=UUID=f900d341-207f-447d-b204-72d9ad6e24da
laurie@Edgar:~$ 
```


Hope that helps,

Laurie

---

### Post by b0b138 on 2009-01-19
yup, according to blkid, you swap uuid is 3bb75e9b-88b3-410c-814e-966df0cd137f. But both fstab and the other one show f900yadayadayada. So gksudo gedit /etc/fstab and edit that one. Then edit the other one. After you edit the /etc/init....blahblah one run ```
sudo update-initramfs -u
```    then reboot

---

### Post by jerome1232 on 2009-01-19
```

# /dev/sda1
UUID=f900d341-207f-447d-b204-72d9ad6e24da none            swap    sw              0       0
 
/dev/sda1: TYPE="swap" UUID="3bb75e9b-88b3-410c-814e-966df0cd137f" 


```

You need to make those uuid's match, Change the one in fstab to match the output from blkid.

---

### Post by mcduck on 2009-01-19
Exactly as I thought it would be.. :D

Change this line in your fstab:
```
UUID=f900d341-207f-447d-b204-72d9ad6e24da none            swap    sw              0       0
```
to this:
```
UUID=3bb75e9b-88b3-410c-814e-966df0cd137f none            swap    sw              0       0
```

then run these commands:
```
sudo mkswap /dev/sda1
sudo swapon -a
```
..and finally run "free -m" again to check if the swap is now working.

---

### Post by b0b138 on 2009-01-19
So jerome or mcduck, do either of you know why this happens?

---

### Post by laurielegit on 2009-01-19
> **mcduck said:**
> Exactly as I thought it would be.. :D

Change this line in your fstab:
```
UUID=f900d341-207f-447d-b204-72d9ad6e24da none            swap    sw              0       0
```
to this:
```
UUID=3bb75e9b-88b3-410c-814e-966df0cd137f none            swap    sw              0       0
```

then run these commands:
```
sudo mkswap /dev/sda1
sudo swapon -a
```
..and finally run "free -m" again to check if the swap is now working.

This seems to have worked. Running it though, I can't see if it is ever going to use the swap. I think I'll log into another user, and see how much that drives up the ram usage, and maybe it'll use the swap. I can but hope.

Thanks so much,

Laurie

---

### Post by mister_pink on 2009-01-19
UUID will change if you've messed with your partions at all since you installed ubuntu. Shouldn't otherwise.

---

### Post by mcduck on 2009-01-19
> **b0b138 said:**
> So jerome or mcduck, do either of you know why this happens?

Not without knowing what has been done with that computer.. ;)

Any editing of partitions will change the UUID of that partition, which would be the most common reason for fstab having wrong UUID. So if you mess with your partitions, remember to check the correct UUID's and edit the fstab afterwards.

Of course if the partitions have not been edited, I have absolutely no idea why the UUID in fstab would be wrong.. :D

---

### Post by mcduck on 2009-01-19
> **laurielegit said:**
> This seems to have worked. Running it though, I can't see if it is ever going to use the swap. I think I'll log into another user, and see how much that drives up the ram usage, and maybe it'll use the swap. I can but hope.

Thanks so much,

Laurie

Great that you got it sorted out. And don't worry if the swap isn't actually used. That's just a sign that you have enough RAM in your machine. At least the swap is now there if you'll ever need it. ;)

Most likely if you leave the machine running for long enough time it will use couple of megabytes worth of swap.

---

### Post by laurielegit on 2009-01-20
After having swap running, I restarted my machine. When I look at it now I have no swap. I have cheaked that my fstab, and it is correct. I cannot seem to make the computer recognise the partition as swap with these commands:

```
sudo mkswap /dev/sda1
sudo swapon -a
```

but that returns this:

```
laurie@Edgar:~$ sudo swapon -a
swapon: cannot stat /dev/disk/by-uuid/3bb75e9b-88b3-410c-814e-966df0cd137f: No such file or directory
laurie@Edgar:~$ sudo mkswap /dev/sda1
Setting up swapspace version 1, size = 4096568 KiB
no label, UUID=c705e371-1e18-47bc-aec4-d59345d9cb65
laurie@Edgar:~$ sudo swapon -a
swapon: cannot stat /dev/disk/by-uuid/3bb75e9b-88b3-410c-814e-966df0cd137f: No such file or directory
laurie@Edgar:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2000        931       1068          0         77        290
-/+ buffers/cache:        563       1436
Swap:            0          0          0
laurie@Edgar:~$ 
```

I can however turn on swap through gparted.

Thanks,

Laurie

---

### Post by mcduck on 2009-01-20
> **laurielegit said:**
> After having swap running, I restarted my machine. When I look at it now I have no swap. I have cheaked that my fstab, and it is correct. I cannot seem to make the computer recognise the partition as swap with these commands:

```
sudo mkswap /dev/sda1
sudo swapon -a
```

but that returns this:

```
laurie@Edgar:~$ sudo swapon -a
swapon: cannot stat /dev/disk/by-uuid/3bb75e9b-88b3-410c-814e-966df0cd137f: No such file or directory
laurie@Edgar:~$ sudo mkswap /dev/sda1
Setting up swapspace version 1, size = 4096568 KiB
no label, UUID=c705e371-1e18-47bc-aec4-d59345d9cb65
laurie@Edgar:~$ sudo swapon -a
swapon: cannot stat /dev/disk/by-uuid/3bb75e9b-88b3-410c-814e-966df0cd137f: No such file or directory
laurie@Edgar:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2000        931       1068          0         77        290
-/+ buffers/cache:        563       1436
Swap:            0          0          0
laurie@Edgar:~$ 
```

I can however turn on swap through gparted.

Thanks,

Laurie
That's strange, the error is telling you that the UUID is wrong..

Check it again with blkid, fix fstab, and reboot. (no mkswap this time). And don't touch that partition with gparted..

---

### Post by jerome1232 on 2009-01-20
I believe anytime you do 'mkswap' the uuid will change, since that's essentially "formating" the partition for swap space.

---

### Post by mcduck on 2009-01-20
> **jerome1232 said:**
> I believe anytime you do 'mkswap' the uuid will change, since that's essentially "formating" the partition for swap space.

If that's true, "swapon -a" shouldn't have worked, as it checks the available swap partitions from fstab...

But it's true that mkswap shouldn't be necessary at this point as the partition is already a swap partition.

---

### Post by mister_pink on 2009-01-20
If you don't swap disks around ever you can use "/dev/sda1" instead of the UUID in the fstab instead. I tend to find this a little less hassle.

---

### Post by mcduck on 2009-01-20
> **mister_pink said:**
> If you don't swap disks around ever you can use "/dev/sda1" instead of the UUID in the fstab instead. I tend to find this a little less hassle.

Some motherboards detect disk on different order on every boot, or depending if you have removable drives plugged in or not. So this solution might or might not work correctly..

---

### Post by jerome1232 on 2009-01-20
> **mcduck said:**
> If that's true, "swapon -a" shouldn't have worked, as it checks the available swap partitions from fstab...

But it's true that mkswap shouldn't be necessary at this point as the partition is already a swap partition.

If you read his output "swapon -a" didn't work due to a uuid mismatch.

---

### Post by mcduck on 2009-01-20
> **jerome1232 said:**
> If you read his output "swapon -a" didn't work due to a uuid mismatch.
..but it worked *yesterday*, right *after* first changing fstab and then running mkswap. ;)

[http://ubuntuforums.org/showpost.php?p=6581066&postcount=26]("http://ubuntuforums.org/showpost.php?p=6581066&postcount=26")

edit: of course this can be explained if running mkswap stores information about that available swap location temporarily in some place other than  fstab (/proc/swaps?) which would allow swapon -a" to work even if the UUID was changed by mkswap, until the machine is rebooted..

edit2: I just tested this, indeed it seems that mkswap changes UUID of that partition, and then stores information about available sap temporarily somewhere. In that case all instructions given in this thread will work fine, just don't use the mkswap part.

---

### Post by RyanVanDiemen on 2009-01-20
Well, can somebody explain me advantages why fstab differentiate between partitions by its UUID and not device location ( /dev/sdaN...) ? Because I remember I had very similar problem some time ago and it took me a while before I solved it (didn`t have internet connection at the time; no forums ;-) ). I just don`t see any advantage, but there must be some...

---

### Post by azz2811 on 2009-01-20
i have 1 gb of ram and my swap never goes above 0% does that mean that i can delete my swap??

---

### Post by mcduck on 2009-01-20
> **RyanVanDiemen said:**
> Well, can somebody explain me advantages why fstab differentiate between partitions by its UUID and not device location ( /dev/sdaN...) ? Because I remember I had very similar problem some time ago and it took me a while before I solved it (didn`t have internet connection at the time; no forums ;-) ). I just don`t see any advantage, but there must be some...

Because the device names (/dev/sdaN) can change in some cases. If you change the disks to different cables, have removable drives plugged in while booting etc. Also some motherboards have a bad habit of detecting disk in different order on every boot causing them to have different device name every time.

For example my old desktop machine detected it's disks randomly, the drive that was /dev/sda became /dev/sdb on next boot. Bit of a nasty situation if you have to rely on device names to mount your partitions.. ;)

Using UUIDs also makes it possible to define options for removable disks in fstab. Of course you can get the same benefits by labeling all your partitions and using label instead of UUID or device name in fstab.

---

### Post by RyanVanDiemen on 2009-01-20
Thanks mcduck, I thought this might be the case. But anyway, UUIDs should be at leas a bit shorter...but that`s not something linux can solve...

---

### Post by mcduck on 2009-01-20
> **RyanVanDiemen said:**
> Thanks mcduck, I thought this might be the case. But anyway, UUIDs should be at leas a bit shorter...but that`s not something linux can solve...

Then you can just use labels instead, you can make them as short as you wish..

For Ext2/Ext3 partitions set the label with "sudo e2label /dev/sdXX *name*"
For swap, sudo mkswap -L *name* /dev/sdXX"

..and the  in fstab use "LABEL=*name*" instead of "UUID=*xxx*" or device name.

Of course you'll need to set the labels by hand, using automatically generated random labels would be pretty much the same as using UUIDs. But this gives you more meaningful names for your disks while still having the same benefits you get by using UUID.

---

### Post by RyanVanDiemen on 2009-01-20
> **mcduck said:**
> this gives you more meaningful names for your disks while still having the same benefits you get by using UUID.

Will these labels be recognized by other distros? If not, it will keep the same disadvantage you have by using UUIDs: linux will not recognize and mount the partition if you format it in another distro...

---

### Post by laurielegit on 2009-01-20
I did what you said, and just before restarting, my computer was recognising swap. After restarting however, it is not recognising swap. What has happened now? and how can I make it recognise swap every time.

Thanks,

Laurie

---

### Post by mcduck on 2009-01-20
> **RyanVanDiemen said:**
> Will these labels be recognized by other distros? If not, it will keep the same disadvantage you have by using UUIDs: linux will not recognize and mount the partition if you format it in another distro...
Of course they are. So are UUIDs and everything else. I have no idea why you believe Linux wouldn't detect drives formatted in another distro.

Automounting is a completely different thing, there's no way you could store information where and how to mount the partition in the partition itself, as it's not possible to know the setup of every possible computer you might plug the drive into. Determining how to mount drives is up to the OS/distro that is currently running.

Just like in Windows you can't tell that your hard drive should be called "F:", move it to another computer and expect it to be called "F:". It's assigned letter depends on how many drives are on *that* computer and in which cable you plugged the drive in.

Anyway, Labels are detected by most operating systems, and most Linux distributions use them when automounting drives. For example I have a removable hard disk, labeled as "Deimos". When plugged in, most Linux distros will automount it into /media/Deimos, my Mac automounts it into /Volumes/Deimos and Windows gives it next available drive letter (while displaying "Deimos" next to the letter).

Both UUID and label are stored in the partition itself, what the OS does with that information depends on the OS/distribution/current hardware setup.

edit: Actually UUID and labels are as close as you can get to a system where drives are always mounted with same names and in same places. It's just up to the OS to use this information. In a way UUID is just another, randomly generated label.

---

### Post by mcduck on 2009-01-20
> **laurielegit said:**
> I did what you said, and just before restarting, my computer was recognising swap. After restarting however, it is not recognising swap. What has happened now? and how can I make it recognise swap every time.

Thanks,

Laurie
1. run "blkid"
2. edit /etc/fstab to use UUIDs you got in the first step
3. reboot and check if swap works.

---

### Post by egalvan on 2009-01-20
> **mcduck said:**
> Then you can just use labels instead, you can make them as short as you wish..

For Ext2/Ext3 partitions set the label with "sudo e2label /dev/sdXX *name*"
For swap, sudo mkswap -L *name* /dev/sdXX"

..and the  in fstab use "LABEL=*name*" instead of "UUID=*xxx*" or device name.



Are these commands safe to use on partitions with data?
A few months ago I used gparted to apply a LABEL, and it erased the data on that partition.
It was a fresh install, so nothing lost, but now I have too much time invested to experiment on this install.

Second question about this:


blkid shows:

LABEL="swap" 
LABEL="gx280-xp"


so does one use 

LABEL="swap"
LABEL="gx280-xp" 

or

LABEL=swap
LABEL=gx280-xp

in the fstab file?

Thank you

ErnestG

---

### Post by mcduck on 2009-01-20
> **egalvan said:**
> Are these commands safe to use on partitions with data?
A few months ago I used gparted to apply a LABEL, and it erased the data on that partition.
It was a fresh install, so nothing lost, but now I have too much time invested to experiment on this install.

Second question about this:


blkid shows:

LABEL="swap" 
LABEL="gx280-xp"


so does one use 

LABEL="swap"
LABEL="gx280-xp" 

or

LABEL=swap
LABEL=gx280-xp

in the fstab file?

Thank you

ErnestG

e2label is safe to use with partitions that contain data. It only changes the label, nothing else.

mkswap -L will format the partition as swap, you should only use it on swap partition (or partition that you want to turn into swap). Also notice that the partiton in question can't be in use when you run the command, so if it's your current swap you need to run "sudo swapoff -a" (or "sudo swapoff /dev/*sdXX*")to disable swap before you can set the label.

To use labels in fstab don't put quote marks around the label:
```
LABEL=gx280-xp
```

---

### Post by egalvan on 2009-01-20
> **ChildOfMana said:**
> 

EDIT: Just realised I read you original post wrong. Sorry. Not sure why you're not getting an output from cat /proc/swaps.

Bump?

Well, under 8.04.1, I just ran 

```
cat /proc/swaps
```

and got no output either.

Is this a problem?

---

### Post by egalvan on 2009-01-20
> **mcduck said:**
> e2label is safe to use with partitions that contain data. It only changes the label, nothing else.


To use labels in fstab don't put quote marks around the label:
```
LABEL=gx280-xp
```

Thanks for the info, I'm in the process of "up-grading" fstab to use LABEL.

And  the "Thanks" button is still missing, will it return sometime soon?
is there any more info on it's disappearance?

---

### Post by laurielegit on 2009-01-20
I'm very sorry, but at this point I have had enough. I seem to be constantly changing my uuid, and not getting anywhere. I can live without swap, so I think I will until I have enough time to get this working. Thank you for all your help.

Laurie

---

### Post by mcduck on 2009-01-20
It will probably return together with the "mark thread solved"-feature as long as forum admins solve all the problems they are currently having with the forum database.

Well, at least working forum without those features is a lot better than just getting a database error instead of Ubuntuforums.. :D

---

### Post by mcduck on 2009-01-20
> **laurielegit said:**
> I'm very sorry, but at this point I have had enough. I seem to be constantly changing my uuid, and not getting anywhere. I can live without swap, so I think I will until I have enough time to get this working. Thank you for all your help.

Laurie

Are you running just the commands I gave you in my last post (so no "mkswap", no "swapon" and no touching the partition with gparted)?

In that case your computer must be run over by poltergeist. :)

---

### Post by egalvan on 2009-01-20
> **mcduck said:**
> Then you can just use labels instead, you can make them as short as you wish..

Yep, human-readable stuff is so much more comfortable. :)

> you'll need to set the labels by hand, using automatically generated random labels would be pretty much the same as using UUIDs. But this gives you more meaningful names for your disks **while still having the same benefits you get by using UUID**.

Well, not **quite** the same benefits...

One theoretical benefit of UUID is that no two are ever the same,
so, theoretically, no two partitions will ever have the same identifier,
so, theoretically, there will never be a mix-up or collision.
(and yes, the math works out to this being a rock-solid theory.)

whereas something like DATA (like we humans are fond of using) will most likely be used more than once :)

---

### Post by Kevbert on 2009-01-20
Thanks McDuck for your replies.  Had a look at this thread and found I had the same problem and I now know why. Every time I install a new version of *buntu/Linux on my PC I use the same partition for swap. Each time I do this the UUID for it changes to a new value.  Is there any way of keeping the UUID number the same without having to add a separate swap partition for each install ?

---

### Post by mcduck on 2009-01-20
> **egalvan said:**
> Yep, human-readable stuff is so much more comfortable. :)



Well, not **quite** the same benefits...

One theoretical benefit of UUID is that no two are ever the same,
so, theoretically, no two partitions will ever have the same identifier,
so, theoretically, there will never be a mix-up or collision.
(and yes, the math works out to this being a rock-solid theory.)

whereas something like DATA (like we humans are fond of using) will most likely be used more than once :)

Good point. :)

Of course I'm absolutely sure there's somebody stupid enough to set his UUIDs by hand to something like "1234 4567", just like it's possible to find cheap network cards with MAC set to zeroes.. :D

---

### Post by mcduck on 2009-01-20
> **Kevbert said:**
> Thanks McDuck for your replies.  Had a look at this thread and found I had the same problem and I now know why. Every time I install a new version of *buntu/Linux on my PC I use the same partition for swap. Each time I do this the UUID for it changes to a new value.  Is there any way of keeping the UUID number the same without having to add a separate swap partition for each install ?

I suppose Ubuntu's installer formats the swap partition automatically.. If it's possible to not define swap partition during install you could do that, and then add the swap to fstab by hand after the install. (I've never had a reason to try that so I don't know if the installer allows you to continue without defining a swap partition)

---

### Post by egalvan on 2009-01-20
> **mcduck said:**
> Good point. :)

Of course I'm absolutely sure **there's somebody stupid enough** to set his UUIDs by hand to something like "1234 4567", just like it's possible to find cheap network cards with MAC set to zeroes.. :D

:lolflag::lolflag::lolflag:

---

### Post by boof1988 on 2009-01-20
> **mcduck said:**
> I suppose Ubuntu's installer formats the swap partition automatically.. If it's possible to not define swap partition during install you could do that, and then add the swap to fstab by hand after the install. (I've never had a reason to try that so I don't know if the installer allows you to continue without defining a swap partition)

In the installer I have used the "Do not use this partition" option instead of "swap" in instances like you mentioned.  IIRC the swap partitions that are going to be formatted/used are Type: "swap" and the ones that are not going to be formatted/used are Type: "linux-swap".

Hope I haven't muddied up the water... ;)

---

### Post by egalvan on 2009-01-20
> **boof1988 said:**
> In the installer I have used the "Do not use this partition" option instead of "swap" in instances like you mentioned.  IIRC the swap partitions that are going to be formatted/used are Type: "swap" and the ones that are not going to be formatted/used are Type: "linux-swap".

Hope I haven't muddied up the water... ;)

From what I remember about the installer, there should be an option to format the partition.

I haven't used the installer partitioner since last May. 
I use PartedMagic to "pre-define" the partitions on machines I install Linux on.

 The latest version of PartedMagic just got "microsoft-ugly", but the partition editor seems to be one or two steps ahead of Ubuntu, thus more options. Definitely a "no format" option.

("microsoft-ugly" such as using "start" button to "stop", and too much eye-candy. Totally personal opinion, I'm sure many folks were dying to see a MS-dekstop clone of this...how sad)

---

### Post by RyanVanDiemen on 2009-01-20
> **mcduck said:**
> I have no idea why you believe Linux wouldn't detect drives formatted in another distro.

What I meant is that if you have a partition in fstab identified by UUID and then let`s say you decide to install new distro in this partition, installer will format the partition and assign new UUID to it. Once you reboot to your original distro it will not mount the partition to the folder you have specified in fstab because UUID is changed. You need to update UUID in fstab as well. That`s my point of disadvantage using UUIDs in fstab. Haven`t tried labels as you recommended yet...
Of course it`s not a big deal to update fstab in this case but when I first encountered this couple of yrs ago, it took me a while before I realised where`s the problem...

---

### Post by mcduck on 2009-01-20
> **RyanVanDiemen said:**
> What I meant is that if you have a partition in fstab identified by UUID and then let`s say you decide to install new distro in this partition, installer will format the partition and assign new UUID to it. Once you reboot to your original distro it will not mount the partition to the folder you have specified in fstab because UUID is changed. You need to update UUID in fstab as well. That`s my point of disadvantage using UUIDs in fstab. Haven`t tried labels as you recommended yet...
Of course it`s not a big deal to update fstab in this case but when I first encountered this couple of yrs ago, it took me a while before I realised where`s the problem...

Yes, that's true. But at least that's something caused by user's own action and doesn't happen too often (or, for most users, never).

Device names changing at boot is something that happens pretty much on every boot (if you have hardware with that "feature"), without user doing anything, and that can't be solved by any other way than using UUID or label.

I'd say that makes UUID the best default way of managing partitions. Every possible way of managing partitions in fstab has good and bad sides, but UUID is the only way that can be configured automatically and that works for every user (unless the user himself changes something in the system).

But of course you are free to configure your system in the way that works best for you. Most of users who play a lot with their partitions and experiment with different distros and operating systems are likely to be also capable of finding out how to change their fstab to use device names instead, if they want.

---

### Post by boof1988 on 2009-01-20
> **RyanVanDiemen said:**
> What I meant is that if you have a partition in fstab identified by UUID and then let`s say you decide to install new distro in this partition, installer will format the partition and assign new UUID to it. Once you reboot to your original distro it will not mount the partition to the folder you have specified in fstab because UUID is changed. You need to update UUID in fstab as well. That`s my point of disadvantage using UUIDs in fstab. Haven`t tried labels as you recommended yet...
Of course it`s not a big deal to update fstab in this case but when I first encountered this couple of yrs ago, it took me a while before I realised where`s the problem...

One doesn't have to format the partitions again (right before a new installation).  One can delete the files on the existing partition and then chose the "do not format the partition" option, but use the mount as / (or whatever mount point).  I believe that this should keep the same UUID.

---

### Post by Kevbert on 2009-01-21
Sounds like it might be worth adding the option of keeping the same UUIDs when performing a manual install of linux may be an option worth mentioning on the Brainstorming page.

---

### Post by mcduck on 2009-01-21
> **Kevbert said:**
> Sounds like it might be worth adding the option of keeping the same UUIDs when performing a manual install of linux may be an option worth mentioning on the Brainstorming page.

That would definitely be cool, and also possible. The installer would only need to check the UUID of a partition before editing it, and afterwards set it back to original.

Of course that would only help those playing with multiple versions of Ubuntu, every other distro and OS would still do what they want.

---

### Post by Kevbert on 2009-01-21
Brainstorm [[COLOR="Red"]link[/COLOR]]("http://brainstorm.ubuntu.com/idea/17524/").

---

### Post by RyanVanDiemen on 2009-01-21
> **mcduck said:**
> The installer would only need to check the UUID of a partition before editing it, and afterwards set it back to original.

That would be really good idea if it`s applicable. I saw your post on brainstroming page. Good idea.

---

### Post by mcduck on 2009-01-21
> **RyanVanDiemen said:**
> That would be really good idea if it`s applicable. I saw your post on brainstroming page. Good idea.

Actually I haven't posted anything there, you'll have to thank Kevbert for that. ;)

By the way, I'm starting to like the alternative solution AndrewLuecke has posted there. The only downside for swap files I know is fragmentation, but knowing how little swap is really used these days I don't think that would be much of a problem. Instead it would solve all the problems swap partitions have, and also allows suspending to disk (which will break if many distros share same swap partition).

---

### Post by Kevbert on 2009-01-21
This swapfile stuff looks very promising. Here's a [[COLOR="Red"]guide[/COLOR]]("http://www.cyberciti.biz/faq/linux-add-a-swap-file-howto/").  The drawback may be that it's not so good for small sized disk drives and if you use the file on a separate partition you'd need to permanently mount that partition.

---

### Post by unutbu on 2009-01-21
According to the AndrewLuecke ([http://brainstorm.ubuntu.com/idea/17524/](http://brainstorm.ubuntu.com/idea/17524/))
"swap files can be enlarged on the fly if the swap memory runs out"

How is that done?

---

### Post by RyanVanDiemen on 2009-01-21
> **Kevbert said:**
> Sounds like it might be worth adding the option of keeping the same UUIDs when performing a manual install of linux may be an option worth mentioning on the Brainstorming page.

> **mcduck said:**
> Actually I haven't posted anything there, you'll have to thank Kevbert for that. ;)


Sure, sorry, my bad :D Thanks Kevbert for that ;)

---

### Post by stimpyaw on 2009-04-10
Hello, this worked for me.  I had changed the size of my swap file from and did not realize the UUID had changed.  :oops:

I checked my fstab vs blkid and notice the change.  How come Ubuntu or the kernel does not update this automatically or even after using GParted how come that program does not update the fstab.

After rebooting system I have a swap file I don't have to turn on manually any more. WOOHOO!!

THANKS!

> **mcduck said:**
> Ok, the swap partition is not recognized, but at least there is one. Now we'll just need to get  Ubuntu to use it.

I bet the problem is with your fstab, most likely with the UUIDss for your partitions. Simply because that has been the reason every single time I've seen somebody with swap that doesn't work..

Could you post here your /etc/fstab file, and output of "blkid" command? (The command lists UUIDs for all your partitions).

(what you'll have to do is to compare UUIDs reported by "blkid" with the ones in /etc/fstab, and if there's any differences then edit the fstab to use correct UUIDs. After that you can reboot the machine and test if the swap is recognized. If not, run "sudo mkswap /dev/sda1" and "sudo swapon -a" and now the swap should be recognized. But before you do any of that please post the information I asked for so we can confirm that this really is what you need to do.)

---

