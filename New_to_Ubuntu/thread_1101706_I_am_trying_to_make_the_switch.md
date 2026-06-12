---
title: "I am trying to make the switch"
date: 2009-03-20
forum: New to Ubuntu
---

### Post by therabidbadger on 2009-03-20
Here we go.

Setup: 

Msi Wind Netbook first-gen; 
80gb HDD (4ish gb system restore files (d:), 40ish gb Windows install (c:), 35ish gb free space(e:))
Thats all you probably need to know for my question.

Goal: Dual-boot Win (c:) and Ubuntu (e:)

Problem: I really don't know what a paging drive is.

I have tried to install ubuntu on my comp (I am using a 8.04 CD) I have found where one will use a custom partition, but it says something about a "paging drive" needed. I have no idea what that is. I tried to just go into windows and delete the e: partition, then just let ubuntu do it magic on the newly combined c:, but windows will not let me delete it. Well, it would but "unknown system errors" may be caused because of it.

So what do I do? Do I divide e: into two drives, if so how big for each? Do you think windows uses the e: as a "paging drive" (still don't know what is)? If I divide it up will that cause a problem with windows?

Let me know. Thanks so much to you all.

---

### Post by Anthon on 2009-03-20
Windows might use it, but in that case you should see some of the disk space taken (shutdown windows, boot from Ubuntu CD, mount e: partition and look if there are any files on that partition).

Are you sure the install CD is not asking for *swap* partition? To have this is strongly recommended, although not absolutely necessary. You could install without a swap partition and later create a swap file. Alternative is to delete the e: partition ( probably called /dev/sda2 in the CD rom setup, but make sure to double check (including the sizes)),
and then create two new partitions: one the 1 or 2x the size of memory  ( 1Gb mem -> 1 or 2Gb of swap partition ) and the rest as root ( / ) partition.

---

### Post by pbpersson on 2009-03-20
A paging or swap area is a section on your disk which is used as virtual memory.

This is not a new concept, back in the old Windows 3.1 days it was a large hidden file in the root directory of your C: drive called pagefile.sys.

For instance, if you have 2GB of RAM and you open too many applications you can run out of memory.  Rather than limit how many applications you can have open, the system will "expand" the RAM by writing some of the data to your hard drive.

If you have 2GB of RAM and a 4GB swap partition, you really have 6GB of total "memory" available.

If you go beyond the limit of the available RAM and swap space, bad things will happen.  In Windows you get an error such as "You are running low on virtual storage, close down some windows or close some applications" and then before you can do anything, Windows slows to a crawl and then hangs up.

I have never seen this happen in Linux.

---

### Post by therabidbadger on 2009-03-20
Thank you for your comments.

So let me see if I get this straight. I should go into the ubuntu install up to where I was before editing partitions and whatnot. Create two partitions from the above stated e: drive. One I make into a 2gb drive because I have 1gb of ram then make the other drive the root drive. 

If windows was using the e: as a paging or swap drive then will windows use the new 2gb drive as one?

Question: if windows cannot use the file notation *insert proper linux speak here* (not FAT32 or NTFS but the linux one) then will windows use it as a paging drive? Can one make the linux swap drive NTFS? So, that windows can use it.

Is bad to have your hard drive split into four partitions?

---

### Post by AndyCooll on 2009-03-20
> **therabidbadger said:**
> Thank you for your comments.

So let me see if I get this straight. I should go into the ubuntu install up to where I was before editing partitions and whatnot. Create two partitions from the above stated e: drive. One I make into a 2gb drive because I have 1gb of ram then make the other drive the root drive. 

If windows was using the e: as a paging or swap drive then will windows use the new 2gb drive as one?

Question: if windows cannot use the file notation *insert proper linux speak here* (not FAT32 or NTFS but the linux one) then will windows use it as a paging drive? Can one make the linux swap drive NTFS? So, that windows can use it.

Is bad to have your hard drive split into four partitions?

Ignore what Windows is saying about "paging", it will deal with "paging" in it's own way when you log in to Windows. From a Linux point of view this is irrelevent (and is just confusing the issue).
As mentioned above, you need to create (a minimum) of two extra partitions for Linux, one for "swap" and a second for your root (/) partition.

And no it isn't bad to have you hard-drive split into partitions. Think of them as slices of a cake.

:cool:

---

### Post by Helios1276 on 2009-03-20
This might be of interest to you,

[http://wiki.msiwind.net/index.php/Ubuntu_8.04_Hardy_Heron](http://wiki.msiwind.net/index.php/Ubuntu_8.04_Hardy_Heron)

---

### Post by sandyd on 2009-03-20
> **therabidbadger said:**
> Thank you for your comments.

So let me see if I get this straight. I should go into the ubuntu install up to where I was before editing partitions and whatnot. Create two partitions from the above stated e: drive. One I make into a 2gb drive because I have 1gb of ram then make the other drive the root drive. 

If windows was using the e: as a paging or swap drive then will windows use the new 2gb drive as one?

Question: if windows cannot use the file notation *insert proper linux speak here* (not FAT32 or NTFS but the linux one) then will windows use it as a paging drive? Can one make the linux swap drive NTFS? So, that windows can use it.

Is bad to have your hard drive split into four partitions?

4 partitions are ok. Keep in mind the fact that there is a maximum of 4 Primary Partitions. 

NO, windows would not use that as a paging file.

now heres something that will make people flame me.....

if your not really into partitioning, you can Install Ubuntu using Wubi. Just pop the cd into the Drive. Open up the cd (if autorun doesn't start) click "Install inside windows". Remember to set the hard disk size to something high as you won't be able to adjust it later... It will automatically create a swap partition and everything for yo9u. After you reboot the computer, go and walk for 10 km, come back, restart your computer, select "Ubuntu" as your OS option when your computer starts up.

Thats it.

---

### Post by sandyd on 2009-03-20
> **pbpersson said:**
> A paging or swap area is a section on your disk which is used as virtual memory.

This is not a new concept, back in the old Windows 3.1 days it was a large hidden file in the root directory of your C: drive called pagefile.sys.

For instance, if you have 2GB of RAM and you open too many applications you can run out of memory.  Rather than limit how many applications you can have open, the system will "expand" the RAM by writing some of the data to your hard drive.

If you have 2GB of RAM and a 4GB swap partition, you really have 6GB of total "memory" available.

If you go beyond the limit of the available RAM and swap space, bad things will happen.  In Windows you get an error such as "You are running low on virtual storage, close down some windows or close some applications" and then before you can do anything, Windows slows to a crawl and then hangs up.

I have never seen this happen in Linux.

I have :)

runaway Adobe photoshop CS3 in WINE.

I came back and found my computer with a blank screen and it didn't respond to anything. force shutted it down and when restarted got a KDE warning dialog saying that Adobe photoshop CS3 crashed.....

---

### Post by therabidbadger on 2009-03-21
Thank you all for your comments.

---

