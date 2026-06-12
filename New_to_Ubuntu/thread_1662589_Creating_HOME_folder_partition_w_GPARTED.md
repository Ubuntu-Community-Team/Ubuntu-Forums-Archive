---
title: "Creating /HOME folder partition w/ GPARTED ????"
date: 2011-01-08
forum: New to Ubuntu
---

### Post by ozark_hillbilly on 2011-01-08
OKAY...instead of trying to transfer /home folder data at upgrade I have decided to attempt to create a new partition to house my /home data.
Attached is a screenshot of GPARTED that shows my existing partition info.
What is a good way to allocate my primary hard drive to have this /home partition?
SOLVED: I wanted to downsize the NTFS (DOS) partition as well. But the resize/move options are at half-intensity and not selectable.    >Drive must be UNMOUNTED first....duh

I do have a backup made by "Simple Backup" on another hard drive.

Also once I get a new partition set up for /home how do I flag it to be used by Linux? After all this can I then go in and delete the /home folder in the originl Linux partition to create some free space?  

Anyone who has a good experience level please chime in. I really don't want "try this" advice as screwing around with disk partitions is not to be taken lightly.

Unrelated: when trying to copy the /home folder to a zipdrive using sudo nautilus I got an error saying I did not have permission to copy certain files in my /Ed folder. I thought under nautilus as a superuser I had root privileges?

---

### Post by Phillip Spencer on 2011-01-08
Hi,

Good luck with this... I am sure you will get some good advice on this forum as I did a while back when I had partitioning problems.  I am not going to advise you to "try this" as there are far more experienced people on this who can help.

> **ozark_hillbilly said:**
> Anyone who has a good experience level please chime in. I really don't want "try this" advice as screwing around with disk partitions is not to be taken lightly.

I am not going to advise you to "try this" as there are far more experienced people on this who can help.  One issue is always "is this good advice?".  If you want to see the sort of advice I received and the people / approach that helped check out:
[http://ubuntuforums.org/showthread.php?t=1491232](http://ubuntuforums.org/showthread.php?t=1491232)

> **ozark_hillbilly said:**
> Unrelated: when trying to copy the /home folder to a zipdrive using sudo nautilus I got an error saying I did not have permission to copy certain files in my /Ed folder. I thought under nautilus as a superuser I had root privileges?  This sounds like another problem I had. See:
[http://ubuntuforums.org/showthread.php?t=1523204](http://ubuntuforums.org/showthread.php?t=1523204)

Cheers
Phillip

---

### Post by WthIteh on 2011-01-08
About /home partition:
You could create your /home partition using the unallocated free space (36.91GB) as a new Primary Partition (sda3). It is also possible to resize sda2 and create home partition within it but it is not required at all.
When created, you could tell Linux to use it as home partition by setting /home as its mount point.

NOTE: You should not continue installation with two home partition. The easiest way is to first create the mentioned home partition. You could do it without running installer from LiveCD, simply by running gparted. Then you could copy your home information (which should be currently in sda2 as it seems in your screenshot) to the new partition.
Then you could remove your previous /home completely. And then set new partition during installation by setting /home as its mount point.

About NTFS partition:
It is possible to do it with gparted but I'm not going to say how. Indeed I could not recommend doing so with gparted in anyway. If you have a windows on that partition, boot with windows and resize it there. gparted could damage ntfs partitions during resizing in many cases.

---

### Post by ozark_hillbilly on 2011-01-08
I am leaning toward resizing sda2 and creating /home within that. Could I reduce ext3 since /home will be coming out of it and put in the new partition. The /home folder is the one that will grow the most over time right?

I would like to keep the unallocated area alone for now if possible.

---

### Post by drs305 on 2011-01-08
> **ozark_hillbilly said:**
> I am leaning toward resizing sda2 and creating /home within that. Could I reduce ext3 since /home will be coming out of it and put in the new partition. The /home folder is the one that will grow the most over time right?

I would like to keep the unallocated area alone for now if possible.

Yes you can. A system partition of 10-15GB should be more than enough if your data and home folders will be elsewhere. Backup any important data before resizing any of your partitions. Since you have so much data in the partition, make sure you move it before you try to shrink the / partition that much!

---

### Post by WthIteh on 2011-01-08
> **ozark_hillbilly said:**
> I am leaning toward resizing sda2 and creating /home within that. Could I reduce ext3 since /home will be coming out of it and put in the new partition. The /home folder is the one that will grow the most over time right?

I would like to keep the unallocated area alone for now if possible.
Yes, you could resize ext3 and prepare free space for a new partition there.
It is not always the case. The /usr is a competing partition when you are going to install more software. It is a good practice to keep all partition 50% used. You could check size of current /usr and /home partition using
```
du -hs /usr
```
and
```
du -hs /home
```
commands, so you could find a clue about right new size for your partitions.

---

### Post by oldfred on 2011-01-08
You can shrink root to 10 or 20GB, but it currently has your /home data in it so you cannot make it that small. You could do it in two steps.

To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
Uses cp -ax
[http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html](http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html)
cp without -a and copying as sudo root takes ownership

If you have copied /home data to NTFS partitions, you will lose permissions & ownership. See this post and summary steps at end to reset ownership & permissions:

Sometimes there are dmrc errors or permission errors and this has how to correct them:
[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)
#Replace all instances of username with your login name.
sudo chown username:username /home/username/.dmrc
chmod 644 /home/username/.dmrc
sudo chown username:username /home/username     
chmod 755 /home/username

---

### Post by Bucky Ball on 2011-01-08
Can't help with transferring your /home data to the new one but I would delete the /swap while you're at it, create your new /home partition, and put /swap last (slowest part of the drive - not much use having a /swap blob you will hardly ever use in the middle of the drive).

Just a thought. ;)

---

### Post by Habeouscorpus on 2011-01-08
Don't forget to make a backup before doing anything! (Why tempt Murphy's Law?)

