---
title: "Sensible partitioning"
date: 2009-03-04
forum: New to Ubuntu
---

### Post by RichardCL on 2009-03-04
Hi Forum members,

I'm looking for suggestions on partitioning for home use.

I've got 2x1TB hard drives on a desktop system with 6GB RAM. The system gets used mainly for office applications including imaging applications (GIMP / UFRAW with images up to about 5MB).

I'm considering RAID1 for my documents. Most older stuff gets backed up to a NAS and a USB HDD.

I'd also like my documents accessible via ftp or similar from outside. Is a separate partition useful for that?

Any ideas?


Richard

---

### Post by hammad1337 on 2009-03-04
10 GB is enough for a root "/" partition. but since u have quite a lot to spare, 20-25GB would make sure u don't need to resize for some years.

I have a seperate /home/user/ partition...If u want much more organised structure, u can use a partition each for the folders in the home directory,(i.e. music,videos,pictures,documents,etc). The size depends on what amount of data u gonna have for each category.

U don't need a swap partition as 6GB ram is more than enough for now.
(u are using a 64-bit system, i suppose, because, otherwise only 4 GB of ram is used, the rest is wasted.)

Hope u find these suggestions useful.

---

### Post by RichardCL on 2009-03-05
Many thanks for the pointers.

I am using 64bit (core 2 quad with 8.10 64bit edition).

I've been considering the separate home partition. I'm assuming that I can change the operating system without change to files in this case (e.g. fresh Ubuntu install with new version or a different distribution). I was just wondering. What happens with the configuration files that are stored under home e.g. /home/user/.skype /home/user/.filezilla? Do these files get used by the applications when they are reinstalled or overwritten?

What about the two hard drives? Is there any advantage to have /home/user on a different drive from system or should the swap file go on the different drive? Do I need swap on both drives (is that faster)?

---

### Post by mikechant on 2009-03-05
> What happens with the configuration files that are stored under home e.g. /home/user/.skype /home/user/.filezilla? Do these files get used by the applications when they are reinstalled or overwritten?

All the apps I have come across which use this type of config files will use an existing .appname folder in your home directory if it exists, or create a new one if it doesn't.

If you are uninstalling an app then the synaptic package manager gives you a choice of keeping or deleting configuration files. I'm not at my Ubuntu PC at present so I don't know if the simpler add/remove programs tool offers this option or not.

Occasionally using old config files with new versions of applications can cause problems. When I used Fedora a few years ago and when did a version upgrade, I seem to remember having to delete some config folders (maybe .gnome or similar) to solve some problems (windows too big for desktop etc.).
But generally it should work just fine.

---

### Post by Vishal Agarwal on 2009-03-05
Keep some unused/partitioned space, so that you can use it later as and when needed. U will need just to create the partition and to mount that.

---

### Post by RichardCL on 2009-03-05
Thanks for the tips.

I'm now planning to move my home partition to sdb (currently unused and unformatted). After that, I'll reinstall Ubuntu on sda when I get the chance.

My plan is to put

sda
20MB boot
180GB swap
200GB Ubuntu 8.10 OS
600GB free space

sdb
200GB /swap/
800GB /home/user/

I'm using GParted to partition the harddisks. Can I create the new partitions from within the operating system and have the system continue to work?

I can make a new home partition and tell the machine to mount as home. How to I move the files in the current home directory and tell Ubuntu to use the new "home".

Finally, what partition is best to use ext3?

---

### Post by marco123 on 2009-03-05
How much swap? :shock:  You'd be better off with:

100Mb /boot
30GB /
1GB /swap
rest for /home 

Just use the other drive for data storage and mount it as something like /Internal2, that's what I do.  You don't really need a separate /boot.

Cheers, Marco.

Edit: Yes ext3 is best.

---

### Post by RichardCL on 2009-03-05
Hi Marco,

Thanks for the suggestion.

Can I move/resize home or should I just backup and then do a full reinstall?

I guess the partition type for swap is linux-swap. Do I need a label for the volume?


Richard

---

### Post by marco123 on 2009-03-05
With such a big change (and that much space) I'd backup first and do a nice fresh install.

You could format your second internal to ext3 ready, drag everything to that and then install fresh.  Just when it comes to the partitioning mount it as Internal2 (or whatever) but don't format it. (Obviously.)  Good luck.:D

Cheers, Marco.

---

