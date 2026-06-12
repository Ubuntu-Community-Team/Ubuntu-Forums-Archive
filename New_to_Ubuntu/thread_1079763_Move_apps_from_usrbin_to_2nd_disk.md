---
title: "Move apps from /usr/bin to 2nd disk"
date: 2009-02-24
forum: New to Ubuntu
---

### Post by FredRW on 2009-02-24
I've been using Ibex as a vmware appliance in order to learn.
Of course, I've run out of space on "sda" the primary disk.

My question:

Is it possible to move applications from (sda) /usr/bin to a dir on a 2nd disk (sdb)? Can they just be copied and put a link to the new directory in usr/bin? Or is this not feasible? Is there an alternative other than have to make a new drive and move all files, which seems to be quite involved?

Could this also work with, e.g. usr/share/doc?

Thanks.

Fred

---

### Post by llamabr on 2009-02-24
Probably it would be best to do a fresh install.  Most of the config files will not work correctly just by copying them over.

---

### Post by geirha on 2009-02-24
This is Intrepid as a guestOS in vmware? If so, the easiest would be to just resize the virtual harddrive, then use gparted from the ubuntu CD to grow sda1 to fill the new space ...

---

### Post by epswinde on 2009-02-24
you could do it this way:

first, a warning.  I have only ever done this with a new physical disk, not a virtual one, and I cannot guarantee that it will be the same.

Create a new virtual disk for the vm to use.  I've never virtualized anything, so I dont know how this is really done. format it in whatever way is possible.  
Once that is completed, copy your /usr/bin to that new disk (sdb).

Then, edit your /etc/fstab to include the new disk, using the mount point as /usr/bin.  look at your other fstab entries for the proper options.  you should use the same ones as your root partition.

