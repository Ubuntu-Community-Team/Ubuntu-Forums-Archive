---
title: "NEED HELP! How to move two partitions together?"
date: 2011-03-19
forum: New to Ubuntu
---

### Post by tambu883 on 2011-03-19
Hi!
I'm new to ubuntu and I'm wondering, how to move to partitions together to create a 1 bigger one. At the moment i have linux swap and 2 ext4 partitions.
i would like to move the ext4 partitions together to create one big partition with mount point /. Is it possible?
Many thanks!

---

### Post by TeoBigusGeekus on 2011-03-19
Boot up with a live cd/usb, open a terminal and fire up gparted (gnome partition editor):
```
gksu gparted
```

---

### Post by kansasnoob on 2011-03-19
> **tambu883 said:**
> Hi!
I'm new to ubuntu and I'm wondering, how to move to partitions together to create a 1 bigger one. At the moment i have linux swap and 2 ext4 partitions.
i would like to move the ext4 partitions together to create one big partition with mount point /. Is it possible?
Many thanks!

NO! It's hardly that simple!

At the very least post the output of:

> sudo parted -l

Or better yet post a screenshot of Gparted.

We also need to know what's on each partition. Only you will know :D

---

### Post by tambu883 on 2011-03-19
Thanks for replying!
Do I have to just open gparted? When i wrote that command, it didn't find it. what do i have to do in gparted?

---

### Post by TeoBigusGeekus on 2011-03-19
I hope we're not talking about a wubi installation right?

If you are on a live cd/usb, open up a terminal and give
```
gksu gparted
```
If the command isn't recognized, it means that gparted isn't installed. So install it
```
sudo apt-get install gparted 
```
and then launch it
```
gksu gparted
```
After that, post us a screenshot of your gparted screen and the output of 
```
sudo fdisk -l
```

---

### Post by tambu883 on 2011-03-19
Here is my screenshot: [http://img138.imageshack.us/i/screenshot1sx.png/](http://img138.imageshack.us/i/screenshot1sx.png/)
There is my xp and ibm recovery parations and there is sda5, where i have linux, sda 6 is  linux swap files and sda7 is the one that i want to join with sda5. Is here all the information needed?
Sorry for being such a newbie :oops:

---

### Post by TeoBigusGeekus on 2011-03-19
Right click on sda7. There should be an option to move the partition.

Make sure you don't interrupt gparted for whatever reason. Let it finish its job for as long as it takes.

---

### Post by coolbrook on 2011-03-19
Back up data from your partitions.  Download the Gparted Live CD image, burn it to a disc and boot your computer from it.  Delete one partition and 'grow' the other one. Restore your data once you've rebooted.

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

USB is another option.

---

### Post by kansasnoob on 2011-03-20
I can see from that /dev/sda7 is nearly empty, only about 130MiB used, so I'd assume that's the partition you want to delete, eh :confused:

Something I'd ask before advising any further is that you boot into your installed Ubuntu and post the output of these two commands:

```
df -H
```

```
cat /etc/fstab
```

Just to be sure we don't break something :)

And then, which OS do you want to give the free space to? Windows or Ubuntu?

Also what flavor of Windows do you have? I prefer resizing Win7 & Vista OS's with their own tools.

Certainly Gparted is the way to go with the rest.

---

### Post by tambu883 on 2011-03-20
Gparted gives me an option to resize/move, but i can't figure out, how to move, it gives me only option to resize. Heres a screenshot of that: [http://img835.imageshack.us/i/screenshot3sg.png/](http://img835.imageshack.us/i/screenshot3sg.png/) . I want to grow my ubuntu partition, the other OS is Windows XP SP2.

---

### Post by mikewhatever on 2011-03-20
You don't have any unallocated space, so there is nowhere to move the partition to. I guess the word you are looking for is 'merge'.

---

### Post by TeoBigusGeekus on 2011-03-20
Instead of resizing it, delete it.
New unallocated space will be created and it will probably be merged with the unallocated space above and below sda7.
Then right click sda5 and resize it taking all the unallocated space you created before.

---

### Post by kansasnoob on 2011-03-20
> **TeoBigusGeekus said:**
> Instead of resizing it, delete it.
New unallocated space will be created and it will probably be merged with the unallocated space above and below sda7.
Then right click sda5 and resize it taking all the unallocated space you created before.

+1 - but I wanted the OP to post his fstab (or the output of "df -H") while booted into his installed Ubuntu just to be certain that sda7 isn't something like a separate /boot partition or such.

---

### Post by TeoBigusGeekus on 2011-03-20
> **kansasnoob said:**
> +1 - but I wanted the OP to post his fstab (or the output of "df -H") while booted into his installed Ubuntu just to be certain that sda7 isn't something like a separate /boot partition or such.

No worries mate :popcorn:

I just think that if he had a separate /boot partition he'd know how to resize partitions. :P

---

