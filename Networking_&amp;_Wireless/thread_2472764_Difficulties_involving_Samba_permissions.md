---
title: "Difficulties involving Samba permissions"
date: 2022-03-11
forum: Networking &amp; Wireless
---

### Post by username2758 on 2022-03-11
Hi,

So I've been trying to learn a bit more about Samba and came up with a problem regarding permissions.

Currently I have like 3 folders shared on my home network:
[B]
- Media (Public)
- Downloads (Private)
- Documents (Private)[/B]

The folder I'm interested in is the 'Media' folder which is public on my home network. It currently has "rwx" permissions for the "others" group.

The smb.conf file for the 'Media' folder is the following:> [Media]
    comment = Public Folder
    path = /mnt/30119cff-db69-46b4-81c4-5k3fa93a6822/Media
    read only = yes
    public = yes
    writable = yes
    browseable = yesRight now I can list and access files of the 'Media' folder without any login credentials (or as anonymous user), but for some reason can't create nor modify files within such public folder. I can only create and modify files in the public folder if I login using the owner credentials of that folder (which means not as user anonymous anymore).

Why is that happening?

---

### Post by TheFu on 2022-03-11
```
read only = yes
```
Remove that line.
Restart the smb process/daemon/service/whatever the kids are calling it today.

_read only_ means - ..... read only.  No write. No modify.  No change.  No delete.
See if that fixes it.

May also need to enable guest accounts. I'm unfamiliar with the 'public' statement, perhaps that does the same thing?  The manpage to my rescue:
```
       public
           This parameter is a synonym for guest ok.
```
Learn something new every day.

---

### Post by username2758 on 2022-03-12
Thanks. But I still couldn't get the folder 'Media' to be modified or written by others group.

I have tried changing "read only = no", tried "guest ok = yes" with and without "public = yes", tried adding write permission to others group for the entire drive (rwx for /mnt/30119cff-db69-46b4-81c4-5k3fa93a6822/). Nothing works.

 Anything else left to try? :roll:

---

### Post by TheFu on 2022-03-12
Well, /mnt/30119cff-db69-46b4-81c4-5k3fa93a6822/ looks like a native Linux mount ... that some GUI tool setup.  Have you considered placing that mount under your full control and into a better location, like /media/data/?  Are the permissions on the mounted storage (as seen locally) working with read-write?  A file system with issues will often be mounted by the OS as read-only. Once mounted read-only, nothing ... NOTHING ... can write there ... until that mount to fixed and read-write.
This output would be helpful:
```
ls -la /mnt/30119cff-db69-46b4-81c4-5k3fa93a6822
```
But I'm just guessing.

I don't allow mounts with UUIDs in the name.

---

### Post by username2758 on 2022-03-12
Thanks again, but what do you want to see from "ls -la /mnt/30119cff-db69-46b4-81c4-5k3fa93a6822" command? It's going to list my files on here.
[quote="TheFu"]Have you considered placing that mount under your full control and into a  better location, like /media/data/?  Are the permissions on the mounted  storage (as seen locally) working with read-write?  A file system with  issues will often be mounted by the OS as read-only. Once mounted  read-only, nothing ... NOTHING ... can write there ... until that mount  to fixed and read-write.[/quote]

I am not very experienced with this. How do I permanently mount the partition at /media/data location? What are the advantages to this?

Yes, the permissions on the mounted storage (seen locally) are working with read-write permissions, or at least when I'm using the server logged in as my user credentials, I can read and write the folders and files on that partition/drive no problem (if that's what you mean).

The interesting fact is I couldn't access anything in that partition (/mnt/30119cff-db69-46b4-81c4-5k3fa93a6822/) using other computers on my home network until I changed the permissions of such partition using the chmod command (can't remember exactly but I think it was "chmod o+r /mnt/30119cff-db69-46b4-81c4-5k3fa93a6822/"). Before using chmod the partition was set to '---' for others group and nothing worked on my home network. Now the partition is set to rwx.

