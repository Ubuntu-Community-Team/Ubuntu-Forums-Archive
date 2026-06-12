---
title: "Unable to Resize Partition"
date: 2009-05-14
forum: New to Ubuntu
---

### Post by Coh3n on 2009-05-14
I need to expand my ubuntu partition.  It's called /dev/sda5 and it says both the max. and min. size is 2.32 GiB.  I can't make it any larger, even though I have over 20 GiB of unused space.  

How do I allocate that 20 GiB to sda5?

---

### Post by compnut41 on 2009-05-14
Are you using the partitioner through a live disk? Preferably 8.04 (I don't know it works better for me.)

---

### Post by Coh3n on 2009-05-14
I'm using the 9.04 disk.

---

### Post by michy99 on 2009-05-14
Are you running the partition editor from a boot cd? You cant resize the partion while it is mounted, and you can't unmount it while running from it.

Edit: wow i guess i'm slow.

---

### Post by Coh3n on 2009-05-14
Yeah, I'm running from the CD, I thought that's what I was suppose to do.

---

### Post by Sef on 2009-05-14
Let's see what your partitions are like

Applications > Accessories > Terminal

then copy and paste this code:

```
fdisk -l
``` copy and paste the results here.

---

### Post by drs305 on 2009-05-14
Is the extra space also in the extended (light blue border) partition. You can't take the space from a primary partition and put it directly into a logical one. You would first have to expand the extended partition and then take the space from there. You also want it adjacent to the partition you want to expand.

However, instead of guessing, it would probably be better to post a gparted snapshot so we can see what the situation really is.

---

### Post by Coh3n on 2009-05-14
I don't even get results... I get:

> ubuntu@ubuntu:~$ fdisk -l
ubuntu@ubuntu:~$ fdisk -l
ubuntu@ubuntu:~$ fdisk -l
ubuntu@ubuntu:~$ 


---

### Post by theozzlives on 2009-05-14
Do you have an extended partition that maybe you have to increase first?

---

### Post by Coh3n on 2009-05-14
Oh good call, I may have got it!
[IMG]http://img39.imageshack.us/img39/2595/screenshotd[/IMG]

---

### Post by Coh3n on 2009-05-14
Beautiful! Now I just have to wait 4 hours for it to work. Lol, thanks everyone!

---

### Post by 3startuna on 2009-05-14
Where is the freespace on the disk? 

It needs to be right beside the partiotion for you to be able to gro it.


Example (....) represents free space

[part1][Part2](...............)[Part3]

You will not be able to grow partition 1 without first moving partition 2 right beside partition 3.

I know its weird how g parted does this.

Also you will need to start up and run it on live CD (NOT IN THE INSTALL SCREEN PARTITIONER) (try linux withoutmaking changes ... option on the CD)

If you try to do it at the install screen partitioner you wont be able to grow only reduce

---

### Post by drs305 on 2009-05-14
the screenshot isn't coming up. and it would be:
```
sudo fdisk -l
```
with a lower case L if you are running this from the livecd and not recovery mode's root command line.

---

### Post by Coh3n on 2009-05-14
Yeah, not sure why the screenshot didn't work, but I think I've solved the problem.  Was pretty simple really - just had to expand the extended partition, then I could expand the sda5.

Thanks, everyone.

Now my attempt to get Java, the reason my problem started in the first place. :(

---

### Post by 3startuna on 2009-05-14
another point the way how I understand how G parted works is that it writes a partition to a specific location or group of sectors on a disc. It doesnt write to the hard drive like you burn to a CD i.e. from inside out. 

When you move a partition what it does is format the new area copy all the files to that area then delete the files from the old area where the partition was. 

hope this explains things. 

You need to run it as live CD to do any of these changes the install screen only allows you to shrink.

---

### Post by Coh3n on 2009-05-14
Yeah that makes sense, thanks. :)

---

