---
title: "Eliminating dual boot and reformatting previous Windows Drive"
date: 2009-09-16
forum: New to Ubuntu
---

### Post by DWL52 on 2009-09-16
Hello all. I switched to Ubuntu 9.04 about a month ago from Vista :smile:, and need a little help. Linux is on a 60 gig drive and works fine. However, there are still a few files I can't get rid of on  the previous Windows drive, which is a 500 gig. What I need help with is to reformat or repartition the 500 gig drive and eliminate the dual boot screen at start up without disturbing anything on the Linux drive. Any and all help is greatly appreciated.

Thank you all,
Dave

---

### Post by AndyCee on 2009-09-16
No problem.

1)** To remove the windows partition**

install gparted by typing:
```
sudo apt-get install gparted
```
in a terminal, or look for it in System -> Administration -> Synaptic

Open GParted in System->Administration->Partition Editor. You will see a graphical representation of your drive. Windows will be installed on ntfs or fat32. You can simply right-click on it and delete it. Make sure you understand what's going on, as partitioning always has a risk of losing all data. Ask if you're not sure.

If you want to expand the ext3 partition (holding Ubuntu) to fill the gap, you'll have to open GParted from a liveCD.

If all goes well GRUB shouldn't be affected.

2) **To remove entries in GRUB**

Back up /boot/grub/menu.lst and open it with your favourite text editor. Remove the windows bit near the bottom. Mine looks like this:

title Windows 7 Release Candidate (Loader)
root (hd0,3)
savedefault
makeactive
chainloader +1

Simply delete that, save the file and reboot. If it fails, follow [these ]("http://ubuntuforums.org/showthread.php?t=224351")instructions to fix grub. If it works, you can hide the menu entirely by replacing the line

#hiddenmenu

with

hiddenmenu

(ie. remove the hash)

Does that help? Let us know how you go or if you have any questions.

---

### Post by DWL52 on 2009-09-16
Andy, thanks ever so much! Your instructions worked like a charm. I am now FREE of 
Windows altogether! Now I have another question. When I boot, I get a 10-second timer,  like I did when the dual boot was installed, that says something about grub will be started in  X seconds. How can I eliminate that and just have it load? 

Thanks,
Dave

---

### Post by DWL52 on 2009-09-16
Andy, one more question. Now that I have the 500 gig drive repartitioned and reformatted, I can't put anything on it or take anything off unless I am logged in as root. When I right click on the drive icon, click on Properties, then on Permissions, it says "the  permissions of sda1 could not be determined" How do I change permissions so I can use it without being logged in as root?

Thanks,
Dave

---

### Post by AndyCee on 2009-09-17
> **DWL52 said:**
> Andy, thanks ever so much! Your instructions worked like a charm. I am now FREE of 
Windows altogether! Now I have another question. When I boot, I get a 10-second timer,  like I did when the dual boot was installed, that says something about grub will be started in  X seconds. How can I eliminate that and just have it load? 

Thanks,
Dave

Have a look in /boot/grub/menu.lst for the number 10, and replace it with the time you'd like. I think it's this bit:

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

to

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		0

---

### Post by AndyCee on 2009-09-17
> **DWL52 said:**
> Andy, one more question. Now that I have the 500 gig drive repartitioned and reformatted, I can't put anything on it or take anything off unless I am logged in as root. When I right click on the drive icon, click on Properties, then on Permissions, it says "the  permissions of sda1 could not be determined" How do I change permissions so I can use it without being logged in as root?

Thanks,
Dave

I can think of a few ways. Do you want to keep it as a seperate partition or extend the Ubuntu one into that space?

Can you open a terminal and type:

```
sudo fdisk -l
```

and paste the output?

---

### Post by muteXe on 2009-09-17
> **DWL52 said:**
> Andy, one more question. Now that I have the 500 gig drive repartitioned and reformatted, I can't put anything on it or take anything off unless I am logged in as root. When I right click on the drive icon, click on Properties, then on Permissions, it says "the  permissions of sda1 could not be determined" How do I change permissions so I can use it without being logged in as root?

Thanks,
Dave