I'm wondering if the partition is set to rwx for others group, it should be able to be modified by others on the home network, right? I don't know it doesn't make sense apparently.

---

### Post by Morbius1 on 2022-03-12
>  Thanks again, but what do you want to see from "ls -la /mnt/30119cff-db69-46b4-81c4-5k3fa93a6822" command? It's going to list my files on here.
What it will show TheFu is the exact permissions of /mnt, /mnt/30119cff-db69-46b4-81c4-5k3fa93a6822, and everything under /mnt/30119cff-db69-46b4-81c4-5k3fa93a6822 - specifically the /mnt/30119cff-db69-46b4-81c4-5k3fa93a6822/Media folder.

The Linux filesystem is hierarchical. If you block the ability of the "guest" user to at least traverse the parent folders leading up to the shared folder you block that user from accessing it - regardless of the permissions on /Media itself.

---

### Post by SeijiSensei on 2022-03-12
[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

---

### Post by TheFu on 2022-03-12
I don't really care what the filenames or subdirectory names are and only a few of each are needed if the permissions are different.
Owner, group, permissions are critical, though less so with Samba access since samba runs as root and ignores most POSIX permissions (but not all, methinks).

But Morbius1 knows samba much better than I, so if he says to check something else, please do.
SeijiSensei answered the mount question.  There are lots and lots of examples for how to mount storage in these forums using the fstab. Please search and find those answers.  

Mounting local storage and mounting remote storage can both happen in the fstab and I consider it the best method for storage connected via SATA or NVMe or eSATA.  

Network storage or USB storage, I prefer to use autofs, but lots of people use the fstab for those types too. For troubleshooting, the fstab is probably the best answer for playing with storage mount options. As you may guess, there are many opinions about how best to mount things.

---

### Post by username2758 on 2022-03-13
Okay. I only asked because of privacy, and I admit not being very good with Linux especially when it comes to networking and permissions so my apologies.

Here is the result:```
ubuntu64@m75q:/mnt/30119cff-db69-46b4-81c4-5k3fa93a6822$ ls -la
total 2580
drwx---rwx 8 ubuntu64 ubuntu64   4096 mar  9 16:17  .
drwxr-xr-x 4 root     root       4096 jan 16 17:24  ..
-rw------- 1 ubuntu64 ubuntu64 811149 mar  9 16:17  bookmarks_3_9_22.html
-rw------- 1 ubuntu64 ubuntu64 234994 jan 15 11:26  chrome-bookmarks_1_15_22.html
drwx---r-x 3 ubuntu64 ubuntu64   4096 fev 21 17:20 '[Documents]'
drwx---r-x 5 ubuntu64 ubuntu64   4096 mar  9 09:36 '[Downloads]'
drwx---r-x 2 ubuntu64 ubuntu64   4096 mar  7 16:59 '[ISOs]'
drwx---rwx 3 ubuntu64 ubuntu64   4096 mar 12 11:47 '[Media]'
drwx---r-x 3 ubuntu64 ubuntu64   4096 fev 20 15:49 '[VMs]'
```I have taken the liberty of omitting individuals files on here for privacy concerns. If you still need to check that, please let me know.
[quote="TheFu"]Mounting local storage and mounting remote storage can both happen in  the fstab and I consider it the best method for storage connected via  SATA or NVMe or eSATA.[/quote]

What I did was I used the 'Disks' utility in Ubuntu and had the 30119cff-db69-46b4-81c4-5k3fa93a6822 partition/drive to 'Mount at system startup'. It's easier that way, but not sure if it's the best way.

I will look into the suggested mounting page!

Thanks!

---

### Post by TheFu on 2022-03-13
Looking at
```
drwx---r-x 5 ubuntu64 ubuntu64   4096 mar  9 09:36 '[Downloads]'
```
Those are extremely odd permissions and you will always be hassled about the directory name because it has characters that have special meaning to Unix. 

I'd change the permissions to be 755(rwxr-xr-x) on all the directories too.  Since the owner and group are dedicated to a single user, the permissions don't really matter, but it is odd - damn odd - to see 705 (rwx---r-x) permissions.  A refresher about Unix permissions wouldn't hurt.  Typically, the group would have either the same permissions as 'other' or as the owner does.

About 'other' .... it was called 'world', as in world-readable, in my Unix classes long ago, but really that is incorrect. 'other' means anyone not the owner or a member of the groupid. So, what the permissions of 705 provide is
[LIST]
[*]owner - full read, write, and execute
[*]group - no access at all
[*]other - read and execute, no write.
[/LIST]
So, anyone in the group cannot access the directory, which really isn't what you want.  The only thing that allows the username, ubuntu64, to still work is because it is the owner.  Damn odd.  I've used this type of setup only a few times over the decades and only as a joke against a co-worker, by making the group on a file/directory be set to their personal group, but let everyone else have access because they were in the 'other'.

Best to change the name to "Downloads" - that will simplify your life a bunch. Using characters that are special to Unix in file or directory names is just a bad idea.  Sure, it is possible, but that doesn't make it smart.  It will probably find bugs in code. That's great if you want to find bugs, but terrible if you just want things to work.  Don't use and of these characters in filenames (directories are just files too, BTW): !@#$%^&*()+=[]{};':"<>?/\|   - I think that's all the characters to be avoided.  If you want to have scripts be able to get passed in a list of filenames and work on each, then avoid {spaces} too. A {space} is a natural separator and most scripting languages will split inputs automatically at a space.  Use_an_underscore rather than a {space} in filenames, if you'd like this ability to be easy.  None of this limited naming is strictly required, but it will make life 1000x easier.

Disks isn't how I handle mounts. Too limiting.  I think for ext4, it does add a line to the /etc/fstab file, which is good. Please check that. To change where it gets mounted in the fstab, just change the mount-point name.  I think systemd-mount will create the directory you specify, if it doesn't exist. In the old days, we had to ensure the directory for the mount-point pre-existed or it would refuse to mount, so if it fails to mount, just create the directory and run **sudo mount -a**. That's a 1-time thing.  If you post the relevant fstab line, I'm happen to recommend changes. For ext4 file systems, there are only a few non-default options to consider.

---

### Post by username2758 on 2022-03-13
> **TheFu said:**
> Looking at
```
drwx---r-x 5 ubuntu64 ubuntu64   4096 mar  9 09:36 '[Downloads]'
```
Those are extremely odd permissions and you will always be hassled about the directory name because it has characters that have special meaning to Unix. 

I'd change the permissions to be 755(rwxr-xr-x) on all the directories too.  Since the owner and group are dedicated to a single user, the permissions don't really matter, but it is odd - damn odd - to see 705 (rwx---r-x) permissions.  A refresher about Unix permissions wouldn't hurt.  Typically, the group would have either the same permissions as 'other' or as the owner does.

About 'other' .... it was called 'world', as in world-readable, in my Unix classes long ago, but really that is incorrect. 'other' means anyone not the owner or a member of the groupid. So, what the permissions of 705 provide is
[LIST]
[*]owner - full read, write, and execute 
[*]group - no access at all 
[*]other - read and execute, no write. 
[/LIST]
So, anyone in the group cannot access the directory, which really isn't what you want.  The only thing that allows the username, ubuntu64, to still work is because it is the owner.  Damn odd.  I've used this type of setup only a few times over the decades and only as a joke against a co-worker, by making the group on a file/directory be set to their personal group, but let everyone else have access because they were in the 'other'.

Best to change the name to "Downloads" - that will simplify your life a bunch. Using characters that are special to Unix in file or directory names is just a bad idea.  Sure, it is possible, but that doesn't make it smart.  It will probably find bugs in code. That's great if you want to find bugs, but terrible if you just want things to work.  Don't use and of these characters in filenames (directories are just files too, BTW): !@#$%^&*()+=[]{};':"<>?/\|   - I think that's all the characters to be avoided.  If you want to have scripts be able to get passed in a list of filenames and work on each, then avoid {spaces} too. A {space} is a natural separator and most scripting languages will split inputs automatically at a space.  Use_an_underscore rather than a {space} in filenames, if you'd like this ability to be easy.  None of this limited naming is strictly required, but it will make life 1000x easier.

Disks isn't how I handle mounts. Too limiting.  I think for ext4, it does add a line to the /etc/fstab file, which is good. Please check that. To change where it gets mounted in the fstab, just change the mount-point name.  I think systemd-mount will create the directory you specify, if it doesn't exist. In the old days, we had to ensure the directory for the mount-point pre-existed or it would refuse to mount, so if it fails to mount, just create the directory and run **sudo mount -a**. That's a 1-time thing.  If you post the relevant fstab line, I'm happen to recommend changes. For ext4 file systems, there are only a few non-default options to consider.

Thank you for all the tips and information! I am really new to Linux permissions, so I don't know what I'm doing most of the time (but am trying to learn).

In fact I don't know who or what set those permissions that way (705 or rwx---r-x). All I did was create the folders and then experiment a bit with folder "[Media]" to try and understand Samba and permissions (Public Vs. Private folders), but never changed permissions of any other folder in this partition.

Here is my fstab:> # /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/nvme0n1p6 during installation
UUID=352ae185-8265-4e68-a891-2b0c9a3448e3 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/nvme0n1p1 during installation
UUID=8ADA-6DE7  /boot/efi       vfat    umask=0077      0       1
# /swapfile                                 none            swap    sw              0       0
/dev/disk/by-uuid/30119cff-db69-46b4-81c4-5k3fa93a6822 /mnt/30119cff-db69-46b4-81c4-5k3fa93a6822 auto nosuid,nodev,nofail,x-gvfs-show 0 0I'm still not certain why mounting the partition at /media/ location would be better than at /mnt/. If you would clarify that I'd much appreciate it.

---

### Post by TheFu on 2022-03-13
> **username2758 said:**
>  I'm still not certain why mounting the partition at /media/ location would be better than at /mnt/. If you would clarify that I'd much appreciate it.

Standards.  Simple as that.  There is a document - **Linux File System Hierarchy Standards** that can be easily found which all the popular Linux distros follow - in theory.  2015 was the last update. There is a wikipedia article.

/mnt/ is for temporary mounts that an admin would use in preparing storage to be used. It is not for permanent mounts.
/media/ is for sometimes connected storage like CD/DVD media.

```
 /dev/disk/by-uuid/30119cff-db69-46b4-81c4-5k3fa93a6822 /mnt/30119cff-db69-46b4-81c4-5k3fa93a6822 auto nosuid,nodev,nofail,x-gvfs-show 0 0 
```

Wow. That's just offensive. If I were the tool that created that link, I'd be embarrassed. Nothing against any user of the tool - rather the coders.
```
 UUID=30119cff-db69-46b4-81c4-5k3fa93a6822 /media/data ext4 nofail,noatime,errors=remount-ro,nosuid,nodev 0 [COLOR="#FF0000"]2[/COLOR] 
```
is what I'd start with, but then I'd add a label on the file system and use the 
```
LABEL=Whatever   /media/data ext4 nofail,noatime,errors=remount-ro,nosuid,nodev 0 [COLOR="#FF0000"]2[/COLOR] 
```
to mount it instead.  Labels are for humans.  *Shorter is better, especially when more useful information is actually provided too*. What use is the UUID or the really long path to a uuid symbolic link?  None.  Longer with more gibberish isn't better.

Look in  /dev/disk/by-label/.  **gparted** can be used to add a label on a partition which usually equates to a file system.  With ext4, there is a CLI tool **e2label** which can put a label on the file system. This can be used if a partition != file system, like it wouldn't when using LVM2.  BTRFS and ZFS have their own methods for mounting, so labels don't get used.

A UUID is mostly about being unique, not being helpful to humans.  LABELs are for humans.  And always remember that LABELs are for file systems, not partitions, nor whole disks.  

That last number at the end of the fstab line?  That's when an fsck should be run during the boot sequence.  _The fstab manpage explains_.  Setting a 0 there is wrong for any locally connected disk. Wrong. Wrong.  The Gnome "Disks" team should be ashamed to do that with any native Linux file system. For other storage - like NTFS or FAT32 an argument can be made for the 0. I'd put 0 for any non-Linux file system too.

I remove the x-gvfs-show option. That has nothing to do with any mount. It is a Gnome show-me-as-special option.  I want all storage to appear as native, local, when used, so the extra option isn't desired. Include it if you like. Personal preference.

Anyway, hope this helps.

---

### Post by Morbius1 on 2022-03-14
I'm not disagreeing with most of what TheFu posted I just have a question.

If your shared folder is at /mnt/30119cff-db69-46b4-81c4-5k3fa93a6822/[Media]:
> ubuntu64@m75q:/mnt/30119cff-db69-46b4-81c4-5k3fa93a6822$ ls -la
total 2580
drwx---rwx 8 ubuntu64 ubuntu64   4096 mar  9 16:17  .
drwxr-xr-x 4 root     root       4096 jan 16 17:24  ..
-rw------- 1 ubuntu64 ubuntu64 811149 mar  9 16:17  bookmarks_3_9_22.html
-rw------- 1 ubuntu64 ubuntu64 234994 jan 15 11:26  chrome-bookmarks_1_15_22.html
drwx---r-x 3 ubuntu64 ubuntu64   4096 fev 21 17:20 '[Documents]'
drwx---r-x 5 ubuntu64 ubuntu64   4096 mar  9 09:36 '[Downloads]'
drwx---r-x 2 ubuntu64 ubuntu64   4096 mar  7 16:59 '[ISOs]'
**[COLOR="#FF0000"]drwx---rwx 3 ubuntu64 ubuntu64   4096 mar 12 11:47 '[Media]'[/COLOR]**
drwx---r-x 3 ubuntu64 ubuntu64   4096 fev 20 15:49 '[VMs]'
Why is your samba share pointing to a folder that apparently doesn't exist:
> [Media]
comment = Public Folder
**[COLOR="#FF0000"]path = /mnt/30119cff-db69-46b4-81c4-5k3fa93a6822/Media[/COLOR]**
read only = yes
public = yes
writable = yes
browseable = yes 


---

### Post by TheFu on 2022-03-14
```
path = /mnt/30119cff-db69-46b4-81c4-5k3fa93a6822/Media
```
excellent catch!

Special characters get in the way again!

---

### Post by username2758 on 2022-03-14
> **Morbius1 said:**
> I'm not disagreeing with most of what TheFu posted I just have a question.

If your shared folder is at /mnt/30119cff-db69-46b4-81c4-5k3fa93a6822/[Media]:

Why is your samba share pointing to a folder that apparently doesn't exist:

What? Are you guys going to argue over a missing special character here... come on! :roll:

But I'm definitely sure I CTRL+C/CTRL+V the smb.conf file exactly the way it was before, not sure what happened after that (I already have enough gaslighting in my life so please).

As to the fstab config file, I'm kinda nervous because I don't want to break things on this drive, it's a data drive. Last time I remember fiddling with fstab I got a blank drive as a result.

What does the "0" and "2" parameter means anyway?

---

### Post by TheFu on 2022-03-14
> What? Are you guys going to argue over a missing special character here... come on!

Perhaps I'm missing the tone of the statement? Joke or serious?

We are agreeing. In case it was a serious statement, the directory listing shows that the path used is incorrect. It is an error.  The correct line would be 
path = "/mnt/30119cff-db69-46b4-81c4-5k3fa93a6822/[COLOR="#FF0000"][[/COLOR]Media[COLOR="#FF0000"]][/COLOR]"
_**not**_
path = /mnt/30119cff-db69-46b4-81c4-5k3fa93a6822/Media

Configuration of samba doesn't work on fuzzy, close-enough, answers.

Now, if the real smb.conf file has the brackets, then it could be a forum input issue ... another bug in some software. Another reason to avoid special characters, but the fact that the sections in the smb.conf file which also have brackets are being displayed correctly leaves me suspicious.

Nobody has requested this, but usually we would ask for the output from the **testparm -s** command on the samba server. That shows what samba is seeing in the config file, not what our human brains think it says. We are all prone to these mistakes, daily.  I make them all the time.

> What does the "0" and "2" parameter means anyway? 
The fstab manpage has a clear description for each field, including the 5th and 6th fields.

---

### Post by Morbius1 on 2022-03-14
smb.conf interprets paths as literal strings so it can accommodate spaces, [], etc ....

This will point to a folder that exists - at least according to your "ls -al" command:
> [Media]
comment = Public Folder
**[COLOR="#FF0000"]path = /mnt/30119cff-db69-46b4-81c4-5k3fa93a6822/[Media][/COLOR]**
read only = yes
public = yes
writable = yes
browseable = yes 
The way you have it now it will point to a folder that does not exist:
> [Media]
comment = Public Folder
**[COLOR="#FF0000"]path = /mnt/30119cff-db69-46b4-81c4-5k3fa93a6822/Media[/COLOR]**
read only = yes
public = yes
writable = yes
browseable = yes 

In Linux [Media] and Media are two different things just like Media and media would be two different things.

The perplexing thing about your post is that you claim to have only read access unless you pass credentials. You should have no access regardless of who accesses the share since the folder in the path does not exist.

---

### Post by deadflowr on 2022-03-14
> What does the "0" and "2" parameter means anyway?
If you mean the fstab the first number 0 is for dump settings of the file systems,
if you don't understand or use dump then it means nothing and the 0 sets it to off.

The second refers to the priorities of running file system checks on the listed partitions,
Primary file systems are to be set to 1 with all secondary file systems set to 2 or 0.
0 in this case is the same as the dump setting of 0, meaning it sets it to off.

Here are the basics of the fstab layout: [https://wiki.debian.org/fstab#Field_definitions]("https://wiki.debian.org/fstab#Field_definitions")

---

### Post by username2758 on 2022-03-14
[quote="Morbius1"]The perplexing thing about your post is that you claim to have only read  access unless you pass credentials. You should have no access  regardless of who accesses the share since the folder in the path does  not exist.[/quote]
I've already said it, I copied the smb.conf parameters the way it was at the time. Not sure what happened afterwards on this forum. May have to change password then.

[quote="deadflowr"]If you mean the fstab the first number 0 is for dump settings of the file systems,
if you don't understand or use dump then it means nothing and the 0 sets it to off.

The second refers to the priorities of running file system checks on the listed partitions,
Primary file systems are to be set to 1 with all secondary file systems set to 2 or 0.
0 in this case is the same as the dump setting of 0, meaning it sets it to off.

Here are the basics of the fstab layout: [https://wiki.debian.org/fstab#Field_definitions](https://wiki.debian.org/fstab#Field_definitions)[/quote]
Thanks for the information!

But what do you mean by primary and secondary file systems? Is it the same as calling them as primary drive and secondary drive? 

As you can see from my fstab, I have two drives on this Ubuntu machine: 1xNVMe and 1xSATA, the former being the drive containing the main OS, and the latter being the drive containing data mostly.

So does that mean the only recommended parameter to be changed in my fstab is the "0 0" to "0 2" from "*/dev/disk/by-uuid/30119cff-db69-46b4-81c4-5k3fa93a6822 /mnt/30119cff-db69-46b4-81c4-5k3fa93a6822 auto nosuid,nodev,nofail,x-gvfs-show 0 0*"?> # /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
# / was on /dev/nvme0n1p6 during installation
UUID=352ae185-8265-4e68-a891-2b0c9a3448e3 / ext4 errors=remount-ro 0 1
# /boot/efi was on /dev/nvme0n1p1 during installation
UUID=8ADA-6DE7 /boot/efi vfat umask=0077 0 1
# /swapfile none swap sw 0 0
/dev/disk/by-uuid/30119cff-db69-46b4-81c4-5k3fa93a6822 /mnt/30119cff-db69-46b4-81c4-5k3fa93a6822 auto nosuid,nodev,nofail,x-gvfs-show 0

---

### Post by Morbius1 on 2022-03-14
Please post the output of this command:
```
ls -dl /mnt/30119cff-db69-46b4-81c4-5k3fa93a6822/Media
```

---

### Post by TheFu on 2022-03-14
> **username2758 said:**
>  
But what do you mean by primary and secondary file systems? Is it the same as calling them as primary drive and secondary drive? 


Ok ... the fstab manpage for the field is this:
```
       The sixth field (fs_passno).
              This field is used by fsck(8) to determine the  order  in  which
              filesystem  checks  are  done at boot time.  The root filesystem
              should be specified with a fs_passno of  1.   Other  filesystems
              should  have  a fs_passno of 2.  Filesystems within a drive will
              be checked sequentially, but  filesystems  on  different  drives
              will  be  checked at the same time to utilize parallelism avail&#8208;
              able in the hardware.  Defaults to  zero  (don't  fsck)  if  not
              present.
```

So, you can interpret that as you like.  I interpret it as
[LIST]
[*]OS file systems should be 1.
[*]Non-OS, but always expected to be mounted local file systems should be 2.
[*]Non-local (or non-Linux) file systems should be 0.
[/LIST]

Interpret however you like. Your choice.

---

### Post by username2758 on 2022-03-14
> **Morbius1 said:**
> Please post the output of this command:
```
ls -dl /mnt/30119cff-db69-46b4-81c4-5k3fa93a6822/Media
```

I have changed both the name of the folder (removed the brackets as recommened) and folder permissions again back to r-x for "other" group.```
$ ls -dl /mnt/30119cff-db69-46b4-81c4-5k3fa93a6822/Media/
drwx---r-x 3 ubuntu64 ubuntu64 4096 mar 12 11:47 /mnt/30119cff-db69-46b4-81c4-5k3fa93a6822/Media/
```

What do you wanna see? :roll:

---

### Post by TheFu on 2022-03-14
That location isn't shown in post #9, which is why we are confused.  Scratch that. I'm confused. Don't know about others.

---

### Post by #&amp;thj^% on 2022-03-14
> **TheFu said:**
> Scratch that. I'm confused. Don't know about others.
I've been confused from Post #1 forward.
Your patience is respected and Admired. ;)

---

### Post by Morbius1 on 2022-03-14
> ls -dl /mnt/30119cff-db69-46b4-81c4-5k3fa93a6822/Media/
drwx---r-x 3 ubuntu64 ubuntu64 4096 mar 12 11:47 /mnt/30119cff-db69-46b4-81c4-5k3fa93a6822/Media/
In the interest of resolving this as quickly as possible and assuming this is still your samba share definition:
> [Media]
comment = Public Folder
path = /mnt/30119cff-db69-46b4-81c4-5k3fa93a6822/Media
read only = yes
public = yes
writable = yes
browseable = yes 
I would edit /etc/samba/smb.conf and change that share definition to this:
> [Media]
comment = Public Folder
path = /mnt/30119cff-db69-46b4-81c4-5k3fa93a6822/Media
read only = yes
public = yes
writable = yes
browseable = yes 
**[COLOR="#FF0000"]force user = ubuntu64[/COLOR]**
Then restart smbd:
```
sudo service smbd restart
```

---

### Post by username2758 on 2022-03-14
> **TheFu said:**
> That location isn't shown in post #9, which is why we are confused.  Scratch that. I'm confused. Don't know about others.

As I already said I have changed the name of the folders (removed the brackets) as per your recommendation.

@**Morbius1:**

Thanks. But what does "force user = ubuntu64" parameter exactly do?

Here is my updated smb.conf file for the specific section:```
[Media]
    comment = Public Folder
    path = /mnt/30119cff-db69-46b4-81c4-5k3fa93a6822/Media
    read only = no
    public = yes
    writable = yes
    browseable = yes
    force user = ubuntu64
```

I still haven't tried without the "read only" line though. I'mma try right now!

---

### Post by username2758 on 2022-03-14
Ooooh my god it worked!

I removed the "read only" parameter from the smb.conf file and bam it works! The "Media" folder is now accessible and modifiable by anyone on my home network!

Then I tried with and without "force user = ubuntu64" parameter, and apparently when I create and/or modify anything in that folder the owner is going to be ubuntu64 user (that right?). Before adding the "force user" parameter, the files were created without a owner and group (nouser, nogroup).

But, oh my god I can't believe this! It's working now! Thank you thank you thank you! :D ](*,) :D ](*,) :D