then (here's the really scary part) clean out the (sda) version of /usr/bin (cd /usr/bin && sudo rm -r *).  the mount point MUST be empty in order for the OS to mount anything there.  

reboot and you should have it all set up.

HOWEVER, this is by no means an exhaustive account of what needs to be done; and I definitely don't recommend it for beginners.  However, if you're willing to totally bork everything and reinstall the OS, then you could do it for a good learning exercise.

One of the best things about unix is that the file tree is totally device independent.  This means that not only can you have your /home and / on different partitions (or any other folder), but you can have a virtual, encrypted file system located in your /home/user folder, and mount it to /encrypteddevice (kinda recursive, but it really does have some good uses).  everything is a file, even a complete filesystem.  by 'mount' in a device, you are merely telling unix that "this is a file that contains information about how to find other files stored therein".  it could be mount -t ext3 /home/user/hidey\ hole /encrypted device instead of just mounting /dev/sda2 or whatever.

that kinda got out of hand there, but i geek out when i get to evangelize linux!

---

### Post by FredRW on 2009-02-25
Just a little more information please...

epswinde, you say to mount sdb in (sda)usr/bin but that (sda) usr/bin should be empty.

Doesn't (sda) usr/bin have to have a mount point dir for (sdb) usr/bin to mount (in)to?

Sorry, but I am rattled by your statement "HOWEVER, this is by no means an exhaustive account of what needs to be done..."

(sdb1) is currently mounted in /media/Ubuntu_2, I understand how to move its mountpoint in fstab, but I didn't think it would mount without a mountpoint fixed in /(any_dir). 

I'm not at home so can't say exact syntax but fstab line is with (similar)  UUID=###  /media/Ubuntu_2   defaults  0  1   
Should this be changed to something (similar) UUID=####  /usr/bin/Ubuntu_2  relatime errors=remount ro  0  1 

?

I really appreciated your additional information, by the way!

---

### Post by geirha on 2009-02-25
You can mount a partition to any directory, whether the directory contains files or not. If the directory you mount to contains files, nothing will happen to the files, they'll still be there, but hidden away. Instead you'll see the contents of the partiton you mounted there. If you unmount the partition, the files will reappear.

So, if you go with epswinde's approach, you do NOT need to remove the files in /usr/bin/ on sda. Just mount the partition on sdb over it and see if it works. Once you've confirmed that everything is working as it should, boot the ubuntu CD, and remove the files in /usr/bin/ on sda from there.

---

### Post by epswinde on 2009-02-26
Honestly, the reason I included such ominous statements is because I didn't have the desire to go through the nuts and bolts of it if you weren't interested.  This isn't that hard, it can just be confusing, especially if you're like me and tend to do things like this late at night.

Since you're interested, i'll elaborate:

First, some assumptions.  I'm assuming the new device you want to use is called /dev/sdb1, and it is formatted as ext3.  I am also assuming that /media/Ubuntu_2 is empty.  If it's not, empty it; or else you'll have personal files stored in a system folder -- bad idea.

```
cd /usr/bin && sudo cp -a * /media/Ubuntu_2/
```

Double check that there contents of /usr/bin are in /media/Ubuntu_2.  There should not be another folder, these files must be in the top level of /media/Ubuntu_2

to check
```
cd /media/Ubuntu_2
```
```
ls
```
The result of ls should be a list of files, not a single folder.

then, the tricky bit is editing fstab.
since the device /dev/sdb1 is mounted at /media/Ubuntu_2, you will need to change the mount point.  Do this by changing  the line
```
UUID=### /media/Ubuntu_2 defaults 0 1 
```
to
```
UUID=### /usr/bin relatime,errors=remount-ro 0 1 
```
or something with similar options.  the important bit is the mount point, /usr/bin

This is where it gets confusing.  You're going to have two identical folders -- to tell them apart make a new file in /media/Ubuntu_2
```
echo "congratulations!" > /media/Ubuntu_2/zztest
```

Then, have a mount for yourself. I didn't know that you could mount things to a non-empty file, i seem to remember getting angry warnings for even thinking about it. But, I just tried it and it does indeed work, so huzzahs are in order.

```
sudo umount /dev/sdb1 && sudo mount -t ext3 /dev/sdb1 /usr/bin 
```

then cd to /usr/bin, ls and look for the file you created.  this will confirm that everything you've done thusfar is ok.  Once this is done, unmount your /dev/sdb1.  

```
sudo umount /dev/sdb1
```

Once you've got everything working right up to this point, time to free some space up.

```
sudo cd /usr/bin && sudo rm *
``` 
then do an ls to make sure that the directory is empty.

then,
```
sudo umount /dev/sdb1 && sudo mount -a
``` 
mount -a will attempt to remount everything in your /etc/fstab.  expect some warnings concerning /dev/sda1 and whatever other drives you have.  to check that it worked right, cd to /usr/bin, and see if anything's there.

if the mount -a doesn't work, then you've got something funny with your /etc/fstab.  but make sure you mount your new /usr/bin so that you'll have the programs to work with.
```
sudo mount -t ext3 /dev/sdb1 /usr/bin
```

and try and figure out what's gone awry.

I think that's about it.  Let us know how it went!

---

### Post by FredRW on 2009-02-27
epswinde,


I can't thank you enough! To find someone willing to take the time to explain things is a real daymaker! I've taken to Ubuntu, and am trying to get my daughters and some other younger family members interseted (mostly to take advantage of the many educational games and programs available for children) but like most folks, they are not interested in the mechanics, just the results. So I am trying my best to learn in order to keep them happy and functional with Ubuntu... I may be an "old dog" but I'm still trying!

I won't have time to try the transfer process until tommorow or perhaps Monday, but I'll make sure to post how it went.

1 further question... if I were to partition sdb into sdb1, sdb2,would the same process work for moving /user/lib? /user/lib contains many folders instead of just files, so I am wondering about ill-effects. 

Everything on my Ubuntu mnachine is virtual so I can easily go back from back-up, but I hate wasting time stupidly...

---

### Post by geirha on 2009-02-27
Yes, but you might as well just move the entire /usr directory to another partition. On my laptop I've got the system folders split into three partitions. 2GiB partition for /, a 6 GiB partition for /usr (starting to get full though), and the rest for /home ...

---

### Post by FredRW on 2009-02-27
geirha,

I've been thinking about this option too.

Would I just follow the same commands substituting /usr for usr/bin?

Thank you for your kind reply!

---

### Post by blueridgedog on 2009-02-27
I would use rsync for the copy to keep user and group values:

rsync -a /usr/bin /media/Ubuntu_2/

---

### Post by geirha on 2009-02-27
> **blueridgedog said:**
> I would use rsync for the copy to keep user and group values:

rsync -a /usr/bin /media/Ubuntu_2/

Ah yes, I failed to spot that. Using cp without any arguments will not copy the permissions and ownership. Either that rsync command or adding the -a option to the cp command should preserve ownership and permissions.

---

### Post by epswinde on 2009-02-28
right.  rsync is a another option.  now that you mention it, i had some permissions issues when i used cp to do what i had said before.  good call.  definitely run this with cp -a, if not rsync.

and yes, you can just substitute /usr for /usr/bin.  as long as you have the space, of course. 

in fact, I first tried this by moving my /home to a separate partition, but it is general, so it will work with any folder.

---

### Post by FredRW on 2009-03-02
Just another question--

I got to the point where I should unmount sdb1 "sudo umount /dev/sdb1" and I receive an error that "the device is busy" (or similar) and the unmount fails.

I haven't had time to go in and re-do things but on a restart I find that the "new" /usr is in place (I see the test file).

Since everthing seems to be working as planned, my plan is to re-edit fstab so I return to the original /usr, restart, then edit it back.
After this, in order to clear the original /usr I believe that I have to use rm -r on each subdirectory in order to remove it and get the space back. On restart sdb1 should be mounted, and I'll be using thye newly placed /usr. 

Is this correct, or should I do something else?

---

### Post by FredRW on 2009-03-03
A final thanks to all of you for your help!
I have finished up and all seems well!

New /usr is in use from sdb1 and I now show the additional free space on sda.

I do have a final question if anyone is still following--

When I run the "disk usage analyzer" it shows /usr at 67.9 %, what is the significance of this? In file manager /usr contains 11 items (2.8 GB) freespace 6.4 GB.

---

### Post by geirha on 2009-03-03
Don't know. Did you rescan? What does ```
df -h
``` say?

---

### Post by FredRW on 2009-03-04
Thanks for additional code advice!

Very interesting outcome...
 
I should note that sdb1 is a vmware vmdk expanding scsi disk to 10gb, 1 partition,ext3- via gparted.

df -h shows dev sdb1 mounted on /usr 3.1g used 6.4g available -- use % 33%

Disk Usage Analyzer shows /usr size 2.8gb, used 67.3%-- it also shows / as size 4.2gb used 100%

I am thinking that the disk usage analyzer is being fooled by the vmware vmdk disks which are expanding.

Windows (host) shows sbd1 as being 3,502,784kb.

===

Through all of your help, I can now say that I have managed to progress from a limited Ubuntu vmware browser appliance, to a full (but space limited) Intrepid Ibex appliance (thanks to visoracle.com),to an appliance that currently has 3 scsi disks and greatly expanded learning and using capabilities.

=====

Thanks again, I'm sure you'll hear from me again, I'm just getting started!

---