You could mount that partition in your home folder. But you might not want to do that if there's other users on your machine wanting that partition too.

---

### Post by DWL52 on 2009-09-17
Andy,  the output of "sudo fdisk -l" is:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x617fe23a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60801   488384001   83  Linux

Disk /dev/sdb: 61.4 GB, 61471162368 bytes
255 heads, 63 sectors/track, 7473 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x434bbe61

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        7163    57536766   83  Linux
/dev/sdb2            7164        7473     2490075    5  Extended
/dev/sdb5            7164        7473     2490043+  82  Linux swap / Solaris

Thanks, 
Dave

---

### Post by DWL52 on 2009-09-17
No, I'm the only user on this machine, and it is not on a network.

Thanks, 
Dave

---

### Post by muteXe on 2009-09-17
Then (i think) if you mount it in your home folder, rather than /media say, you shouldnt have any permission problems.

---

### Post by DWL52 on 2009-09-17
> **muteXe said:**
> Then (i think) if you mount it in your home folder, rather than /media say, you shouldnt have any permission problems.

I tried going into the home folder to do as you said, but couldn't fine any folder or file that gave any indication of being able to mount a drive. One other problem: When I click on the 500 Gig icon to mount it, (not in the home folder, just is Places), I get the message "Unable to Mount volume". When I click on the details, it says "cannot get volume.fstype.alternative". If I go into  root mode, I do not have this problem, which makes me think it's a permission problem. Can you shed any light on  this for a newbie?

Thanks.

---

### Post by DWL52 on 2009-09-17
Well, the process continues, but may be a little simpler. Further info. When I log in as root, go into media folder, accesss the 500 gig drive, change the permissions to myself, and do the same in the /dev/ folder with the sda and sda1 files. then log out and back in as myself, everything works fine. However, when I reboot the computer, everything goes back to the way it wass before. How can I keep the permissions when I reboot?

Thanks,
Dave

---

### Post by cjv8888 on 2009-09-17
> **DWL52 said:**
> I tried going into the home folder to do as you said, but couldn't fine any folder or file that gave any indication of being able to mount a drive. One other problem: When I click on the 500 Gig icon to mount it, (not in the home folder, just is Places), I get the message "Unable to Mount volume". When I click on the details, it says "cannot get volume.fstype.alternative". If I go into  root mode, I do not have this problem, which makes me think it's a permission problem. Can you shed any light on  this for a newbie?

Thanks.

Try the following:

First create a mount point
```
sudo mkdir /media/sda
```

Then mount the drive
```
sudo mount /dev/sda /media/sda
```

Then change owner to yourself
```
sudo chown -R username: /media/sda
```

Now you should be able to mount it without being root

---

### Post by DWL52 on 2009-09-17
I tried to follow your instructions, but when I tried to mount the drive, I got the message that I must specify the filesystem type. ???

Thanks,
Dave

---

### Post by DWL52 on 2009-09-17
Another thing that puzzles me, and may shed some light on the problem. When I'm logged in as myself, and I go into /media/, the 500 gig drive is not shown in that folder, but it is when I'm logged in as root. 
Any ideas?

Thanks,
Dave

---

### Post by cjv8888 on 2009-09-17
try

```
sudo mount -t ext3 /dev/sda /media/sda
```

assuming that you have formatted the drive to ext3

---

### Post by cjv8888 on 2009-09-17
> **DWL52 said:**
> Another thing that puzzles me, and may shed some light on the problem. When I'm logged in as myself, and I go into /media/, the 500 gig drive is not shown in that folder, but it is when I'm logged in as root. 
Any ideas?

Thanks,
Dave

That is probably because when you are logged in as yourself, the drive is unmounted.  The drive is owned by root so it shows up when you logged in as root.

---

### Post by garyed on 2009-09-17
I have a question also.
Wouldn't it be better to mount the drive in fstab so it mounts automatically every time at boot up?

---

### Post by DWL52 on 2009-09-17
I tried your suggestion and got the following error:

mount: wrong fs type, bad option, bad superblock on /dev/sda,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Any Ideas how to resolve this? Also, another thing is that when I unmount the volume to try cxvj8888's suggestion, the 500 gig icon disappears from the media folder.

