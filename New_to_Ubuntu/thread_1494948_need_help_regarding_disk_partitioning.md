---
title: "need help regarding disk partitioning"
date: 2010-05-27
forum: New to Ubuntu
---

### Post by naiquevin on 2010-05-27
Hi, 

I have already installed ubuntu 10.04 using wubi on windows 7 but considering uninstalling it and installing it on a separate partition. But i am a bit confused about disk partitioning that is to be done before installation. 

i have a new hard disk and one drive (E on windows ) is completely empty which i want to assign to ubuntu. so if i select this particular partition during the installation process, will it be completely used up or will this drive be further divided into partitions ? i dont want to create any more partitions and allocate the entire E drive to ubuntu.

Secondly, i have 3 partitions (c,d,e on windows) but during installation it shows me 4 with the smallest one of them labeled 'free space' .. is this what is meant by 'swap space' ? Now at this stage which one should i select and go ahead? 

I know the questions are very silly but i am quite new to installing OSs although i have  good enough experience of working on ubuntu.

The main reason for reinstallation is that, i have been using a wubi installed ubuntu at work and it was great to start with. but the maximum space available to ubuntu is 30gb. Already having a feeling that i might be running out of space shortly ( only about 7 gb free as of today) 

So I want to try doing it on my home computer first so that i have some experience before i install it at work.  

Thanks. 
Vineet

---

### Post by vamc on 2010-05-27
Hi Vinnet, 

You can entirely allocate your E drive to ubuntu.If you select E drive as your '/' , it uses entire E drive for ubuntu. (Ofcourse there are some advanced options like repartition E drive for individual home and boot sectors).

Also, you have to allocate 'swap' area. (maybe you can use 'free space' mentioned above as swap area).If you do not have enough space consider repartitioning E drive.

Good Luck.

EDIT: A better option is to delete the E drive (delete it as a partition and it will be shown as free space). Then select the option "Install them side by side choosing between each start-up".  Ubuntu will automatically detect the other operating system and install Ubuntu alongside it in the free space. 

