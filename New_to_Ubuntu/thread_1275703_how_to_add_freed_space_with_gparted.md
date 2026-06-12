---
title: "how to add freed space with gparted"
date: 2009-09-26
forum: New to Ubuntu
---

### Post by boogey on 2009-09-26
hi everyone,

after a few problems with updating I discovered (with the help of users here) that I have not enough space on my harddrive. I was told to use gparted to transfer some unused space from one of my partitions to the other (that is full). I burned an iso file of gparted and ran the live cd and even freed up some 3 GiB (that is unallocated space right now) but haven't managed it to add it to the partition where I need the extra space. what do I do wrong?
this is my harddrive:
>  Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             1.4G  961M  307M  76% /
varrun                252M  128K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
udev                  252M   68K  252M   1% /dev
devshm                252M   12K  252M   1% /dev/shm
lrm                   252M   40M  212M  16% /lib/modules/2.6.24-24-386/volatile
/dev/sda8              57G   26G   29G  48% /home
/dev/sda6             4.6G  4.4G   45M  99% /usr
/dev/sda7             2.8G  813M  1.9G  31% /var

I still try to add space to sda6 after taking 3 GiB (that are unallocated at present) from sda8. 
thanks for helping even though this might be a dumb question...

---

### Post by Liolikas on 2009-09-26
You can not add there you want. There has to be continuation. Actually you are in real mess and reainstall should be considered.

I suggest to shrink:
/dev/sda8 57G 26G 29G 48% /home
to create  about 20Gb space and create new partition then move:
/dev/sda1 1.4G 961M 307M 76% / to it and move
/dev/sda6 4.6G 4.4G 45M 99% /usr to /usr folder of it
Then move /dev/sda7 2.8G 813M 1.9G 31% /var to /var folder of it.
And edit /etc/fstab to apply changes new place / no more /usr at all.

Then you have scatered empty space you can merge last two now empty partitions and create /media/disk or sth like that from it.

Congrats if you do not created even more mess it the end.

---

### Post by CatKiller on 2009-09-26
> **Liolikas said:**
> Actually you are in real mess and reainstall should be considered.

That's crazy talk.

To the OP: Use Gparted (you've already got the Gparted live cd) to shuffle the partitions around. As Liolikas says, you need the unallocated space next to the partition that you want to grow to be able to grow the partition into the unallocated space. From the numbers you'll probably need to move sda8 & sda7 to the right so that the space is to the right of sda6, and then expand sda6 to the right, although it might be different depending on your partitioning setup.

---

### Post by drs305 on 2009-09-26
This post might provide a few hints for resizing your partitions, especially your / partition:
[Expanding an Ubuntu System Partition]("http://ubuntuforums.org/showthread.php?t=1219270")

---

### Post by boogey on 2009-09-26
thanks everyone. all I do is moving sda7 and 8 so that they will be to the right of sda6 n the graphical display? can I do the same with the unallocated space? and do I just have to find "expand" 
in the menue and apply after that? It might also help to know that I only have ubuntu on that machine....

---

### Post by CatKiller on 2009-09-26
> **boogey said:**
> thanks everyone. all I do is moving sda7 and 8 so that they will be to the right of sda6 n the graphical display? can I do the same with the unallocated space? 

You don't need to do anything to the unallocated space. It's just a hole where there's no partition. Moving the partition to the right will necessarily move the unallocated space to the left.

> and do I just have to find "expand" 
in the menue and apply after that?

It's exactly the same Resize/Move tool that you've already used to resize one partition, and that you'll use to move the other two. Then you just resize the partition you want to make bigger by dragging the end into the unallocated space.

---

### Post by boogey on 2009-09-26
thanks again, worked perfectly and I after working with gparted I see that some of my questions were a little uninformed, sorry about that. but yeah, great I tried to move a few GiB and this is how my computer looks now:

> 
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             1.4G  961M  307M  76% /
varrun                252M  120K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
udev                  252M   68K  252M   1% /dev
devshm                252M   12K  252M   1% /dev/shm
lrm                   252M   40M  212M  16% /lib/modules/2.6.24-24-386/volatile
/dev/sda8              57G   26G   29G  48% /home
/dev/sda6             7.5G  4.4G  2.8G  61% /usr
/dev/sda7             2.8G  422M  2.3G  16% /var


cheers.

---

