---
title: "Preparing partitions for a fresh 10.04 install"
date: 2010-08-22
forum: New to Ubuntu
---

### Post by constellanation on 2010-08-22
I'm doing a fresh install on my newly built computer (I initially had it set up as a server, but realized i didn't need a server as much as I thought)  

I'm trying to manually prepare the partitions on the install, since that seems to be the only way I can get it to partition and format both of my 1tb hard drives.

I know I don't want a raid set up I just want all of the storage available.   

I have 4gb of ram 
  -I'll mostly be using the space for movies, photo, music etc.. the usually
  -If I can ever get my tv tuner correctly configured I might be running mythbuntu
  -and I'd like to use it as a "sometimes" server

If I could get some recommendations on how everyone else would partition this I would appreciate it. thanks in advance

---

### Post by cj.surrusco on 2010-08-22
I would recommend using software RAID 1, but since you don't want that, I would advise making a 40GB partition on just one of the hard drives for /. 

Then, 2GB of swap on each hard drive. I think you can *slightly* increase swap performance by mounting on two disks because it will stripe the data.

I would then set up a LVM on the remaining space of both of the drives to store the movies, photos and music. 

Also, you should give software RAID a chance. You can set it up just for your / partition, and leave the rest non-RAID. The RAID can increase performance and your / partition would be safe in case of a drive failure. I would set up the entirety of the drives in RAID, but the suggested solution would allow you to use almost all of your hard drive capacity, as opposed to the latter, which would cut the storage space in half.


I'm sure other people may suggest other ways of going about this, but that's how I would do it.

---

### Post by constellanation on 2010-08-22
> **cj.surrusco said:**
> 
You can set it up just for your / partition, and leave the rest non-RAID. The RAID can increase performance and your / partition would be safe in case of a drive failure.