For more details:                           [https://help.ubuntu.com/community/HowtoPartition]("https://help.ubuntu.com/community/HowtoPartition"). or

refer [The Ubuntu Manual]("http://www.ubuntumanual.org")

---

### Post by naiquevin on 2010-05-28
> **vamc said:**
> Hi Vinnet, 

You can entirely allocate your E drive to ubuntu.If you select E drive as your '/' , it uses entire E drive for ubuntu. (Ofcourse there are some advanced options like repartition E drive for individual home and boot sectors).

Also, you have to allocate 'swap' area. (maybe you can use 'free space' mentioned above as swap area).If you do not have enough space consider repartitioning E drive.

Good Luck.

EDIT: A better option is to delete the E drive (delete it as a partition and it will be shown as free space). Then select the option "Install them side by side choosing between each start-up".  Ubuntu will automatically detect the other operating system and install Ubuntu alongside it in the free space. 

For more details:                           [https://help.ubuntu.com/community/HowtoPartition]("https://help.ubuntu.com/community/HowtoPartition"). or

refer [The Ubuntu Manual]("http://www.ubuntumanual.org")

Hi vamc, 

Thanks for the reply. I have fair amount of space in E drive and the free space (which will be used as swap) is about 2GB , so i think i ll use it without partitioning. But i have some more questions. My E drive in windows currenlty is ntfs. Will it cause any problems if i keep it ntfs or is it better to change it something else ? If yes then what should i change it to ? 

Thanks again.

---

### Post by ranch hand on 2010-05-28
An even better idea is to boot to you Live CD and run;
[code]
sudo fdisk -l
[code]
That is a lower case L at the end of that command.

Post the results here.

This will let us know exactly what your partition table is and how it can best be used.

If you are going to install 10.04 on its own it would be better to install it using the manual partioning option when installing.  That way you can have a separate / (root) partition and a /home partition along with your /swap partition.  This is good if you need to reinstall at some time for some reason.  You can then have the partitioner in the installer just format the / partition, not format the /home partition and your data and config files will be  nice and safe on the /home partition (backing up is still a good idea but I have done this several time and never lost a thing).

Here is an example of the above command from my sda drive;
> 
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004630f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        4698    37736653+  83  Linux
/dev/sda2           18210       38913   166304880    5  Extended
/dev/sda4            4699       18209   108527107+  83  Linux
/dev/sda5           18210       20774    20603331   83  Linux
/dev/sda6           20775       28238    59954548+  83  Linux
/dev/sda7           38632       38913     2265133+  82  Linux swap / Solaris
/dev/sda8           28239       31127    23205861   83  Linux
/dev/sda9           31128       38631    60275848+  83  Linux

Partition table entries are not in disk order


---

### Post by Elfy on 2010-05-28
> Thanks for the reply. I have fair amount of space in E drive and the free space (which will be used as swap) is about 2GB , so i think i ll use it without partitioning. But i have some more questions. My E drive in windows currenlty is ntfs. Will it cause any problems if i keep it ntfs or is it better to change it something else ? If yes then what should i change it to ? 

It will be formatted to a linux type - ntfs will be no use.

Basically if you delete that partition you will be able to use the resulting free space to install into - the installer will create the partitions it needs.

I would +1 ranchhand - at the moment you are talking about c:\ d:\ etc - linux does not use that :)

---

### Post by naiquevin on 2010-05-28
yes a command like that would really help.. i am still thinking in terms of c:,d:,e etc. :P
Unfortunately cant try it now. will do it when i get back home ..thanks for the help .

---

### Post by naiquevin on 2010-05-28
hi i did 
[code] sudo fdisk -l [code] and this is the output

> 
[1]+  Stopped                 man fdisk
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe1e8878b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       12749   102296576    7  HPFS/NTFS
/dev/sda3           12749       41432   230400000    7  HPFS/NTFS
/dev/sda4           41432       60801   155583488    7  HPFS/NTFS

Disk /dev/sdb: 1998 MB, 1998519808 bytes
32 heads, 63 sectors/track, 1936 cylinders
Units = cylinders of 2016 * 512 = 1032192 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6ad436c2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1  



what would be the recommended way to proceed from here ?

---

### Post by naiquevin on 2010-05-28
okay . so after a bit of searching, i think i have figured out how to go about it. but i still need to confirm a few things before i hit delete on one of my partitions as i wouldnt want to break anything in the process and also make sure i dont have to reinstall ubuntu anytime soon. i request you guys to confirm if the following procedure would be correct. 

1) i open computer management in windows and go to disk managament section under storage
2) there are 4 partitions - c, d, e + system reserved  (sorry for using the letters again :)) 
3) i have an option to delete them .. i choose the e:\ and delete it
4) now e is no longer visible on windows. ( just a guess at this point)
5) but now when i install ubuntu i can see it as 'free space'
6) i choose manual partition and select this free space. create a partition table. 1 primary partition (selecting /) + around 2-4 gb of swap area + one logical partition. ( what directory do i select here ? ) 
7) so now i have 2 big partitions and a small swap space for linux which will not be available for storage when logged into windows. 

is this right ? 

and in future if i need to install another OS, can i free up the second big partition from ubuntu and use it ? 

 looking forward to your replies. Thanks for bearing with me.

---

### Post by ranch hand on 2010-05-28
And which of these is it that you are planning on using?  I take it that it is sda3 and that sda4 is the empty one you mention.

If that is correct I would use gparted on your LiveCD (System>Administration>Gparted) to delete those 2 partitions.

One thing you must know is that you are limited to 4 "primary" partitions on any drive.  So you have 2 after deleting sda3 and sda4.  You want to have 3 for Ubuntu.  This makes 5 and will not work.

An "extended" partition is a type of "primary" partition that allows you to create any number of "logical" partitions inside of it.

I would create an extended partition where you deleted the 2 unneeded (sda3 and 4).  With in it I would put a /swap partition, twice the size of your ram, at the end of that extended partition.  At the beginning of the extended partition I would put a 10 to 15GB / partition.  The rest of the extended partition (in the middle) would be for your /home partition.

Format the swap partition as "swap"  when you create it.  The other 2 can be formatted by the installer when you install.

When you install choose the "manual" option when you get to the partitioner.  By right clicking on a partition you will get a menu.  Select "change" and just tell it to use the partition as ext4, mount point / or /home )which ever it is), check the format box and go to the other partition and do the same thing.

One thing that can't be over said is watch the installation closely and if prompted to choose where to install grub make sure that sda ONLY is marked.  There is a tendency to mark all of the partitions.  Grub does NOT go on a partition.  If it does you will totally screw your MS boot sector and have to repair it.  This is a pain and does not need to happen if grub is just installed on sda.

---

### Post by Elfy on 2010-05-28
All of that by ranch hand.

I would be inclined to delete the partition in windows - you'll not confused over differences in partition naming. I would also allow the installer to install in the largest free space - it will create the partitions it will need - and extended and 2 logicals.

