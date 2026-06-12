---
title: "Mounting Problem"
date: 2011-05-13
forum: New to Ubuntu
---

### Post by Robert1305 on 2011-05-13
I have been trying to load 11.04 onto my 500gb hard drive with no success.

I think I have stumbled on as to why..............the HD is mounted at /media/new volume........and I think it should be....../....is this correct?

If so,how do I change the mount point to /.

Thanks.

---

### Post by sikander3786 on 2011-05-13
What are you trying to achieve? I guess you are simply trying to install 11.04? If yes, only your Ubuntu System Partition (that will hold the system files, /home etc) would be mounted as '/' and all other partitions would be mounted under /media. I mean the data partitions, NTFS, ext3/ext4 etc.

Does the HDD contain any other OS? How many partitions are there? We can guide you step by step through the installation setup.

---

### Post by dezzie-boy on 2011-05-13
Try changing the bios to mount the hdd you want to install on first, run ubuntu from disk, format and partition the drive and install...

---

### Post by Robert1305 on 2011-05-13
> **sikander3786 said:**
> What are you trying to achieve? I guess you are simply trying to install 11.04? If yes, only your Ubuntu System Partition (that will hold the system files, /home etc) would be mounted as '/' and all other partitions would be mounted under /media. I mean the data partitions, NTFS, ext3/ext4 etc.

Does the HDD contain any other OS? How many partitions are there? We can guide you step by step through the installation setup.

[ATTACH]192017[/ATTACH]

This is the drive I am trying to load 11.04 on to

---

### Post by sikander3786 on 2011-05-13
Ok. So you want to assign all of that disk space to Ubuntu? My partition plan would be something like this.

1. Primary, Ubuntu System Partition, Mount Point '/', size > 30 GB, ext4
2. Primary, Home Partition, Mount Point '/home', size > 10 GB at least, ext4
3. Extended Partition
a. Logical, Data Partition, Mount Point '/media', sized = custom, ext4 or NTFS if you want to share between different OS.
b. Logical, Swap, size = RAM X 2 for hibernating.

For a better idea of partitioning, I hope this page would help.

[http://ubuntu4beginners.blogspot.com/2011/02/manual-advanced-partitioning-in-ubuntu.html](http://ubuntu4beginners.blogspot.com/2011/02/manual-advanced-partitioning-in-ubuntu.html)

For a simple setup, you can just start the Ubuntu installer and choose 'Use entire disk' at the partitioning step so the installer would automatically create the needed partitions.

---

### Post by Morbius1 on 2011-05-13
OK, I'll admit it,  I'm confused.

Are you trying to install 11.04?

Or are you trying to mount the 11.04 install from another OS on that machine?

---

### Post by Robert1305 on 2011-05-13
> **Morbius1 said:**
> OK, I'll admit it,  I'm confused.

Are you trying to install 11.04?

Or are you trying to mount the 11.04 install from another OS on that machine?

All I want to do is install 11.04 onto that drive.

---

### Post by Robert1305 on 2011-05-13
> **sikander3786 said:**
> Ok. So you want to assign all of that disk space to Ubuntu? My partition plan would be something like this.

1. Primary, Ubuntu System Partition, Mount Point '/', size > 30 GB, ext4
2. Primary, Home Partition, Mount Point '/home', size > 10 GB at least, ext4
3. Extended Partition
a. Logical, Data Partition, Mount Point '/media', sized = custom, ext4 or NTFS if you want to share between different OS.
b. Logical, Swap, size = RAM X 2 for hibernating.

For a better idea of partitioning, I hope this page would help.

[http://ubuntu4beginners.blogspot.com/2011/02/manual-advanced-partitioning-in-ubuntu.html](http://ubuntu4beginners.blogspot.com/2011/02/manual-advanced-partitioning-in-ubuntu.html)

For a simple setup, you can just start the Ubuntu installer and choose 'Use entire disk' at the partitioning step so the installer would automatically create the needed partitions.

I have always used the simple setup and let the installer create the partitions, as I always use the entire disk for the OS, but when I try to install I get the message..."no root file system defined,,..please correct from the partitioning menu."

---

### Post by Morbius1 on 2011-05-13
I'm really begiining to wonder if "Disk Utility" knows what it's doing. That partition is listed as "Linux  swap" in your attachment. If you're doing a advanced install and telling it to place / in there without a reformat then it won't work. But if you tell it to reformat then it should take care of things.

You might want to post the output of the following command just to see how Linux itself sees those partitions:
```
sudo blkid -c /dev/null
```

---

### Post by sikander3786 on 2011-05-13
> **Robert1305 said:**
> I have always used the simple setup and let the installer create the partitions, as I always use the entire disk for the OS, but when I try to install I get the message..."no root file system defined,,..please correct from the partitioning menu."
Can you please post a screen shot of that error message?

---

### Post by Robert1305 on 2011-05-13
> **Morbius1 said:**
> I'm really begiining to wonder if "Disk Utility" knows what it's doing. That partition is listed as "Linux  swap" in your attachment. If you're doing a advanced install and telling it to place / in there without a reformat then it won't work. But if you tell it to reformat then it should take care of things.

You might want to post the output of the following command just to see how Linux itself sees those partitions:
```
sudo blkid -c /dev/null
```

Options:
  -c <file>   cache file (default: /etc/blkid.tab, /dev/null = none)
  -h          print this usage message and exit
  -g          garbage collect the blkid cache
  -o <format> output format; can be one of:
              value, device, list, udev or full; (default: full)
  -s <tag>    show specified tag(s) (default show all tags)
  -t <token>  find device with a specific token (NAME=value pair)
  -l          lookup the the first device with arguments specified by -t
  -L <label>  convert LABEL to device name
  -U <uuid>   convert UUID to device name
  -v          print version and exit
  -w <file>   write cache to different file (/dev/null = no write)
  <dev>       specify device(s) to probe (default: all devices)

Low-level probing options:
  -p          switch to low-level mode (bypass cache)
  -S <bytes>  overwrite device size
  -O <bytes>  probe at the given offset
  -u <list>   filter by "usage" (e.g. -u filesystem,raid)

---

### Post by Morbius1 on 2011-05-13
Never seen that happen before. I can reproduce it if I make "c" "C". Did you make it a small "c"?

---

### Post by Robert1305 on 2011-05-13
Right lets see if I can confuse the problem even further.

1/.... I have a 11.04 disk.
2/....It installed into my laptop no problem.
3/....Liked 11.04 and Unity, so loaded into my desk top, no problems is working OK on my 160gb HD, but, the HD is making some funny noises.
4/....Son-in-law gave me a nearly new 500gb HD, format-ed.
5/.... Fit into my PC, and that is what I am trying to install 11.04 on.
6/.... Installs up to where it should ask me where I want to install it.ie, along side, use entire disk etc, except this is not happening, I get a screen I have never seen before, and when I click on install it comes up with..."no root file system is defined....correct this from the partitioning menu.

And that's it in a nutshell folks.

PS/...Even more confusing, I have an old Ubuntu 9.04 disk and this installs and works perfectly on the 500gb HD....

PSS/...Even, even more confusing I have tied 5 different distros, and 9.04 is the only one that installs.

---

### Post by Lateralis on 2011-05-14
I am really struggling to work out what it is that you are doing or what is going wrong.  I've personally never seen that error message before but I certainly don't believe it is related to the hard drive.  

Someone earlier in the thread asked if you could post a screenshot of the error message next to the installation window and I think that would be really helpful.

---