---

### Post by MoebusNet on 2011-01-08
Aysiu has a tutorial he wrote about creating a separate /home partition after installing ubuntu without the separate /home. He wrote it a while back and isn't maintaining it, but it might give you an overview and some ideas on how to proceed.

The tutorial is here: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

I suggest you read it through a couple of times and then make your plan before you proceed. Best of luck!

---

### Post by ozark_hillbilly on 2011-01-08
Thanks BB....I will probably do that as well.

---

### Post by ozark_hillbilly on 2011-01-08
Stumbling block:

Was suggested to move / files out of partition before downsizing. I transferred / files to a temp folder on my backup hard drive. Then I went to unmount the /dev/sda5 partition to allow it to be resized . GParted wouldn't let me unmount. So now I have transferred / files back to sda5 and wonder what to do  next.

Attached is the error display from GParted unmount attempt.

I am using the PartitioningHomeMoving Guide under Community Documentation as I attempt these changes....

---

### Post by Verbeck on 2011-01-08
> **ozark_hillbilly said:**
> Stumbling block:

Was suggested to move / files out of partition before downsizing. I  transferred / files to a temp folder on my backup hard drive. Then I  went to unmount the /dev/sda5 partition to allow it to be resized .  GParted wouldn't let me unmount. So now I have transferred / files back  to sda5 and wonder what to do  next.

Attached is the error display from GParted unmount attempt.

I am using the PartitioningHomeMoving Guide under Community Documentation as I attempt these changes....

you cant unmount the filesystem root / while using the file system

try it from a live cd

---

### Post by drs305 on 2011-01-08
> **ozark_hillbilly said:**
> Stumbling block:

Was suggested to move / files out of partition before downsizing.

You also want to make sure you are only moving data files out of the / partition until you have completed your manipulation of the repartitioning.

As Verbeck mentioned, you can't work on mounted partitions (key icon next to them) and you can't unmount system partitions while running the OS from that partition.

If you boot the LiveCD, your real system partition won't be mounted. You may have a swap partition mounted and you will have to unmount that by selecting it, then from the menu: Partition, Swapoff.

---

### Post by Bucky Ball on 2011-01-08
> **ozark_hillbilly said:**
> Stumbling block:

Was suggested to move / files out of partition before downsizing. 

!!! Why would you want to do that? Bad advice. Just resize. Backup your personal data from / if you have any but *ALL* files? No.

---

### Post by ozark_hillbilly on 2011-01-09
Bucky,

It was suggested by another forum member, I will avoid name pointing, to do this I believe to make the repartitioning faster and to reduce the size of the partition since /home would no longer reside there. But when I moved my data files out and looked at the partition w/ GParted the size was the same.
So I dunno. I am gonna try tomorrow to boot off CD and resize existing partition and then boot back up off hard drive and add new /home partition.
Keeping my fingers crossed.

---

### Post by Bucky Ball on 2011-01-09
That sounds good. There are ways of moving your old /home data to a new /home partition then deleting the old /home. You might want to post another thread regarding that when you get that far. ;)

---

