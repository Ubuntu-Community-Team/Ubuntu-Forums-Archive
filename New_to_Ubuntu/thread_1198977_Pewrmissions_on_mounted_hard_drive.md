---
title: "Pewrmissions on mounted hard drive"
date: 2009-06-28
forum: New to Ubuntu
---

### Post by george_b on 2009-06-28
Hi 

My PC has 3 internal hard drives that I want to use, where sdb1 is mounted as root, and I want to use the other two as data storage.

I have created a directory structure 

/data/projects
/data/music

Both of these directories were created with an owner of glen and a group of data.

I have successfully mounted sda1 on /data/music and sdd1 on /data/projects ( sdc1 is a windows drive formatted as NTFS that is mounted as a temporary measure and it holds all the data I want to transfer to the other 2 drives ) with a line like 
/dev/sda1  /data/music ext3 defaults 0 0 
in fstab for each of the drives that mounts them correctly.

However it mounts them owned by root with a group of root.

How can I mount the hards drive so they have an owner of glen ( my user name ) and a group called data ( which I have created and I am a member of )?

Thanks
Glen

---

### Post by MasterProg on 2009-06-28
Try setting uid (user id) and gid (group id) in fstab, like

/dev/sda1 /data/music ext3 defaults,uid=n,gid=n 0 0

Run *id* in console to find out what uid and gid you have.

---

### Post by george_b on 2009-06-28
Thanks for the suggestion 

I ran id in a console and my user id is 1000 and my group id is 1000.

I tried the line in fstab as you suggested (with uid=100,gid=1000) and I now get the error

mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

and the last line in dmesg is

[14686.058627] EXT3-fs: Unrecognized mount option "uid=1000" or missing value

I am now looking at the man entries for fstab and mount to see if I can spot anything

---

### Post by swisstone198 on 2009-06-28
> **MasterProg said:**
> Try setting uid (user id) and gid (group id) in fstab, like

/dev/sda1 /data/music ext3 defaults,uid=n,gid=n 0 0

Run *id* in console to find out what uid and gid you have.

Should be 

/dev/sda1 /data/music ntfs-3g defaults,uid=n,gid=n 0 0

for ntfs

---

### Post by george_b on 2009-06-28
The partition I want to mount is ext3

and according to this post

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131) (How to fstab )

uid and gid can't be used with ext2 or ext3.

Seems like I need investigate more

---

### Post by swisstone198 on 2009-06-28
Sorry, i miss-read your post, I saw ntfs and jumped straight in.

Have you tried  

sudo chown -iR userID:groupID /(filesystem)/

---

### Post by george_b on 2009-06-28
Thats OK I do that as well.

It seems that if I create the /data/music directory and change its owner/group to the appropriate values, then have a line like

/dev/sda1       /data/music ext3  users,noauto 0 0

in fstab, then it mounts and leaves the owner and permissions alone.

I'm not sure how this fits in with what you suggested, but I'll play with both.

Thanks for the help

---