what kind of performance gains would i get from doing something like this?  I might be willing to try that out, since I won't feel like I'm "wasting" space (i know if the drives fail i won't be saying that)

thank you for your quick reply by the way.  The rest of that set up seems very logical and almost easy (which is good)


Edit: one more beginner question, when setting up the logical volume what format do you recommend and where is the best mount points?

---

### Post by bergfly on 2010-08-22
Most people use EXT4 nowadays, which seems good, stable and pretty fast. 

So put / in your primary

and put /home in your lvm

I would also recommend a spare partition for later upgrades. This little trick has saved me time and again. Make a /spare partition the same size as your /

Then when 10.10 comes out and you are tempted to do an upgrade,  you can first do a clean install into this partition and know it will all work, and once it does, then do the upgrade to your /. Upgrades don't always go as smoothly as one would like and getting a working system back when something goes wrong can be downright ugly.

RAID performance advantages comes from striping data across disks, which means two disks can be accessing data at once, rather one. The problem with this type of RAID is no redundancy, which brings more disks and different RAID types into play (welcome to the world of server...)

A note, RAID is not a backup solution, if data becomes corrupted on one disk, it becomes corrupted on both. Raid only protects against actual complete disk failure.

---

### Post by cj.surrusco on 2010-08-22
> **constellanation said:**
> what kind of performance gains would i get from doing something like this?  I might be willing to try that out, since I won't feel like I'm "wasting" space (i know if the drives fail i won't be saying that)

With RAID 1, you would have increased drive read speed, since it can read from two drives at once. Also, if a drive fails, the OS (and anything else on the RAID) will still run fine with only one drive. 

You can also use RAID 0, which won't "waste" any space (20 GB on each drive=40GB total for use) and it will have have increase read *and* write speeds. However, if a drive fails, there is no way to recover the data. 

> **constellanation said:**
> thank you for your quick reply by the way.  The rest of that set up seems very logical and almost easy (which is good)


Edit: one more beginner question, when setting up the logical volume what format do you recommend and where is the best mount points?

Ext4 or Ext3 would be fine for the job. You can find comparisons of the two filesystems anywhere.

As far as the mount point, it doesn't really matter. You can mount it at /home if you want (then application settings would be saved there), or you can have it separate from the home folder and mount it in a directory the /media folder, and use it just for the media. The home folder will be in the / partition if you go with the second option.

---

### Post by constellanation on 2010-08-22
I'm kind of combining both of your advices so far.  

If i decide to do the raid / partition can i do that at a later point?

I've added a photo of how i have it arranged so far, any recommendations or last minute changes?

---

### Post by cj.surrusco on 2010-08-22
> **bergfly said:**
> 
A note, RAID is not a backup solution, if data becomes corrupted on one disk, it becomes corrupted on both. Raid only protects against actual complete disk failure.

Not entirely true ;)

If you use a RAID 1 or RAID 5 setup, you are safe from an individual drive failure. You wouldn't be safe if your computer spontaneously combusts, but it sure can be used as a backup solution.

---

### Post by cj.surrusco on 2010-08-22
> **constellanation said:**
> I'm kind of combining both of your advices so far.  

If i decide to do the raid / partition can i do that at a later point?

I've added a photo of how i have it arranged so far, any recommendations or last minute changes?

If you decide to set up RAID later, it can be a huge pain. It is much easier to set it up during install. However, you can't do it with the normal Ubuntu install CD, you need the alternate CD.

EDIT: Also, you wouldn't need to mount that spare drive. You can leave it untouched until you need it.

---

### Post by -kg- on 2010-08-22
Much to my chagrin, I know next to nothing about LVM or how it's set up.  The image you have posted looks like a standard partitioning setup in the installer.

If you don't already know about it, I've found a pretty good article on the subject of setting up LVM on Debian (and Ubuntu) here:

[http://www.howtoforge.com/linux_lvm]("http://www.howtoforge.com/linux_lvm")

I'm going to read that page myself later.

---

### Post by constellanation on 2010-08-22
When you say leave it untouched, do you mean Just leave it blank (as free space)?

 I think I'm going to go ignorantly without any raid array for the time being... but only because I already have this one running.

---

### Post by cj.surrusco on 2010-08-22
> **constellanation said:**
> When you say leave it untouched, do you mean Just leave it blank (as free space)?

 I think I'm going to go ignorantly without any raid array for the time being... but only because I already have this one running.

Yes, you would need to configure the LVM after the install, since the Ubuntu installer does not support it.

---

### Post by constellanation on 2010-08-22
Man this is turning into more questions then I expected,  thanks for your patience and answers guys!

How would I set up lvm after install?

---

### Post by cj.surrusco on 2010-08-22
> **constellanation said:**
> Man this is turning into more questions then I expected,  thanks for your patience and answers guys!

How would I set up lvm after install?

I don't remember which tutorial I used to learn about LVM, but I think this one should do the trick. 

[https://help.ubuntu.com/community/SettingUpLVM-WithoutACleanInstall](https://help.ubuntu.com/community/SettingUpLVM-WithoutACleanInstall)

---

### Post by constellanation on 2010-08-22
ok so I redid the /spare so that in fact it is just free space. 

for clarification doing lvm is so that multiple physical disks have the appearance of one disk correct?


and finally when i try to go forward with the partitioning. It's not allowing me to mount two partitions at /home so sda and sdb can't both have /home, so what is a better alternative?

---

### Post by cj.surrusco on 2010-08-22
> **constellanation said:**
> ok so I redid the /spare so that in fact it is just free space. 

for clarification doing lvm is so that multiple physical disks have the appearance of one disk correct?

Yeah that's what you want to do.
> **constellanation said:**
> 
and finally when i try to go forward with the partitioning. It's not allowing me to mount two partitions at /home so sda and sdb can't both have /home, so what is a better alternative?
You would have to make the LVM across the two disks *first*. Then you could mount the /home directory to the LVM.

---

### Post by constellanation on 2010-08-22
so i should leave that blank also and format it after?

---

### Post by cj.surrusco on 2010-08-22
Yeah. Do that.

---

### Post by constellanation on 2010-08-22
Thanks for all your help, I think I'm going to have to do some more research into lvm.  I tried following those two different guides and I'm a little lost... 

this is from [this thread]("https://help.ubuntu.com/community/SettingUpLVM-WithoutACleanInstall") my questions are in red...

 > 1. Backup your data!!
 [COLOR="Red"]no need for this it's a fresh install[/COLOR]

2.Map out your goals for LVM. Do you just want some expandable space for media files? Do you want to move your /home into LVM? Do you want to move everything under LVM? If you want to put everything under LVM, you should create a separate /boot partition (100MB should be fine) - otherwise you may not be able to boot your system.
[COLOR="red"]does it matter where i make this /boot and do i have to mount it or is simply creating it in gparted enough?[/COLOR]

3.You're going to need some free space to setup your volume groups. You can use:
Free space on your primary hard drive.
A partition that you are not using any more. (such as the Windows partion you haven't booted in 6 months, that is what Qemu/VMWare are for isn't it??)
A new blank hard drive you've added to your system.
4.Format your free space/partition/new drive using your favorite disk management tool to "Linux LVM".
[COLOR="red"]ok, i have both free space and in theory an extra hard drive, do i need to reformat everything I intended to be /home? gparted also isn't giving me linux lvm as an option for formatting, is there a better disk management tool or am i missing a step?[/COLOR]

 Also use some of this space to create your separate /boot partition (100MB, ext3, bootable flag) if you are planning on putting everything under LVM.
[COLOR="red"]is that what i'm doing "putting everything under lvm?" or is the fact that i have other stuff in / not part of the lvm mean i should be doing something else?[/COLOR]

5.Now that you have an LVM partition you can create your volume groups on. Note that you don't need a single large partition formated to Linux LVM, you can format as many smaller LVM partitions as you like, and combine them into a single filesystem using the power of LVM later - this is the preferred method as it allows more flexibility.
[COLOR="red"]not sure what this means, and what the benefit is or why i would do this?[/COLOR]

6.Install "lvm2" from the Ubuntu repositories. ("sudo aptitude install lvm2")
[COLOR="red"]I get this part done :)[/COLOR]

7.Optionally install "system-config-lvm". Here: [http://ubuntuforums.org/showthread.php?t=216117](http://ubuntuforums.org/showthread.php?t=216117) is a forum thread on how to install it from Fedora RPM, (its not available in Ubuntu repositories.)
[COLOR="red"]I think i can pass on this[/COLOR]

8.Load the LVM module - modprobe dm-mod. You can skip this step in Jaunty (9.04) because the dm-mod module is compiled into the kernel.
[COLOR="red"]and i think i can skip this as well[/COLOR]

9.If that works without any errors, you can go ahead and add dm-mod to the end of your /etc/modules file (sudo nano /etc/modules). This will autoload LVM when Ubuntu starts - very important if you plan on moving your system directories under LVM.
[COLOR="red"]i assume i will have to do this though if i ever get to this point?[/COLOR]then it's the configuration.... sigh...


---

### Post by constellanation on 2010-08-23
Edit: should i just try reinstalling with the alternate cd?  I suspect that might make this whole thing a lot easier.  also if I do reinstall (or do a fresh install I suppose) with this would i be able to set up that raid1 configuration on my /home partition?

just a little bump, still lost... staring at my output for fdisk and I don't really know what I'm doing for lvm, it seems there is little up to date info on it, on google.

this is my fdisk readout if it helps to know what I'm working with currently....
> Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
248 heads, 63 sectors/track, 125033 cylinders
Units = cylinders of 15624 * 512 = 7999488 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000bea85

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         256     1998848   82  Linux swap / Solaris

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006ca40

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4980    39999488   83  Linux
/dev/sda2            4980      121602   936760321    5  Extended
/dev/sda5            4980        5229     1998848   82  Linux swap / Solaris
/dev/sda6            5229      121602   934760448   83  Linux


---

