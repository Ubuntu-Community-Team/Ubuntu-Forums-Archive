---
title: "Need help"
date: 2011-01-23
forum: New to Ubuntu
---

### Post by mr.srimanth on 2011-01-23
i have downloaded ubuntu for pc..and made a DVD.. and while installing its giving an error.. some input output... couldnot be found and its asking to refer help... its much like cmd... i dont know this .. and iam using it for the first time...

---

### Post by mr.srimanth on 2011-01-23
i cant capture the exact error also as its happening while .. installation.. so help me...

---

### Post by GregBrannon on 2011-01-23
It's hard to help you without knowing the error, but I understand that it's sometimes hard to capture error messages.

It's possible that your DVD is corrupt.  Did you try running a live session from the DVD before installing?  You may still be able to try that.  If a live session won't run, you may get error messages that you can capture and/or it may indicate the DVD is not right.

There are also ways to verify the fidelity of the DVD.  Check the place where you downloaded or obtained the DVD to see if there are instructions.

---

### Post by mr.srimanth on 2011-01-23
the exact error is ..

Enter 'help' for the list of commands
(initramfs)mount:mounting/div/loop0 on//filesystem.squashfs failed:input/output error
cannot mount/dev/loop0(cdrom/casper/filesystem.reuesthts)on//filesystem squashfs

---

### Post by Elfy on 2011-01-23
Check the md5sum of the download - [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

then 

Check the dvd haas burnt ok - [https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)

---

### Post by mr.srimanth on 2011-01-23
Its giving md5sums are different... so what to do now...

---

### Post by Elfy on 2011-01-23
download it again - use a torrent rather than a direct download

[http://www.ubuntu.com/desktop/get-ubuntu/alternative-download#bt](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download#bt)

---

### Post by mr.srimanth on 2011-01-23
Thank you very much.. appreciate ur time and patience..:)

---

### Post by mr.srimanth on 2011-01-23
Hello......... I have downloaded  it again... from the torrent .. but still.. the md5sum is not matching .. what to do... 

I have been very eager to install it... since morning... and .....am very dissapointed

---

### Post by Sef on 2011-01-23
> Hello......... I have downloaded it again... from the torrent .. but still.. the md5sum is not matching .. what to do... 

I have been very eager to install it... since morning... and .....am very dissapointed

1) If you torrented it, then there is no need to md5sum, as the torrent automatically does that. 

2) If you did not torrent it, then find the md5sum from the site that you downloaded it from.

---

### Post by mr.srimanth on 2011-01-24
Thank you all for the support... i was able to install it .. however not as i wanted... as am ameture.. so ... i have my entir... hardisk as one drive.. so now i want ot partition it .. is it possible.????


please reply..................

---

### Post by Elfy on 2011-01-24
Yes it's possible, but you're going to need to give people more detail of what it is you want to achieve.

For the record - the drive will have partitions already :)

Run this from a terminal and it will tell you what you have

```
sudo fdisk -l
```

---

### Post by mr.srimanth on 2011-01-24
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9360    75182080   83  Linux
/dev/sda2            9360        9730     2966529    5  Extended
/dev/sda5            9360        9730     2966528   82  Linux swap / Solaris


i dont know what i means.. i want to keep my files .. separately as i do with windows

---

### Post by mr.srimanth on 2011-01-24
and i have one more question .. i guess i have downloaded ubuntu.. 32bit.. however not sure abt it... how to reconfirm it??

---

### Post by Elfy on 2011-01-24
> **mr.srimanth said:**
> Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9360    75182080   83  Linux
/dev/sda2            9360        9730     2966529    5  Extended
/dev/sda5            9360        9730     2966528   82  Linux swap / Solaris


i dont know what i means.. i want to keep my files .. separately as i do with windows

Ok - firstly you currently have 1 primary (sda1), 1 extended (sda2) and a logical partition (sda5).

You can have 4 primaries - that can include 1 extended. 

Linux does not number drives and partitions as windows does.

the a in sda means it's the first drive, sdb would be the second, sdc the third ..

the 1 is the first partition - now here 1 -4 means it is a primary, 5 is the first logical partition.

So the first logical partition on a second drive would be sdb5.

Hope that helps that a bit.

Now as to your needs - to do that you will first need to shrink the sda1 partition in order to have free space to create a partition with.

IF you want to create another primary then you can do so after resizing the first.

If you want a logical you would first need to increase the extended partition - think of the extended as a box to put logicals in.

---