### Post by drs305 on 2011-01-09
> **ozark_hillbilly said:**
> ... when I moved my data files out and looked at the partition w/ GParted the size was the same.

You would move any/all data files (such as music, videos, etc) out of the / partition to allow it to be reduced in size. Generally the Ubuntu installation would take less than 10GB of space if the user had no personal files in the partition. Once these files are removed, the partition could be made smaller with Gparted. 15GB is normally a comfortable size for / if you don't intend to store your personal files therein.

The size of the partition will not change as data is removed, as the partitions are a fixed size. Gparted shows the amount of space being used by shading it yellow. You must not shrink the partition into the 'yellow' zone or you will lose files. You *can* shrink the partition once you have moved personal files out of the partition, but it won't do it automatically.

---

### Post by ozark_hillbilly on 2011-01-09
OKAY I booted under LIVE CD and added new /home partition.
Then following Partitioning Home Moving community doc I did this:

1. Duplicate your fstab file:

sudo cp /etc/fstab /etc/fstab.$(date +%Y-%m-%d)
2. Compare the two files to confirm the backup matches the original:

cmp /etc/fstab /etc/fstab.$(date +%Y-%m-%d)
3. Open the original fstab in a text editor:

gksu gedit /etc/fstab 
and add these lines into it

# (identifier)  (location, eg sda5)   (format, eg ext3 or ext4)      (some settings) 
UUID=????????   /media/home    ext3          nodev,nosuid       0       2 
and replace the "????????" with the UUID number of the intended /home partition.

*****************************************************
After adding the new data my fstab looks like this:


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=9360d76a-ddb7-4a4a-8a92-21d35c903ad3 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=2d31d0c7-73ab-4b92-a354-c34d2bb6bf5c none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

# /dev/sdb1
UUID=7a117704-c5b0-4858-92c4-16e95deb55f9    /media/backupdrive    ext3    relatime    0    2

# new home partition setup
# (identifier)  (location, eg sda5)   (format, eg ext3 or ext4)      (some settings) 
UUID=d1bad45a-7159-4875-a77d-67b3a55c00a4   /media/home    ext3          nodev,nosuid       0       2           
    


# Floppy Drive
/dev/fd0        /media/floppy0     auto     rw,user,noauto,exec,utf8    0  0

************************************************************

I tried to mount the partition but got an error message that said:

ed@House:~$ sudo mount -a
[sudo] password for ed: 
mount: mount point /media/home does not exist
ed@House:~$ 

Under "Places" it shows the Home Partition but it says I am not privileged to mount....


Uh oh... looking for some suggestions.... thanks

Ed

PS   my new home partition is sda6 according to blkid and I noticed that before I repartitioned/moved swap, etc that sda6 was the Linux swap...does this need fixed??

ed@House:~$ blkid
/dev/sda1: UUID="30182B1D182AE218" TYPE="ntfs" 
/dev/sdb1: UUID="7a117704-c5b0-4858-92c4-16e95deb55f9" TYPE="ext3" SEC_TYPE="ext2" 
/dev/sda5: UUID="9360d76a-ddb7-4a4a-8a92-21d35c903ad3" TYPE="ext3" 
/dev/sda6: LABEL="HOME Partition" UUID="d1bad45a-7159-4875-a77d-67b3a55c00a4" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: UUID="0f8995e5-fc02-48f4-ade7-5191c714b1e7" TYPE="ext4" 
/dev/sdb6: TYPE="swap" UUID="059f28b0-63d9-44a1-9de5-47213c36d238" 
/dev/sda3: TYPE="swap" UUID="17f5839e-8207-4b03-bdca-478e59159827" 
ed@House:~$

---

### Post by ozark_hillbilly on 2011-01-09
I have created some additional problems for myself. ](*,)](*,)

Evidently after resizing/reducing my original partition I don't have ANY spare free space. I cannot save a simple text file due to lack of space. ???  GParted shows 1.7gig unused (3%) on my Linux partition.

Under my wife's user area her browser will not load properly.

I am in the middle of moving /home to it's own partition and I don't know if these issues will correct themselves or not.

Ed

---

### Post by drs305 on 2011-01-09
The mount point in fstab is normally just "/home", not "/media/home".

I don't know how you set it up but you are getting the error because you don't have a mount point of "/media/home".  Your fstab, if you set it up as most do, should have the entry as:

> UUID=d1bad45a-7159-4875-a77d-67b3a55c00a4 /home ext3 defaults 0 2

I use 'defaults' for my /home options but others use what you had listed.

---

### Post by dBuster on 2011-01-09
> **ozark_hillbilly said:**
> Bump...