Thanks, 
Dave

---

### Post by DWL52 on 2009-09-17
> **garyed said:**
> I have a question also.
Wouldn't it be better to mount the drive in fstab so it mounts automatically every time at boot up?


Gary, that's ultimately what I want to do, if you can help accomplish it. Another thing that I've done is log in as root, set the permissions for the sda and sda1 files in /dev/ to myself, as well as the 500 gig icon in /media/.

---

### Post by DWL52 on 2009-09-17
I've changed ownership to myself, I've changed permissions to myself, and as long as I go into root and mount the drive, then log out and back in as myself, everything is fine, as long as I don't unmount the drive, or reboot the computer. If I do then everything goes back to this: I go into Places, click on the 500 Gig icon to mount it, and I get the message "Unable to Mount volume". When I click on the details, it says "cannot get volume.fstype.alternative". Does anyone have a solution before I pull out what little hair I have>

Thanks,
Dave

---

### Post by garyed on 2009-09-17
> **DWL52 said:**
> Gary, that's ultimately what I want to do, if you can help accomplish it. Another thing that I've done is log in as root, set the permissions for the sda and sda1 files in /dev/ to myself, as well as the 500 gig icon in /media/.
I'm sorry but i haven't a clue.
I was watching this thread & just wondering why fstab wasn't mentioned.
I guess until you can manually mount the drive you won't be able to do it in fstab.

---

### Post by DWL52 on 2009-09-17
> **garyed said:**
> I'm sorry but i haven't a clue.
I was watching this thread & just wondering why fstab wasn't mentioned.
I guess until you can manually mount the drive you won't be able to do it in fstab.

OK Gary, I guess it all goes back to the file system type not being recognized. But when I reformated and repartitioned the drive, I formated it in the ext3 type. Should I have formatted it in something different? I used GParted Partition Manager.

---

### Post by DWL52 on 2009-09-17
OK, maybe this newbie is missing something,  and if so, someone please enlighten me. I just went into a root terminal, changed ownership of a couple of files, specifically /dev/sda and /dev/sda1, to myself, then rebooted the computer, and pulled those files back up and the ownership is back to root.  I find it hard to believe that this is the way it works and I think this relates to not being able to mount the 500 gig drive without going into root. Can someone please help me und3erstand this?

---

### Post by egalvan on 2009-09-17
This is what I have in my fstab for an ext3 drive that is mounted at boot.

```

# Entry for /dev/sda5 :
UUID=0933d680-d893-40fa-a01d-3c819f0b2ea3   /   ext3   relatime,errors=remount-ro 0 1

LABEL=swap none swap sw 0 0

```

note that / is referenced by UUID, while swap is referenced by LABEL.
This is my way, as I find LABEL to be easier to read than UUID.
This machine has not been fully changed to LABEL, though.


further, bodhi. has an excellent "How-to fstab" at this post...

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

one of the points he stresses is that partitions that are not in fstab can only be mounted by root.

---

### Post by DWL52 on 2009-09-17
[quote=egalvan;7964067]This is what I have in my fstab for an ext3 drive that is mounted at boot.

```

# Entry for /dev/sda5 :
UUID=0933d680-d893-40fa-a01d-3c819f0b2ea3   /   ext3   relatime,errors=remount-ro 0 1

LABEL=swap none swap sw 0 0

```note that / is referenced by UUID, while swap is referenced by LABEL.
This is my way, as I find LABEL to be easier to read than UUID.
This machine has not been fully changed to LABEL, though.


I've done everything that everyone has suggested, and I still cant get it to work. Here is my fstab in its entirety:

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc                                       /proc          proc         defaults                    0  0  
# Entry for /dev/sdb1 :
UUID=91b7dc2a-7c12-4a66-9fcb-6f5cc8d2e1fc  /              ext3         relatime,errors=remount-ro  0  1  
# Entry for /dev/sdb5 :
UUID=2f68117e-26bb-440c-8755-b66c8a3e2150  none           swap         sw                          0  0  
/dev/hdc                                   /media/cdrom0  udf,iso9660  user,noauto,exec,utf8       0  0
# Entry for /dev/sda1 :
Label=WD500G                  /          ext3        relatime,errors=remount-ro  0  1
/dev/sda /media/sda    user,auto,exec 0  0