If you get confused try some live help - link in my sig will take you to the beginners team help channel - there's usually someone about - and you can do that from within the livecd while you are installing.

---

### Post by naiquevin on 2010-05-29
> **ranch hand said:**
> And which of these is it that you are planning on using?  I take it that it is sda3 and that sda4 is the empty one you mention.

i think i am still missing something. sd4 is the empty one i am talking about but i dont want to delete sd3 as all my data on windows is stored there.  it is the largest partition on windows and after installing ubuntu, i might need to be able to mount this drive to access the data from ubuntu.

do i need to delete two partittions because of the 4 primary partition limit? I thought i could delete only sd4 in windows and create an extended partition when prompted during ubuntu installation so that it can be divided further into logical partitions. Please correct me.  Thanks a lot. 



> **forestpiskie said:**
> All of that by ranch hand.

If you get confused try some live help - link in my sig will take you to the beginners team help channel - there's usually someone about - and you can do that from within the livecd while you are installing.

for some reason i am not able to access the internet when i boot from the live cd. that is a different issue though. but if it works it would be really nice to have some live help.. thanks

---

### Post by ranch hand on 2010-05-29
That is why I asked.  I really do not know a thing about the way Win JerryLewis Pro is set up or the insane way they designate partitions.  Yes I know, I are ignernt.

What you propose should work fine.

I do not know why you have a network problem.  Are you on wireless or wired?  If wireless can you plug the bugger in?

If you right click on the network applet (upper left on panel) you can make sure that networking is enabled, you can also edit the connection there.

---

### Post by naiquevin on 2010-05-30
sorry for not posting any update.. had been away from the comp for a while. I 
guess i should just do it now without thinking any further ..lets see whatever happens. 
will come back if i am stuck. Thanks for all the help guys.

---

### Post by ranch hand on 2010-05-30
> **naiquevin said:**
> sorry for not posting any update.. had been away from the comp for a while. I 
guess i should just do it now without thinking any further ..lets see whatever happens. 
will come back if i am stuck. Thanks for all the help guys.
It is not a good thing to rush these things.  By all means take your time.

---

### Post by naiquevin on 2010-05-31
> **ranch hand said:**
> It is not a good thing to rush these things.  By all means take your time.

hi ranch, 

I am already stuck . so i think i should follow your advice. I am trying to install ubuntu with manual partitioning. it shows me four devices under sda - sda1, sda2, sda3 and free space. i clicked on the free space and selected 'add'. I created a primary partition with mount point '/' selecting all the available space. it lets me do it and labels the new disk sda4. But now i cant create any disks further. i know there are only 4 primary partitions allowed. But here i want to create 2 new logical partitions from the sda4, one for swap and one for '/home'. it doesnt let me proceed further from here. 

The other thing i tried was creating a logical partition first (for swap) which happens without any problems (labeled sda5) and it lets me create another partition too . now i wanted to make a logical partition with mount point '/'  but the option to slect between primary and logical was no longer  available now . I still went further but it named the new partition sda6 which as per my limited knowledge is another logical partition since a primary partition would have been labeled sda4.  why is it not letting me create the fourth primary partition? am i missing something here ? 


Edit: 
now I tried using gparted inside the live session to create an extended partition sda4 having all of the initial free space. 
when i type the command fdisk -l in terminal it shows me sda4 ans extended partition. But the ubuntu installer still shows only 3 partitions and the free space as it was doing earlier.. please help.  

o/p of fdisk -l 
> 
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe1e8878b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       12749   102296576    7  HPFS/NTFS
/dev/sda3           12749       41432   230400000    7  HPFS/NTFS
/dev/sda4           41433       60801   155581492+   5  Extended
ubuntu@ubuntu:~$ 



Thanks .

---

### Post by ranch hand on 2010-05-31
Use gparted to create your /, /home, and /swap logical partitions in sda4.  Then in the installer just use those partitions.  If you format / and /home to ext4 when you create them you can skip formating in the installer partitioner altogether.

I find it a good idea to write down, yes I have mastered the pen and paper technology, the partitions that you create so that you KNOW what you are doing when you get to installing.  I have a lot of installs and it is really no fun to install on the wrong partition.

---

### Post by naiquevin on 2010-06-04
finally did it using gparted as suggested by ranch hand.. thanks everyone.

---

### Post by ranch hand on 2010-06-04
This is great to hear.

You should mark the thread as solved (top of page under Thread Tools).  This saves folks time when looking for answers to similar problems and folks popping in to help.

---