Wow not even an hour old and getting bumped...

Any how

Did you follow completely the guide at [PartitioningHomeMoving]("https://help.ubuntu.com/community/Partitioning/Home/Moving")?

Seems from what you posted earlier that you may have missed something.  That is just after a quick glance.

Also, didn't you already have a thread talking about this and your moving the home due to an upgrade you want to do?  I thought I subscribed to that one as well since I am about to undergo the same moving of home and then clean installing 10.04....

---

### Post by ozark_hillbilly on 2011-01-09
followed Home Partition/Moving to the letter....

---

### Post by ozark_hillbilly on 2011-01-09
drs,

I was following the community doc for Home Partitioning/Moving:

Setup Fstab

gksu gedit /etc/fstab 
and add these lines into it

# (identifier)  (location, eg sda5)   (format, eg ext3 or ext4)      (some settings) 
UUID=????????   /media/home    ext3          nodev,nosuid       0       2 
and replace the "????????" with the UUID number of the intended /home partition.

I don't know enough about Linux to know if /media/home is correct or just 
/home. I was going by information in the Ubuntu community documentation.
Now I'm on the verge of having a totally unusable Linux environment. 
No spare memory, wife's user area browser not loading, etc.
Should I try a restore or modify fstab to remove /media and just go with /home as mount point?
Not having any spare memory is a serious issue as I cannot even save screenshots for posting to the forum.

---

### Post by oldfred on 2011-01-09
It looks like you still are on step 2 as you have not yet mounted the newhome before even  copying your data.

The instruction may have left off a important point. To mount something in fstab it has to exist before, so you must create the mount before. To avoid confusion I prefer to use newhome and oldhome until everything is finalized into your actual new home.

sudo mkdir /media/newhome

This one does the same thing except it uses the cp command instead of rsync. 
[http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html](http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html)

---

### Post by ozark_hillbilly on 2011-01-09
I am getting more confused.   
Question 1: Does fstab get updated automatically after you change partitioning? sda6 used to be my swap file; after downsizing the original partition, creating new HOME partition, and deleting/creating swap file at bottom I have new assignment designators. Do these have to be updated in fstab? 

Question 2: When I commented OUT the fstab line "UUID=d1bad45a-7159-4875-a77d-67b3a55c00a4   /media/home    ext3          nodev,nosuid       0       2 " and rebooted I could then access the /Home partition under Places. Do I leave it like this and continue to step 3: 
Use rsync to migrate all data from /home into /media/home.

BLKID result:

root@House:/home/ed# blkid
/dev/sda1: UUID="30182B1D182AE218" TYPE="ntfs" 
/dev/sdb1: UUID="7a117704-c5b0-4858-92c4-16e95deb55f9" TYPE="ext3" SEC_TYPE="ext2" 
/dev/sda5: UUID="9360d76a-ddb7-4a4a-8a92-21d35c903ad3" TYPE="ext3" 
/dev/sda6: LABEL="HOME Partition" UUID="d1bad45a-7159-4875-a77d-67b3a55c00a4" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: UUID="0f8995e5-fc02-48f4-ade7-5191c714b1e7" TYPE="ext4" 
/dev/sdb6: TYPE="swap" UUID="059f28b0-63d9-44a1-9de5-47213c36d238" 
/dev/sda3: TYPE="swap" UUID="17f5839e-8207-4b03-bdca-478e59159827" 
root@House:/home/ed# 
**************************************************

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=9360d76a-ddb7-4a4a-8a92-21d35c903ad3 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=2d31d0c7-73ab-4b92-a354-c34d2bb6bf5c none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

# /dev/sdb1
UUID=7a117704-c5b0-4858-92c4-16e95deb55f9    /media/backupdrive    ext3    relatime    0    2

# new home partition setup
# (identifier)  (location, eg sda5)   (format, eg ext3 or ext4)      (some settings) 
#    UUID=d1bad45a-7159-4875-a77d-67b3a55c00a4   /media/home    ext3          nodev,nosuid       0       2           
    


# Floppy Drive
/dev/fd0        /media/floppy0     auto     rw,user,noauto,exec,utf8    0  0

---

### Post by oldfred on 2011-01-09
Whatever you do with partitions fstab will not change. If you delete something it is trying to mount then it will complain or not let you boot. I always run the mount -a after editing to make sure it works.

For the rsync command to work it has to have a from and a to mount points, from is you existing /home but you have to create a mount for sda6 and call it something unique and mount sda6 to that mount point. Then the rsync will work. It looks like some instructions have you edit fstab, others have you just manually typing in a mount command. Either will work.