I don't know if this has anything to do with it, but I repartitioned and reformated the drive to the ext3 file system, rather than the NTFS sytem mentioned at the top of my fstab file. When trying to mount the drive while logged in as myself I get the error "Cannot Mount volume WD500G" Under details I get "Cannot get volume.fstype.alternative." Can someone PLEASE help me figure this out so I can use my 500 gig drive?

Thanks in advance,
Dave

---

### Post by egalvan on 2009-09-17
> **DWL52 said:**
> 
I've done everything that everyone has suggested, and I still cant get it to work. Here is my fstab in its entirety:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

# Entry for /dev/sda1 :
[COLOR="Red"]Label=WD500G [/COLOR]    /    ext3   relatime,errors=remount-ro  0  1

**/dev/sda** /media/sda    user,auto,exec 0  0

```

,I repartitioned reformated to the ext3 file system, rather than the NTFS sytem mentioned at the top of my fstab file.
 When trying to mount the drive while logged in as myself I get the error "Cannot Mount volume WD500G"
 Under details I get "Cannot get volume.fstype.alternative."
 Can someone PLEASE help me figure this out so I can use my 500 gig drive?
Dave

OK,  a few of observations...

is the label of the drive  WD500G  ?

post the output of

```
sudo blkid
```

to let us see...

Next you are referencing the drive twice, it seems...
once with[COLOR="Red"] LABEL=WD500G[/COLOR]
once with **/dev/sda**

also, you quoted my example... so you are mounting the drive at "/", or the root... not correct.

next, are you sure the drive is not mounted?

run Disk Partitioner (gparted) (System -> Administration) and check on whether it sees that drive or not.
It should show up. Does it show a mount point?

if not, this is good, so you can try the following...

for now, comment out the two lines I quoted above...
add a # at the beginning of the lines, this effectively erases them.

Then...

CHOOSE ONE ONLY, ONLY ONE EXAMPLE, PLEASE NOT BOTH !
[COLOR="black"]red color[/COLOR] high-lights the difference


==============================================================
IF YOU WANT THE DRIVE TO SHOW ON THE DESKTOP THEN USE THIS ONE

edit fstab 
```
sudo etc/fstab
```
 and add this line below the ones you commented out...

```
LABEL=data_drive	[COLOR="black"]/media[/COLOR]/WD500G	ext3	relatime	0	2

```

then type these in a terminal

```
sudo mkdir [COLOR="black"]/media[/COLOR]/WD500G
sudo mount -a
```

go to Places -> Computer -> File System
and open the 'media' folder...

the drive SHOULD show as WD500G

and their SHOULD be an icon on your desktop.

if not, reboot.

if STILL not, then scream and shout, and run about.


=====================================================================
IF YOU DO NOT WANT THE DRIVE TO SHOW ON THE DESKTOP THEN USE THIS ONE

edit fstab 
```
sudo etc/fstab
```
 and add this line below the ones you commented out...


```
LABEL=WD500G	[COLOR="Red"]/mnt[/COLOR]/WD500G	ext3	relatime	0	2

```

then type these in a terminal

```
sudo mkdir [COLOR="Red"]/mnt[/COLOR]/WD500G
sudo mount -a
```

go to Places -> Computer -> File System
and open the '[COLOR="Red"]mnt[/COLOR]' folder...

the drive SHOULD show as WD500G

and their SHOULD NOT be an icon on your desktop.

if not, reboot.

if still not correct, then scream and shout, and run about.
===================================================================

AND, I'm out of ideas...

except, if the drive is empty, then nuke it from orbit to be sure,
using dban (Darik's Boot And Nuke)...
NOTE... THIS IS DANGEROUS TO YOUR DATA...
IT WILL WIPE DRIVES...
IT IS BEST TO DISCONNECT DRIVES ON WHICH YOU WANT TO CONSERVE THE DATA.

Then using gparted, recreate the partition and format.

and try again.

and I'm *really* out ideas...

where's Bohdi. when you need him?

---

