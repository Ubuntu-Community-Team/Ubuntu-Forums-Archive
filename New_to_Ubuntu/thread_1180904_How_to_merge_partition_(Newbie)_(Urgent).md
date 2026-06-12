---
title: "How to merge partition (Newbie) (Urgent)"
date: 2009-06-07
forum: New to Ubuntu
---

### Post by ubfu on 2009-06-07
Using window XP , which I can't merge external hard disk partition.

If I am to use Ubuntu live cd , can I merge them ? any guiding step merging it ?


I had J,K,L,M

J= Primary partition
K= (Deleted the date but it remain as a partition) Now it's unallocated 
L= Primary partition
M= Primary partition

Extra 170GB space 

How do I merge them ?

---

### Post by kwacka on 2009-06-07
Try partition manager (gparted) on the Live Cd to edit partitions - expand J into the free space which was K to make one partition, copy data from L, delete L, expand J, and repeat for partition M.

---

### Post by elliotn on 2009-06-07
U cant u need to format da whole drive, I tryd with gparted but failed

---

### Post by jbruced on 2009-06-07
Sounds scary. 
Defragment all Windoze partitions twice.
Back-up everything in sight!

I'd copy data I need from one to the other(say copy data on b partition to a partition), shrink or delete the partition I don't want(b), resize the partition I do want(a). 

Did I mention backup?

[edit] kwaka beat me to it. Hooray for kwaka, good advice.

---

### Post by ubfu on 2009-06-07
I mean I did a mistake on the previous partition

I had J,K,L,M and 170GB of free space.A big mistake I made.
Finding out , max on 4 primary or 3 primary 1 logical.
I remove and delete the K logical partition and I plan to merge with the extra 170GB space.

J= Primary partition
K= Logical Partition (I deleted the logical partition)
L= Primary partition
M= Primary partition
Extra 170GB space

---

### Post by ubfu on 2009-06-07
How do I type in ubuntu terminal checking an external hard disk drive ?

sudo fdisk -l is for my hard disk.But how about external hard disk via USB ?

---

### Post by ubfu on 2009-06-07
Anyone know what's the command line to check external hard disk size and partition ? 

I can only attach window's parition

I wanted to merge the 2 unallocated space together which is 48GB and 172GB.

[IMG]http://ubuntuforums.org/picture.php?albumid=1164&pictureid=4209[/IMG]

Thank you very much :)

---

### Post by heroidi on 2009-06-07
If you want to merge it with you'r data partition you can press Resize/Move and whrite a bigger number of space and it automaticlly allocates the free space to that partition and you can make the free space as patition too if you press new partition just choose the filesystem press apply and everything done.

---

### Post by ubfu on 2009-06-07
Sorry , 
I wanted to merge the unallocated partition from above to form a extended partition.
Which means 48GB + 172GB = 220GB extended partition.
So I can create as many logical partition as I wanted

---

### Post by miegiel on 2009-06-07
> **ubfu said:**
> How do I type in ubuntu terminal checking an external hard disk drive ?

sudo fdisk -l is for my hard disk.But how about external hard disk via USB ?

My *sudo fdisk -l* lists my external USB disk.

```
:~$ sudo fdisk -l
...
...
...

Disk /dev/sdf: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6dfe2621

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1         131     1052226    b  W95 FAT32
/dev/sdf2             132        3647    28242270    7  HPFS/NTFS
```

---

### Post by ubfu on 2009-06-07
Nope it does not list my external hard disk drive.
Anyone know why ?

---

### Post by LewRockwell on 2009-06-07
sounds like you should rescue everything you want to save and then DBAN or Killdisk the hard drive and start over

---

### Post by LewRockwell on 2009-06-07
is jumper on drive set to correct position?

some of my machines don't like the "cable select" position.

---

### Post by ubfu on 2009-06-08
> **LewRockwell said:**
> sounds like you should rescue everything you want to save and then DBAN or Killdisk the hard drive and start over
> **LewRockwell said:**
> is jumper on drive set to correct position?
some of my machines don't like the "cable select" position.

I don't understand , you wanted me to Killdisk or wipe all my data ? 
It just can't detect through USB.

Jumper ? not too sure since it's an external hard disk but what about cable select ? 

[B]The weird problem is it able to detect at window but not at ubuntu.
If anyone know why ?[/B]

Thank you

---

### Post by joyneo04 on 2009-06-08
its not possible from running the live cd...u have to install it....but there is an option like using ubuntu over windows....so u can install that.....

---

### Post by miegiel on 2009-06-08
> **ubfu said:**
> The weird problem is it able to detect at window but not at ubuntu.
If anyone know why ?

Maybe checking the disk for errors in windows will fix it. That's what I had to do once to mount my windows partitions in ubuntu. It turned out the windows partitions didn't properly unmount in windows for some reason.

---