Just one more question though: is "sudo service smbd restart smbd" the same as "sudo systemctl restart smbd"? And do I really need to restart both the smbd and nmbd services in order for changes to be applied?

---

### Post by TheFu on 2022-03-14
Let me get this straight.  Post #2 above solved this?

---

### Post by rsteinmetz70112 on 2022-03-14
The default of read only is yes It is the inverse writable so read only = yes is the same as writable = no

To make the share writable you must use writable = yes or read only = no they both do the same thing.

Have your run testparm? It may give you warnings and errors and output the actual effective smb.conf.

---

### Post by rsteinmetz70112 on 2022-03-14
> **TheFu said:**
> Let me get this straight.  Post #2 above solved this?

OK I'm confused 

```
read only = yes 
```
Should result in a read only share.
but the last post showed ```
read only = no
```
Which should result in a writable share.
of course```
 writable = yes
```
as shown in the last post should have resulted in a writable post 
The only thing I can think of is that smbd and nmbd weren't restarted and samba was running with the old smb.conf loaded.

---

### Post by username2758 on 2022-03-14
> **TheFu said:**
> Let me get this straight.  Post #2 above solved this?

I'm not exactly sure but yes maybe... come on man I'm a noob help me here.

**@rsteinmetz70112:**

That is weird. I am not definitely sure how or what made it work, but I'm certain I was trying with both "read only = no" and "writable = yes" before and it did not work. Then I removed the "read only" parameter altogether and now I can create new files on the public folder without logging in as user ubuntu64 on my home network.

Here is the output of "testparm":```
$ testparm
Load smb config files from /etc/samba/smb.conf
lpcfg_do_global_parameter: WARNING: The "client lanman auth" option is deprecated
Loaded services file OK.
Weak crypto is allowed
Server role: ROLE_STANDALONE

Press enter to see a dump of your service definitions
```

---

### Post by TheFu on 2022-03-14
> _*Press enter to see a dump of your service definitions*_

Did you press <enter>?

Hint: Read what the output says. If something specific is there, do it.

---

### Post by username2758 on 2022-03-14
> **TheFu said:**
> Did you press <enter>?

Hint: Read what the output says. If something specific is there, do it.
Yes, I didn't. (:

---

### Post by TheFu on 2022-03-14
I give up. Good day.

---

