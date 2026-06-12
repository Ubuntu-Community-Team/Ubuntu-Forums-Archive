---
title: "dual boot questions"
date: 2011-07-28
forum: New to Ubuntu
---

### Post by johnw512 on 2011-07-28
I downloaded ubuntu by dual booting it with winXP..now i want to delete/uninstall winXP to free up hardrive. Do i need to either copy ubuntu to a CD or is there another way to do it?

---

### Post by Paqman on 2011-07-28
Did you use Wubi to install Ubuntu? Wubi looks like this:
[IMG]https://help.ubuntu.com/community/Wubi?action=AttachFile&do=get&target=Wubi3.png[/IMG]

If so then Ubuntu is installed as a virtual partition on the Windows filesystem, which means that if you wipe Windows, you wipe Ubuntu. You should back up your data and reinstall Ubuntu using a CD or USB stick if you want to end up with a 100% Ubuntu system.

---

### Post by johnw512 on 2011-07-28
That is exactly what i used! I can use a regular blank CD for ubuntu? Also i have already tried to delete winXP and was having problems (which is probably a good thing since i would of deleted ubuntu as well) do u kno of any good websites that will make deleting winXP as easy as possible?   
   THX!

---

### Post by Paqman on 2011-07-28
> **johnw512 said:**
> That is exactly what i used! I can use a regular blank CD for ubuntu?

You can. For best results, burn it at a low speed. It has to be bit-perfect. There are instructions and help on the [download page]("http://www.ubuntu.com/download/ubuntu/download").

You need to boot up off the disk and tell the installer to use the whole drive when it asks. This will wipe *everything*, including Windows, Ubuntu and all your data. But you'll end up with a nice fresh machine running only Ubuntu.

---

### Post by johnw512 on 2011-07-28
Is it better to download on a USB or a CD?

---

### Post by Mark Phelps on 2011-07-28
You DO understand that deleting XP will delete Ubuntu, right?

Just wanted to be sure you were aware of that.

---

### Post by Paqman on 2011-07-28
> **johnw512 said:**
> Is it better to download on a USB or a CD?

Makes no difference really, use what you've got. Although you do occasionally find some machines that refuse to boot from a USB.

---

### Post by johnw512 on 2011-07-28
okay just to be sure can i get the procedures to unistalling winXP and installing ubuntu..and second how many gigs does the usb need to be?

---

### Post by gradysghost on 2011-07-28
I just want to make a response here saying first of all that by installing Ubuntu, you *will* delete *all* of your data.  I know it's already been said here, but it really can't be said enough.  If you have precious data, back that up first!

If you're going to make a USB installer out of it, you'll need one that's at least 1 GB in size.  If this is your first time installing Ubuntu, it may just be easier for you to burn it to a standard blank CD-ROM as it doesn't complicate the task at all, although Ubuntu will install much faster from a USB stick.

---

### Post by gradysghost on 2011-07-28
I just want to make a response here saying first of all that by installing Ubuntu, you *will* delete *all* of your data.  I know it's already been said here, but it really can't be said enough.  If you have precious data, back that up first!

If you're going to make a USB installer out of it, you'll need one that's at least 1 GB in size.  If this is your first time installing Ubuntu, it may just be easier for you to burn it to a standard blank CD-ROM as it doesn't complicate the task at all, although Ubuntu will install much faster from a USB stick.

---

### Post by Paqman on 2011-07-28
> **johnw512 said:**
> okay just to be sure can i get the procedures to unistalling winXP and installing ubuntu..and second how many gigs does the usb need to be?

You don't need to actually need to uninstall Windows first, you just install Ubuntu over the top of it. When you run the Ubuntu installer one of the options will be something like "Erase Windows and install Ubuntu", which is the one you want.

---

### Post by johnw512 on 2011-07-28
THX and this is a new computer to me it has alot of problems in the windows os like running slow and registry errors and whatnot..there is no data on there that i want to keep however will unistalling windows delete any needed data that i will need on ubuntu?

---

### Post by johnw512 on 2011-07-28
Ok i sent that last one without looking at all post sorry..so basically when i download ubuntu it will guide me doin everything i need done? also what is a good version to start off with? thx

---

### Post by oldfred on 2011-07-28
Some info on migrating. I think it assumes you are keeping XP, at least for the time being. One advantage of keeping XP & wubi is if you forgot to copy something you can go back & get it. But it is a bit more work to delete XP after the install and create a partition for data in the freed up space. Moving Ubuntu can be done but is even more difficult.

HOWTO: migrate wubi install to partition - bcbc 
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

I like separating data from system. System then has its files closer together on drive & is slightly quicker. 

Basics of partitions:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

---

### Post by Paqman on 2011-07-28
> **johnw512 said:**
> however will unistalling windows delete any needed data that i will need on ubuntu?

It will delete *everything* on the drive, so you would need to back it all up first. It's a good idea to have backups of your data anyway.

---