### Post by ubfu on 2009-06-08
> **miegiel said:**
> Maybe checking the disk for errors in windows will fix it. That's what I had to do once to mount my windows partitions in ubuntu. It turned out the windows partitions didn't properly unmount in windows for some reason.

Tested with ubuntu 8.04 ,and it detects while newer version 9.04 doesn't.

What's the difference between them ?

---

### Post by LewRockwell on 2009-06-08
> **ubfu said:**
> Tested with ubuntu 8.04 ,and it detects while newer version 9.04 doesn't.

What's the difference between them ?

others are having this issue as well

---

### Post by joyneo04 on 2009-06-08
what you are saying that u are able to select partition through 8.04 but not through 9.04 don't know why you are facing this problem because i was using ubuntu 9.04 in my system and experimented a lot regarding partition manager and i was able to create ,move ,and delete partition in my internal hdd.now coming to external hdd which i am using after destroying my own internal hdd ,when i run gnome partition editor through bootable cd...it gave me the external hdd.

---

### Post by ubfu on 2009-06-08
> **joyneo04 said:**
> what you are saying that u are able to select partition through 8.04 but not through 9.04 don't know why you are facing this problem because i was using ubuntu 9.04 in my system and experimented a lot regarding partition manager and i was able to create ,move ,and delete partition in my internal hdd.now coming to external hdd which i am using after destroying my own internal hdd ,when i run gnome partition editor through bootable cd...it gave me the external hdd.

Sorry I don't quite understand.

Firstly I created a topic regarding on how to merge partition on my external hard disk.I didn't install any ubuntu yet and I plan to do it after I manage well the partition.

I can't do any resize and merging using window XP partition except using shareware like partition magic which I don't plan to buy any.
I found out ubuntu Gparted can do it and there I go.