If you have copied with rsync all your data from your home that is in your root partition to sda6, then you should add the /home to fstab. As drs305 mentioned above, not as /media/home but just /home with the UUID from sda6.

---

### Post by ozark_hillbilly on 2011-01-09
I figured out the errors I was getting on boot w/ fstab.
SYNTAX was wrong. My new partition is titled HOME Partition; well you have to put an underscore between the two words evidently. I now have no bad format errors in fstab or mounting local filesystems errors on boot!!!!
After transferring /home folder to new /home partition I ran a diff check and it wasn't pretty. 
Can I simply do a Simple Backup restore from my backup and direct it to the new partition folder and then continue?
I currently have problems with Desktop operation and browsers. Also no spare memory. Hopefully when I go to new partition memory issues will go away. This was a result of moving files around trying to get original /home folder smaller before resizing. 

I am at the installation stage now of:

4. Edit fstab again so the new partition mounts as /home instead of /media/home but not reboot just yet.
5. Move /home to /old_home and reboot
6. Delete /old_home.

---

### Post by oldfred on 2011-01-09
Yes, I found out a long time ago Linux does not like spaces. There are workarounds, but I just do not use spaces anywhere any more.

Rsync is very good at making sure things match. After running rsync I am surprised you are finding differences. Sometimes a / at the end makes a huge difference on where entire folder or just files are copied. 

You should be able to restore backup, but was it to a linux file system or compressed so it preserved ownership and permissions. Otherwise you have to fix those also.

---

### Post by ozark_hillbilly on 2011-01-10
So close to throwing in the towel...:(

EVERYTHING went to hell in a handbasket....

So I am at a crossroads...I've spent past two days making next to no progress....so much for a sob story....

I decided after original partition got screwed up to reinstall 10.04 off CD and say to H$LL with 9.04 completely. I do now have a /home partition that has my user data from 9.04 on it. Good data I don't know.

So after installing 10.04 and overwriting Jaunty Jackelope I modified fstab to direct OS to the new /home partition.  WRONG!!!   Following errors occur on boot:

Could not update ICEauthority file /home/ed/.ICEauthority

Problem with configuration server.
(/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)



Forced to remove /home pointer in fstab as Desktop would not boot up properly. I can't even get network connection to work under 10.04. Using good ole DOS XP OS to type this crap in. 
Linux totally unusable at this point. 

If someone wants to give me a little push I'll go ahead and jump off the cliff. May be time to install DOS 7 and go on with my life. This effort in futility has me pretty whipped right now. :-({|= 

Any ideas...anybody ???

---

### Post by dBuster on 2011-01-10
Before you threw in the 10.04 and new installed did you make sure that your memory issues were not from a mis pointed swap drive location?  Swap drive being the partition, as you said it used to be #6 and then your home became #6...  That could have been where the whole thing started to go downhill.

I do not have your whole thread or your results up so I am just throwing this out there in case you had back ups and wanted to go at it again.  I believe something did go awry with the new partitioning you did, and or moving of partitions.

---

### Post by Bucky Ball on 2011-01-10
The wireless card might get up if you plug in an ethernet cable, get updates. Then System >Admin >Additional Drivers if you aren't already offered drivers and firmware for your card.

It's a start.

If there's any chance I would back up the data in /home you want to keep and just install, wiping out old, new, middle-aged, and whatever other partitions are on the and start fresh. Then put your personal data in your /home partition and done.

---

### Post by oldfred on 2011-01-11
I posted this back in #7. dmrc errors need you to reset permissions.

Sometimes there are dmrc errors or permission errors and this has how to correct them:
[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)
#Replace all instances of username with your login name.
sudo chown username:username /home/username/.dmrc
chmod 644 /home/username/.dmrc
sudo chown username:username /home/username     
chmod 755 /home/username

---

### Post by ozark_hillbilly on 2011-01-11
Well I am one the road to recovery at last!
Thanks to Oldfred, Bucky Ball, and others.

Ended up wiping home partition and reformatting. 
Learned hard way about using chown & chmod without 100% certainty;
this caused sudoers errors and inability to run as superuser in terminal mode.

Unfortunately I did not have a clean transfer of data to /home partition so I now must retrieve tar backup data and transfer manually. Ugh...

Google search is EXTREMELY valuable tool when you need info NOW;
like 1:00 am in morning.

Lots to do like activate Update Manager and go to 10.10.

Thanks again.

Ed

---

