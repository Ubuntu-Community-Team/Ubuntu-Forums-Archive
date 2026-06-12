---
title: "install ubunto beside windows 7 in netbook??"
date: 2010-09-27
forum: New to Ubuntu
---

### Post by Dantey on 2010-09-27
Hi....

I have a netbook...[Samsung N150]... with 250 GB...

Hard disk = C+D... 120GB + 120GB = and of course as ntfs..

I want to install ubunto on it beside windows 7...

but i am afraid that i get windows 7 and the hard disk damaged...

i want windows 7 on C Drive... and ubunto on D Drive...

my question is how can i make a disk ready for ubunto..

when i want to install ubunto... the third screen for the disk..

what is the exactly steps to install it on disk D without damaged the windows 7 and without damaged the boot of windows...

also without damage the disks....



sorry for bad english...

---

### Post by cap10Ibraim on 2010-09-27
error

---

### Post by Paqman on 2010-09-27
First of all: Ubuntu cannot damage your disks, but it is wise to back up your data before altering your partitions.

If you run the Ubuntu installer it will give you the option to install Ubuntu side-by-side with Windows 7. You can tell it how much of the disk to use.

You currently have one drive split into two partitions, which Windows calls C:/ and D:/. Ubuntu will shrink one of those down to make room for itself, then create some new partitions to install itself on. You don't have to do this yourself, just tell the installer how much space you want to give to Ubuntu (20GB is plenty) and it will make it all happen for you.

If you're still nervous about partitioning then there is a way to install without doing any. It's called [Wubi]("http://www.psychocats.net/ubuntu/wubi"), and it's really easy to use.

---

### Post by xumuk37 on 2010-09-27
You should make 4 partitions on your D drive: first - some 200 Mb as ext2 as /boot, about 2- 3 Gb as swap area, an amount of 10 Gb as ext4 for root /  and the same ext4 the rest for your home partition (/home). Good luck and welcome to Ubuntu!

---

### Post by Paqman on 2010-09-27
> **xumuk37 said:**
> You should make 4 partitions on your D drive

It's a netbook. I strongly suspect D:/ is a partition, not a drive.

---

### Post by Dantey on 2010-09-27
> **Paqman said:**
> First of all: Ubuntu cannot damage your disks, but it is wise to back up your data before altering your partitions.

If you run the Ubuntu installer it will give you the option to install Ubuntu side-by-side with Windows 7. You can tell it how much of the disk to use.

You currently have one drive split into two partitions, which Windows calls C:/ and D:/. Ubuntu will shrink one of those down to make room for itself, then create some new partitions to install itself on. You don't have to do this yourself, just tell the installer how much space you want to give to Ubuntu (20GB is plenty) and it will make it all happen for you.

If you're still nervous about partitioning then there is a way to install without doing any. It's called [Wubi]("http://www.psychocats.net/ubuntu/wubi"), and it's really easy to use.  

thanks for replay...

but i tried wubi before on a laptop...

then... windows doesn't boot...

and the 'tech guy' have to open the laptop to fix the hard disk..

because the hard disk became un formatable via windows...

so i think i will try the installer of ubunto...

---

### Post by Planetes on 2010-09-27
I have a win7/Ubuntu dualboot on my laptop. I would suggest backing up your files before you attempt anything. I  had a lot of trouble with my partitioning, mainly with the four primary restriction. I wanted to split my D: into two parts for swap and ubuntu but it was over the limit so i went with an overwrite on the windows "recovery parition (15mb)" and made that my swap. I've never used a netbook but i would assume that windows would partition your hard drive the same way initially.

---

### Post by Dantey on 2010-09-27
also... in my laptop....

some of hard disk become logical...

this one have 100 GB

and it become unusable....

windows can't read it....

then i try to format it via unbuntu 'usb try version' into FAT...

but still windows can't read it or format it...

i am afraid that when i install unbuntu on my netbook..

it will become like this... and i will lose my original W7...

============

i realy want to try another os .... i get boring from windows...


i tried to install mac os... and the same problem happened...

---

### Post by Mark Phelps on 2010-09-27
> **Dantey said:**
> ... and i will lose my original W7...

With desktops, preinstalled with Win7, it's a simple matter to use the Backup feature to create and burn a Win7 Repair CD.  Thus, as long as you don't actually remove the Win7 OS partition, it's a quick boot from the CD and a few repair actions to restore Win7 boot functionality.

But with Netbooks, there is no CD drive, and I don't personally know if the Backup feature can create the same bootable-solution with a USB stick.

That makes messing around with multi-booting a LOT riskier with a netbook than with a desktop or more traditional laptop.

Still ... it's a good idea to do an image backup (of your Win7 partitions) to an external drive before you start down this path.

At least that way, if the worst happens, you can get your working Win7 setup back.  And, given that Macrium Reflect is a free download, and it can be used to create a Restore CD, doing a backup is a cheap as getting an external USB stick or drive.

---

