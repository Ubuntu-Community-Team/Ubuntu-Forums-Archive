---
title: "moving `/home` file to `/` partition"
date: 2009-05-07
forum: New to Ubuntu
---

### Post by shultays on 2009-05-07
hello

my /home folder is another partition than /

I want to move it back to / partition (just convert it a regular file not a mount)

how can i do this? i am on a live cd edition so  every partitioin is unmounted

---

### Post by shultays on 2009-05-07
hello

my /home folder is on another partition than /

I want to move it back to / partition (just convert it a regular file not a mount)

how can i do this? i am on a live cd edition so every partitioin is unmounted

---

### Post by b@sh_n3rd on 2009-05-07
Well, I'm not exactly sure if you COULD do that...but having /home in a different partition is an advantage. Like, just in case you need to reinstall Ubuntu, you only need to format the /boot and /root partitions and all your existing files will still be available when you're done reinstalling.

---

### Post by Dngrsone on 2009-05-07
I wish I could tell you... out of curiosity, why do you want to do that?  Having /home on a separate partition makes things easier for reinstalling or upgrading the OS, since you won't lose any of your data and settings that way.

---

### Post by mcduck on 2009-05-07
Mount both partitions, then create a /home directory on the root partition (if one doesn't exist). Next copy all your user home directories from the old /home partition there.

Next edit the /etc/fstab file on the / partition, and remove the entry for mounting /home.

That's it. Boot the system and confirm that everything works.

After that you can use any partition editor to remove the old /home partition and use that space for something else or possibly merge the space to one of your existing partitions.


edit: For the other people who replied to this, if you don't have the habit of breaking your system and having to reinstall, keeping /home on the same partition with root has it's advantages as well. ;)

---

### Post by shultays on 2009-05-07
I need some extra storage for windows. that is why i want to remove home partition. i shrinked it a bit and increased the size of / partition. after moving home to / i will reformat old home as ntfs

is there any way to divide in a partitioin into two without making grub giving error 22? Once before a merged two partitions into one and my pc didn`t boot anymore (error 22) i had to re install linux in order to fix my boot loader

---

### Post by shultays on 2009-05-07
> **mcduck said:**
> Mount both partitions, then create a /home directory on the root partition (if one doesn't exist). Next copy all your user home directories from the old /home partition there.

Next edit the /etc/fstab file on the / partition, and remove the entry for mounting /home.

That's it. Boot the system and confirm that everything works.

After that you can use any partition editor to remove the old /home partition and use that space for something else or possibly merge the space to one of your existing partitions.

thanks. before trying that is it possible to split a partition into two without causing error 22 on grub? i have gparted but i afraid that it will cause that grub error.

---

### Post by Dngrsone on 2009-05-07
> **shultays said:**
> I need some extra storage for windows. that is why i want to remove home partition. i shrinked it a bit and increased the size of / partition. after moving home to / i will reformat old home as ntfs

is there any way to divide in a partitioin into two without making grub giving error 22? Once before a merged two partitions into one and my pc didn`t boot anymore (error 22) i had to re install linux in order to fix my boot loader

Ah, gotcha!

Yes, I do break my machine on a semi-regular basis.  It seems like every upgrade manages to screw me up as well, which is why I'm going to wait a while before moving to Jaunty.  [IMG]http://i230.photobucket.com/albums/ee303/Dngrs_1/rolleyes.gif[/IMG]

---

### Post by SuperSonic4 on 2009-05-07
> **shultays said:**
> thanks. before trying that is it possible to split a partition into two without causing error 22 on grub? i have gparted but i afraid that it will cause that grub error.

Grub error 22 comes from deleting/editing the partition on which /boot resides (in your case this is likely to be /)

Can you post the outputs of ```
cat /boot/grub/menu.list
``` and ```
sudo fdisk -l
```

---

### Post by mcduck on 2009-05-07
> **shultays said:**
> thanks. before trying that is it possible to split a partition into two without causing error 22 on grub? i have gparted but i afraid that it will cause that grub error.
That shouldn't be a problem, unless you are about to do that to your root partition. In  that case you just need to reinstall Grub afterwards, which really is rather easy thing to do.

Just remember that changing the partitions in any way will also change their UUID's, so you will need to edit the /etc/fstab file to use correct UUIDs for your partitions afterwards.

---

### Post by shultays on 2009-05-07
> **mcduck said:**
> That shouldn't be a problem, unless you are about to do that to your root partition. In  that case you just need to reinstall Grub afterwards, which really is rather easy thing to do.

Just remember that changing the partitions in any way will also change their UUID's, so you will need to edit the /etc/fstab file to use correct UUIDs for your partitions afterwards.

So it is okay to split my home partition into two? (by splitting i mean shrinking it and creating a new partition on new unallocated place)

also how can I reinstall grub?

---

### Post by cariboo on 2009-05-07
Just copy your user directory into /home on your main hard drive, then remove the mount entry for your /home partition in /etc/fstab.

---

### Post by SentientFluid on 2009-05-07
Lots of replies in your other post here:
[http://ubuntuforums.org/showthread.php?p=7232797#post7232797](http://ubuntuforums.org/showthread.php?p=7232797#post7232797)

---

### Post by Sef on 2009-05-07
Locked.  [Duplicate Post]("http://ubuntuforums.org/showthread.php?p=7232815#post7232815").

---

### Post by Dngrsone on 2009-05-07
But that one is locked.

---

