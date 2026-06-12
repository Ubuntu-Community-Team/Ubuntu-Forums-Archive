---
title: "problem in partitions need help"
date: 2011-01-04
forum: New to Ubuntu
---

### Post by Mayank Bhagat on 2011-01-04
Hello I am using windows xp 
I have four drives and i want to install ubuntu as a single operating system without formatting my other three drives.
I want to install ubuntu on the drive which has windows.

Thank You.

---

### Post by seawolf167 on 2011-01-04
Welcome to the forums!

I'd start by reading the [Ubuntu/Windows Dual Boot ]("https://help.ubuntu.com/community/WindowsDualBoot")article (installing Ubuntu after Windows) and coming back and asking if you have any questions (or asking Google!)

Ubuntu can read NTFS partitions (i.e. Windows) so there is no need to re-format them. You will, however, have to at least re-partition the hard drive which contains Windows (assuming you will install Ubuntu on that hard drive). If you are worried, you can always unplug the 3 "data" drives and re-plug them in after you get everything installed.

---

### Post by Bucky Ball on 2011-01-04
You are looking to install Ubuntu on the same drive as Windows? Good idea and easy. Do you have free space on that drive? If not, make some.

10.04 LTS is the go. As a new user you will have a smoother ride. ;)

Let us know what you have on the drive you are looking to install to.

Or are you saying you want to get rid of XP and just install Ubuntu on that drive? That's even easier!

Welcome, and good call from seawolf. If you are a bit worried unplug the other three. But let us know what you are intending to do specifically first (and perhaps avoid that hassle). The Windows partitions will all be NTFS or FAT, easily recognisable. They will be clearly visible when you get to the partitioning section of the install. You just leave them alone and install to some free space or over a partition you don't want.

---

### Post by coffeecat on 2011-01-04
> **Mayank Bhagat said:**
> Hello I am using windows xp 
I have four drives

When you say "four drives", do you mean physical hard drives or four partitions? Windows has a habit of calling partitions drives, which is very confusing.

---

### Post by Bucky Ball on 2011-01-04
> **coffeecat said:**
> When you say "four drives", do you mean physical hard drives or four partitions? Windows has a habit of calling partitions drives, which is very confusing.

Yep, and you can't have any more than four partitions on a single physical hard drive, therefore you couldn't install Ubuntu anyhow without some serious partition manipulation. You would need to add an extended partition (which can contain up to 99 virtual partitions) which would mean deleting one of the existing partitions. :)

---

### Post by Mayank Bhagat on 2011-01-04
> **Bucky Ball said:**
> You are looking to install Ubuntu on the same drive as Windows? Good idea and easy. Do you have free space on that drive? If not, make some.

10.04 LTS is the go. As a new user you will have a smoother ride. ;)

Let us know what you have on the drive you are looking to install to.

Or are you saying you want to get rid of XP and just install Ubuntu on that drive? That's even easier!

Welcome, and good call from seawolf. If you are a bit worried unplug the other three. But let us know what you are intending to do specifically first (and perhaps avoid that hassle). The Windows partitions will all be NTFS or FAT, easily recognisable. They will be clearly visible when you get to the partitioning section of the install. You just leave them alone and install to some free space or over a partition you don't want.

yeah i want to get rid of xp and install ubuntu on the same drive
Thanks

---

### Post by Bucky Ball on 2011-01-04
Firstly, do you have four hard drives or one hard drive with four partitions? This makes a difference.

Either way, I would use 10.04 LTS as this is more stable and as a new user you will get a smoother ride. Boot from the CD and install Ubuntu.

When you get to the partitioning section, choose to manually partition, wipe the drive you are wanting to install Ubuntu on and make it all free space.

Now, get a pen and paper and decide exactly what you want on there. For Ubuntu, at the very least, you are going to want:

/ = where you OS lives (15Gb should be plenty)
/home =where your data lives (whatever size you like)
/swap = doesn't need to be more that 2Gb

You can add others and call them what you like but the ones I mention are set as defaults if you want to choose them. Make them all EXT4 partitions (except /swap which chooses its own file type). As I said before; if you want more than four partitions on one physical drive you are going to need an extended partition. (/ and /home, then an extended partition with your other partitions in there and /swap last).

When you're ready, set up your partitions and continue with the install.

You could unplug the other drives, if they exist, but you could also just avoid them (they won't show anyhow as Gparted partitioner, the one you'll be using, only shows one drive at a time).

---

### Post by Mayank Bhagat on 2011-01-04
> **Bucky Ball said:**
> Firstly, do you have four hard drives or one hard drive with four partitions? This makes a difference.

Either way, I would use 10.04 LTS as this is more stable and as a new user you will get a smoother ride. Boot from the CD and install Ubuntu.

When you get to the partitioning section, choose to manually partition, wipe the drive you are wanting to install Ubuntu on and make it all free space.

Now, get a pen and paper and decide exactly what you want on there. For Ubuntu, at the very least, you are going to want:

/ = where you OS lives (15Gb should be plenty)
/home =where your data lives (whatever size you like)
/swap = doesn't need to be more that 2Gb

You can add others and call them what you like but the ones I mention are set as defaults if you want to choose them. Make them all EXT4 partitions (except /swap which chooses its own file type). As I said before; if you want more than four partitions on one physical drive you are going to need an extended partition. (/ and /home, then an extended partition with your other partitions in there and /swap last).

When you're ready, set up your partitions and continue with the install.

You could unplug the other drives, if they exist, but you could also just avoid them (they won't show anyhow as Gparted partitioner, the one you'll be using, only shows one drive at a time).

Sorry for inconvenience 
I have one hard drive and four partitions. 
and the one in which i want to install is of only 10 GB. 
Is there any possibility to install in this partition.
Thanks a lot again for the help.

---

### Post by Bucky Ball on 2011-01-04
> **Mayank Bhagat said:**
> Sorry for inconvenience 
I have one hard drive and four partitions. 
and the one in which i want to install is of only 10 GB. 
Is there any possibility to install in this partition.
Thanks a lot again for the help.

Not really. This would be very minimal. It could be done though as Ubuntu can read NTFS and other partitions so you could keep your personal data on your existing partitions. It really depends on what Ubuntu you are going to install (among other things). 

You could install Ubuntu to 8Gb and save 2Gb for the /swap file. Remembering; your /home partition will be inside the / (root or OS partition) and therefore you could avoid using it and store your personal data elsewhere on one of the existing partitions. That would work.

---