But things doesn't turn out well.Booted a live cd of Ubuntu 9.04 and I surprise it didn't detect my external hard drive.Typing  sudo lsusb shows there is an external usb port use but it doesn't detect it.
My previous topic [http://ubuntuforums.org/showthread.php?t=1181065](http://ubuntuforums.org/showthread.php?t=1181065)

Did a lot of search but not much solution turn in since 9.04 is still new.
I tried with ubuntu 8.04 which I had it on had last year and surprise it auto mount my external hard drive on startup.
I still need help on the lastest 9.04 (unable to detect external hard drive) 
[http://ubuntuforums.org/showthread.php?t=1181065](http://ubuntuforums.org/showthread.php?t=1181065)

Back to topic 

I wanted to merge 2 unallocated partition but I doesn't know how to do it at gparted.
I hope someone can help me out.Here I attached a picture of the partition detected using 8.04 boot live cd gparted.

J= Primary partition (NTFS 58GB)(sdb1)
1#= Unallocated (48GB)
L= Primary partition (NTFS 58GB)(sdb2)
M= Primary partition (NTFS 126GB)(sdb3)
2#= Unallocated (170GB)


I wanted to merge both 1# and 2# unallocated partition into one Extended logical partition.Can someone guide me the step on doing it ? 

Many thanks for reading this long post.Thank you

---

### Post by miegiel on 2009-06-08
> **ubfu said:**
> Back to topic 

I wanted to merge 2 unallocated partition but I doesn't know how to do it at gparted.
I hope someone can help me out.Here I attached a picture of the partition detected using 8.04 boot live cd gparted.

J= Primary partition
1#= Unallocated 48GB
L= Primary partition
M= Primary partition
2#= Unallocated 170GB


I wanted to merge both 1# and 2# unallocated partition into one Extended logical partition.Can someone guide me the step on doing it ? 

Many thanks for reading this long post.Thank you

Hmmm .... let me guess
If you right click sdb2 *"resize / move"* is grayed out ?

---

### Post by LewRockwell on 2009-06-08
if this data is valuable then you should back it up to another drive BEFORE attempting this procedure.

grow/enlarge/increase the size of your sdb2 to use all the unallocated space between sdb1 and sdb2. Apply your changes to successfully complete this task.

now shrink/reduce/decrease the size of sdb2 leaving the new unallocated space between sdb2 and sdb3. Apply your changes to successfully complete this task.

now do the same thing to sdb3 that we did to sdb2.

now you should have all the unallocated space together. Select that area and create a new extended partition. Apply changes to complete this task.

now you can create/manipulate/delete logical partitions within the extended partition as you desire.

Note: These procedures may take an extended period of time.

Never give up, never surrender!

---

### Post by miegiel on 2009-06-08
If you can't resize/move the partitions with the ubuntu live disk you might want to try the [_GParted Live CD_]("http://gparted.sourceforge.net/livecd.php").

Else :
[LIST]
[*]Make a new temporary partition at the end of your disk (in ubuntu or windows)
[*]Copy everything in sdb2 and sdb3 to separate directories on the new temporary partition (don't forget to copy hidden files too).
[*]Delete sdb2 and sdb3 and make 2 new partitions in the freed space.
[*]Copy all the stuff from the temporary partition to the new sdb2 and sdb3 partitions.
[*]Delete the temporary partition and make a new extended partition for your linux partitions.
[/LIST]

ps Windows might make a mess of your drive letters :twisted:

---

### Post by ubfu on 2009-06-08
> **LewRockwell said:**
> if this data is valuable then you should back it up to another drive BEFORE attempting this procedure.

grow/enlarge/increase the size of your sdb2 to use all the unallocated space between sdb1 and sdb2. Apply your changes to successfully complete this task.

now shrink/reduce/decrease the size of sdb2 leaving the new unallocated space between sdb2 and sdb3. Apply your changes to successfully complete this task.

now do the same thing to sdb3 that we did to sdb2.

now you should have all the unallocated space together. Select that area and create a new extended partition. Apply changes to complete this task.

now you can create/manipulate/delete logical partitions within the extended partition as you desire.

Note: These procedures may take an extended period of time.

Never give up, never surrender!

Thanks , seems like it will take a lot of time moving from part to part.

If I am understanding well , I need to move my unlocated partition 48GB #1 to the middle of sdb2 and sdb3.
Then from the middle of sdb2 and sdb3 moving it to sdb3 and 2# unallocated partition.
Process will take a lot of time since file are to be move from the last sector to the front of the sector.
Like (1 = data , 0 = free space)

-After resize sdb2 , 48GB [00000] + 58GB [111111] = 106GB [00000111111] then moving files from the last sector to the front of the sector  = before [00000111111] after [11111100000]
-Resize back the sdb2 back to 58GB , getting again unallocated 48GB between sdb2 and sdb3
-After resize again sdb3 126GB + 48GB = 174GB and move the files from the last sector to the front of the sector again.
-So lastly the resize back the 174GB to 126GB and the unallocated file is at the back end.

I'd take like half a day to do that.[B]Rather than wasting time , if it's possible to just merging sdb2 + unallocated like above to become 106GB.
So can I still create a logical partition at 172GB if I had merge both sdb2 (58GB) + unallocated (48GB) ?[/B]

Thank you :)

---

### Post by LewRockwell on 2009-06-08
> **ubfu said:**
> Thanks , seems like it will take a lot of time moving from part to part.

If I am understanding well , I need to move my unlocated partition 48GB #1 to the middle of sdb2 and sdb3.
Then from the middle of sdb2 and sdb3 moving it to sdb3 and 2# unallocated partition.
Process will take a lot of time since file are to be move from the last sector to the front of the sector.
Like (1 = data , 0 = free space)

-After resize sdb2 , 48GB [00000] + 58GB [111111] = 106GB [00000111111] then moving files from the last sector to the front of the sector  = before [00000111111] after [11111100000]
-Resize back the sdb2 back to 58GB , getting again unallocated 48GB between sdb2 and sdb3
-After resize again sdb3 126GB + 48GB = 174GB and move the files from the last sector to the front of the sector again.
-So lastly the resize back the 174GB to 126GB and the unallocated file is at the back end.

I'd take like half a day to do that.[B]Rather than wasting time , if it's possible to just merging sdb2 + unallocated like above to become 106GB.
So can I still create a logical partition at 172GB if I had merge both sdb2 (58GB) + unallocated (48GB) ?[/B]

Thank you :)

now you see why I asked in an earlier post if you could just save what you needed and wipe the whole drive.

and yes I think you should just enlarge your sdb2 to include the unallocated area currently between sdb1 and sdb2...and then you can create an extended partition with your 172GB space

(and, as a note to others who are following this thread, this is why it's relatively important to plan out your partitions in advance. There are many discussions and tutorials on partitioning strung across the interwebs for your viewing and learning pleasure.)

Never give up, never surrender!

---

### Post by ubfu on 2009-06-09
> **LewRockwell said:**
> now you see why I asked in an earlier post if you could just save what you needed and wipe the whole drive.

and yes I think you should just enlarge your sdb2 to include the unallocated area currently between sdb1 and sdb2...and then you can create an extended partition with your 172GB space

(and, as a note to others who are following this thread, this is why it's relatively important to plan out your partitions in advance. There are many discussions and tutorials on partitioning strung across the interwebs for your viewing and learning pleasure.)

Never give up, never surrender!

Yep , I mess up my partition because I don't know much about limitation of 4 primary.
And as a newbie who doesn't know about ubuntu partition

Firstly I though Ubuntu needed a primary partition to install like window.Didn't know that it can be install even on a extended partition
Second I never though Unbuntu need an extra partition on swap , thinking it same as window page files within the partition.

This 2 question brings up the mess on my partition.Anyway thanks , will report back after I install ubuntu.thanks :)

---

