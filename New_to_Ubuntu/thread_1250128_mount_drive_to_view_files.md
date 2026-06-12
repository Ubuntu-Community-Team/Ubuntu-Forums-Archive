---
title: "mount drive to view files"
date: 2009-08-26
forum: New to Ubuntu
---

### Post by mvalenti on 2009-08-26
I have been running Ubuntu for months without much problems. I recently had some audio issues after installing ubuntu studio. I attempted to remove studia along with any audio packages via package manager. Since then, system hangs after log in, and now most recently, it tells me my session lasted less than 10 seconds....... and still nothing... I tried using xterm as a session option, message says xterm cant be found. I can get into term via ctrl-alt-f1, so i see my files. Just to use the laptop, I am running Ubuntu Live. I can mount the drive but the only files that show are recycle bin....  I would like to get the important files off before reinstalling... any help is MUCH appreciated!!!!


-Mark

---

### Post by shankhs on 2009-08-26
Do u have a dual-boot with windows . If yes then u can install some softwares which when installed in win will help you to get files from ext2/ext3 partitions.

---

### Post by tarps87 on 2009-08-26
If you are using the Ubuntu live cd the drive should be listed under places, failing that can you post the output of
```
sudo fdisk -l
```
(lowercase L)

Did you create a separate home partition?

---

### Post by mvalenti on 2009-08-26
Thanks, I do have win xp as well as vista on this machine. What software do you recommend?

---

### Post by mvalenti on 2009-08-26
I tried disk internals software... shows drive as empty.

---

### Post by mvalenti on 2009-08-26
I can see the drive under places.. It shows it as empty.... I can ctrl-alt-F1 and vterm... then see all the files on the drive.... I would like to copy all my pictures and docs to a cd... then try to grab any mail from thunderbird before I reformat....

---

### Post by tarps87 on 2009-08-26
You say that you have xp installed, could to go to the terminal when using the live cd and run the sudo fdisk -l command, then I can give you the command to mount the drives

---

### Post by mvalenti on 2009-08-26
done

---

### Post by mvalenti on 2009-08-26
sda1          hpfs/ntfs
sda2          hpfs/ntfs
sda3          w95 fat32 lba
sda4          w95 ext lba
sda5          hpfs/ntfs
sda6          linux
sda7          linux swap/solaris


I obviously left out the start end, and blocks as well as id....
I have a desktop running ubuntu also, and just got a hold of a device to connect the laptop drive to the desktop, again, it only sees the ubuntu partition and shows as empty... mounting and unmounting via the gui.....

-Mark

---

### Post by tarps87 on 2009-08-27
try:
```
sudo mkdir /media/ubuntu
sudo mount /dev/sda6 /media/ubuntu
```
if this fails
```
sudo mount -t ext3 /dev/sda6 /media/ubuntu
```
Now
```
cd /media/ubuntu
ls -A
```
You should see root, home, ...
using ls see if you can see your files

From what you have said in your original post this should work. The next step is to work out which drive to copy the files to.
The easiest may be to use
```
df -h
```
This will list the space available on each partition
```
sudo mkdir /media/back
sudo mount /dev/***deviceID*** /media/back
cp -r /media/ubuntu/home/***username*** /media/back
```

---

### Post by mvalenti on 2009-08-27
Thankyou,

The ds command was not found.. When I ran the command cp /media/ubuntu/home/mark /media/back   the return line read cp: omitting directory '/media/ubuntu/home/mark'

I can now see the files through the gui! Thanks!  I will be reformatting this drive, 320gb, I will be removing my windows completely.  I like the idea of having Home on a separate drive. Do you have a good link that I can use to get the best formatting options?


Thanks again for your help. 

-Mark

---

### Post by tarps87 on 2009-08-27
Sorry typos ds should have been df and cp should have been cp -r, I have updated my previous post.

These should help with making a separate home partition, if you have the space I would suggest 10GB for the root (/) partition.
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

Note: You can change the sizes after

---

### Post by mvalenti on 2009-08-27
Working like a charm now, Thanks!

---

