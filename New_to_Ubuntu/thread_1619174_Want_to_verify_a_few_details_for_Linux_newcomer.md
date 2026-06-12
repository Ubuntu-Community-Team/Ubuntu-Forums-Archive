---
title: "Want to verify a few details for Linux newcomer"
date: 2010-11-11
forum: New to Ubuntu
---

### Post by hobbes543 on 2010-11-11
So, I am planning on installing a new hard drive into my desktop and then installing Linux to this drive as a dual boot with Win 7 (already on my other drive)  Now, since my new drive is 1TB and I don't need all that space for Ubuntu, I wanted to set my partitions up this way,

1: 200 GB primary in EXT4 for / to install Ubuntu and for software installs
2: 8 GB Swap
3: 80 GB in EXT4 or EXT3 for /home
4: Remainder format in NTFS for data storage and shared space between both OSes.

I have never installed Linus before and was wondering what the best way of setting up the drive.  Should I leave the drive blank and use the Ubuntu installer to create and format the first three partitions and then after Ubuntu has installed, boot into Windows to format the final partition?  Or would it be better to use Window's disk manager to create the partitions, leaving the first 3 unformated and then formatting the remainder in NTFS before I do the Ubuntu install?

The other detail I want to clarify concerns grub.  Does the Ubuntu installer install grub by default on MBR of the drive it is being installed to?  I have read that for this type of setup, where Windows and Linux are on separate disks that you want grub on the disk with Linux and then have your BIOS boot from that disk.  What was never clear to me was where the installer tries to put grub by default and if I would have to do something special to specify that grub be placed on the second drive.

---

### Post by bioterror on 2010-11-11
I would just install like this:

swap 8GB
/    rest of 1TB drive.

But you if you want to do it like you have planned, you should give something like 10GB for the / and rest for /home.

---

### Post by c2tarun on 2010-11-11
> **hobbes543 said:**
> So, I am planning on installing a new hard drive into my desktop and then installing Linux to this drive as a dual boot with Win 7 (already on my other drive)  Now, since my new drive is 1TB and I don't need all that space for Ubuntu, I wanted to set my partitions up this way,

1: 200 GB primary in EXT4 for / to install Ubuntu and for software installs
2: 8 GB Swap
3: 80 GB in EXT4 or EXT3 for /home
4: Remainder format in NTFS for data storage and shared space between both OSes.

I have never installed Linus before and was wondering what the best way of setting up the drive.  Should I leave the drive blank and use the Ubuntu installer to create and format the first three partitions and then after Ubuntu has installed, boot into Windows to format the final partition?  Or would it be better to use Window's disk manager to create the partitions, leaving the first 3 unformated and then formatting the remainder in NTFS before I do the Ubuntu install?

The other detail I want to clarify concerns grub.  Does the Ubuntu installer install grub by default on MBR of the drive it is being installed to?  I have read that for this type of setup, where Windows and Linux are on separate disks that you want grub on the disk with Linux and then have your BIOS boot from that disk.  What was never clear to me was where the installer tries to put grub by default and if I would have to do something special to specify that grub be placed on the second drive.


boot form linux live CD choose try linux.
open GParted and do the partition as per your choice, leave a 200 GB space unallocated. then click on install and u r done

still having problem, visit this page... 
[http://tricksfind.blogspot.com/2010/09/ubuntu-install-linux-quick-and-easy.html](http://tricksfind.blogspot.com/2010/09/ubuntu-install-linux-quick-and-easy.html)

---

### Post by hobbes543 on 2010-11-11
And I will be able to install linux software to the /home partition?  

And I do not want the whole 1TB for Ubuntu... so the last ~700 GB I still want to format as NTFS so my Windows install can access that space easily.

Still unclear about the grub bit.

---

### Post by Verbeck on 2010-11-11
200 gb / is too big
try these

30 gb / (i doubt this would ever get full)
swap : same as RAM
rest /home (application settings , downloads and other stuff goes here by default)

as for the ntfs partitions,  leave the space unallocated from the installer and create them later

you can select where the grub loader is to be installed from the installation. in 10.10 its on the partitioning step and in 10.04 its in the final stage before you click install ( click the advanced buton)

---

### Post by mcduck on 2010-11-11
200GB for root is quite a lot, especially if you have a separate partition for /home.

You'll have to install serious amount of stuff to even fill a 10GB root partition.

I'd probably go for 20GB root, max. (Actually I only use 10GB for my root, and with pretty huge amount of audio/video tools and stuff installed I'm still using only a bit over 4GB)

The swap is quite large as well. You didn't mention how much you have RAM on the machine, but with anything over 1GB you have not likely to ever actually need the swap space for swapping. So you'll only need it if you want to suspend the machine, in which case you'll need as much swap as you are using RAM at the time (excluding buffers&cache, since you don't need to store those when suspending). If you want to play it safe, use equal amount of swap as you have RAM installed. In reality you wouldn't even need that much, 2-3GB should be more than enough.

The only thing that will require much space is your personal files.

---

### Post by DarthScape on 2010-11-11
Best way might be to: Install Windows to the drive, then, when installing Linux, move the slider to your desire, it seems pointless to keep /home on a separate partition, doesn't really help much, unless you plan on reinstalling a few times.

---

### Post by hobbes543 on 2010-11-11
> **Verbeck said:**
> 200 gb / is too big
try these

30 gb / (i doubt this would ever get full)
swap : same as RAM
rest /home (application settings , downloads and other stuff goes here by default)

as for the ntfs partitions,  leave the space unallocated from the installer and create them later

you can select where the grub loader is to be installed from the installation. in 10.10 its on the partitioning step and in 10.04 its in the final stage before you click install ( click the advanced buton)

So, just to be clear, I can use the /home partition then for software installation, should / get full?  And thank you for clarifying the grub loader.  All the guides I have found talk about dual booting when both OSs are going to be on the same drive.  

And I ask about the /home partition because I would like to try and migrate the software I use most in my windows install and run through wine in Linux.  One of these being WoW, which at this point weighs in at close to 20 GB or so.  So I want to make sure I have a space large enough in the linux parts of the drive to install some of this stuff. ect...   And since I am not familiar with how linux handles installs / running of windows software through wine, I wanted to insure there was enough space for installs of other software, namely games which tend to run quite big.  Another plan is to install Steam as well...

---

### Post by Tony Flury on 2010-11-11
My Unix install - reasonably modest - only got a few development tools and internet tools installed, only takes up 6GB on a 17Gb partition - and i have never had a partition full message.

---

### Post by Tony Flury on 2010-11-11
> **DarthScape said:**
> Best way might be to: Install Windows to the drive, then, when installing Linux, move the slider to your desire, it seems pointless to keep /home on a separate partition, doesn't really help much, unless you plan on reinstalling a few times.

I would disagree - I think a separate /home is a good idea - just in case.

---

### Post by Verbeck on 2010-11-11
all wine stuff is installed in /home/username/.wine
only linux stuff go in / (they don't take much space)
so you'll need a large /home if you install a lot of wine apps

hope this helps

---

### Post by hobbes543 on 2010-11-11
> **DarthScape said:**
> Best way might be to: Install Windows to the drive, then, when installing Linux, move the slider to your desire, it seems pointless to keep /home on a separate partition, doesn't really help much, unless you plan on reinstalling a few times.

Windows is already installed on a 500GB drive I have in the machine and I don't want to mess with that drive.  I have a new 1TB drive that is still unopened that I plan to put in the computer.  This is the drive I want to install Ubuntu onto.  And the separate /home partition is so that if I do have to reinstall I don't loose all my data.

---

### Post by hobbes543 on 2010-11-11
> **Verbeck said:**
> all wine stuff is installed in /home/username/.wine
only linux stuff go in /

hope this helps


Thanks.  That is good to know.  so yeah... /home will be the big one then... Though actually... shouldn't need to actually migrate WoW over... Since I will be able to mount my C: drive in Linux and can just run the WoW executable from there through wine, if what I read is correct.    But there are other games that I want to migrate over ect...

---

### Post by mcduck on 2010-11-11
> **hobbes543 said:**
> So, just to be clear, I can use the /home partition then for software installation, should / get full?  And thank you for clarifying the grub loader.  All the guides I have found talk about dual booting when both OSs are going to be on the same drive.  

And I ask about the /home partition because I would like to try and migrate the software I use most in my windows install and run through wine in Linux.  One of these being WoW, which at this point weighs in at close to 20 GB or so.  So I want to make sure I have a space large enough in the linux parts of the drive to install some of this stuff. ect...   And since I am not familiar with how linux handles installs / running of windows software through wine, I wanted to insure there was enough space for installs of other software, namely games which tend to run quite big.  Another plan is to install Steam as well...

For Linux programs, no, you can't install them on your /home partition. The programs aren't installed in any single location, instead each file is placed in different place based on the file's purpose. All executables from all your programs are in one place, documentation and manuals in one place, icons & images in one place and so on.

On the other hand, the Linux programs are not going to cause you any problems when it comes to disk space.

Wine is a bit of a different beast, but luckily for you everything you install in Wine will be installed in your own home directory. So you don't need to do anything at all, your Windows programs will end on your /home partition automatically. (Wine creates a fake Windows file system inside a hidden directory in your home dir).

Just don't count too much on things actually *running* with Wine. Some programs work, many won't, and large part requires at least some tweaking and still doesn't run well. If you depend heavily on Windows applications you should instead just dualboot, or at least check the databases at WineHQ website to see if your software runs with Wine or not.

---

### Post by madmax75 on 2010-11-11
Yeah, 200 GB is WAY much for the apps, and I think 80 GB for /home might be too little.

My own /home folder is something like 50 GB. You won't believe how quickly you can fill 80 GB up with all sort of stuff :)

I would reserve more for /home and less for linux and apps.

EDIT:

I checked my system with the Baobab disk usage analyzer, and got this:

I have a 141 GB hard drive.

Linux currently uses about 78 GB of it.

My /home is 72,2 GB. So yeah, I believe you also might want much more than 80 GB :)

And the rest (some 5 to 6 GB) is all the Linux stuff and apps (/usr, /var, /lib, /boot and so on). So the Ubuntu installation in itself is something like 5-6 GB or so, give or take.

And of these /var uses overwhelmingly the majority of disk space, some 870 MB. I probably have many useless log files and temporary files lying around there...

I hope this example of my own system can give you some ideas and pointers how to set up your own.

---

### Post by Jerry N on 2010-11-11
I don't use a separate /home partition anymore although many people recommend it.  Since I used Windows more than Linux, and since Linux accesses NTFS just fine, I would agree with the large NTFS partition.  What I have done under the dual drive circumstance is to first disconnect the drive that has Windows and then install Linux on the new drive, using gparted to partition the drive the way you want it.  After you have installed Linux and have assured yourself that it is running to your satisfaction, turn off the machine and reconnect the Windows drive.  The next time you boot, grub (installed only on your new 1tb drive) will find Windows and give you the option of opening Windows or your new Linux program.  Nothing will have been done to the Windows drive and if the new drive was to go up in smoke you could still run Windows just fine.  On my secondary computer (which has removable drives)presently one drive (SATA) has Windows 7 and Windows XP and the other has Mint 9 and Ubuntu 10.10.  

Jerry

---

### Post by walt.smith1960 on 2010-11-12
> **mcduck said:**
> 200GB for root is quite a lot, especially if you have a separate partition for /home.

You'll have to install serious amount of stuff to even fill a 10GB root partition.

I'd probably go for 20GB root, max. (Actually I only use 10GB for my root, and with pretty huge amount of audio/video tools and stuff installed I'm still using only a bit over 4GB)

The swap is quite large as well. You didn't mention how much you have RAM on the machine, but with anything over 1GB you have not likely to ever actually need the swap space for swapping. So you'll only need it if you want to suspend the machine, in which case you'll need as much swap as you are using RAM at the time (excluding buffers&cache, since you don't need to store those when suspending). If you want to play it safe, use equal amount of swap as you have RAM installed. In reality you wouldn't even need that much, 2-3GB should be more than enough.

The only thing that will require much space is your personal files.

I agree with most of this post--Linux takes less than 3 GB. to install the O.S. and included software. It's nowhere near as bloated as Windows.  You do not need a swap partition to **suspend. **I am using a swap file instead of a swap partition and can suspend just fine.  I would need a swap partition if I wanted to** hibernate.** The difference as I understand it is when I suspend RAM is kept refreshed so with a notebook some battery power is used.  If I were to hibernate, RAM info is written to the disk (swap partition) so the RAM is not using battery power.  I haven't tried hibernating Linux but Windows hibernation was pointless--it took as long to resume from hibernation as it took to cold boot so I would simply shut down. I find Ubuntu suspend/resume to be quite reliable.

---

### Post by mcduck on 2010-11-12
> **walt.smith1960 said:**
> I agree with most of this post--Linux takes less than 3 GB. to install the O.S. and included software. It's nowhere near as bloated as Windows.  You do not need a swap partition to **suspend. **I am using a swap file instead of a swap partition and can suspend just fine.  I would need a swap partition if I wanted to** hibernate.** The difference as I understand it is when I suspend RAM is kept refreshed so with a notebook some battery power is used.  If I were to hibernate, RAM info is written to the disk (swap partition) so the RAM is not using battery power.  I haven't tried hibernating Linux but Windows hibernation was pointless--it took as long to resume from hibernation as it took to cold boot so I would simply shut down. I find Ubuntu suspend/resume to be quite reliable.

Yeah, you are correct about hibernate. I always mix up the two, as I seem to always end with hardware that fails both suspending and hibernating regardless of what OS I run so I never use them myself. :)

---

### Post by c2tarun on 2010-11-12
> **mcduck said:**
> 200GB for root is quite a lot, especially if you have a separate partition for /home.

You'll have to install serious amount of stuff to even fill a 10GB root partition.

I'd probably go for 20GB root, max. (Actually I only use 10GB for my root, and with pretty huge amount of audio/video tools and stuff installed I'm still using only a bit over 4GB)

The swap is quite large as well. You didn't mention how much you have RAM on the machine, but with anything over 1GB you have not likely to ever actually need the swap space for swapping. So you'll only need it if you want to suspend the machine, in which case you'll need as much swap as you are using RAM at the time (excluding buffers&cache, since you don't need to store those when suspending). If you want to play it safe, use equal amount of swap as you have RAM installed. In reality you wouldn't even need that much, 2-3GB should be more than enough.

The only thing that will require much space is your personal files.


hi mcduck...
buddy i installed my ubuntu in 30 gb partition and i hardly installed any serious package.... and only 17 GB left now... **over 10GB is full **
is there any problem with my installation??? my home folder is of around 2GB??
i m not using any other operating system....

---

### Post by sydbat on 2010-11-12
> **hobbes543 said:**
> Thanks.  That is good to know.  so yeah... /home will be the big one then... Though actually... shouldn't need to actually migrate WoW over... Since I will be able to mount my C: drive in Linux and can just run the WoW executable from there through wine, if what I read is correct.    But there are other games that I want to migrate over ect...You should be able to run all the games that you have installed in your Windows partition, depending on whether they will run in wine. You shouldn't need to install them in Linux / wine separately.

---

### Post by mcduck on 2010-11-12
> **c2tarun said:**
> hi mcduck...
buddy i installed my ubuntu in 30 gb partition and i hardly installed any serious package.... and only 17 GB left now... **over 10GB is full **
is there any problem with my installation??? my home folder is of around 2GB??
i m not using any other operating system....

Try running "sudo apt-get clean" to remove the package manager's cached packages. If you've never done that it should give you a fair amount of free space.

The Disk Usage Analyzer in the Applications/Accessories -menu is also a good tool for finding out where your disk space is used. To make things easier you mighr want to go to Edit/Preferences and set the filesystem scan to only include your root partition.

---

### Post by c2tarun on 2010-11-12
> **mcduck said:**
> Try running "sudo apt-get clean" to remove the package manager's cached packages. If you've never done that it should give you a fair amount of free space.

The Disk Usage Analyzer in the Applications/Accessories -menu is also a good tool for finding out where your disk space is used. To make things easier you mighr want to go to Edit/Preferences and set the filesystem scan to only include your root partition.


i did the file system scan as said and found that.
usr folder 4.3GB
home folder 3.1GB
var folder 1.1GB

these are the major occupants.
+ i m not sure exactly is this the cache u are talking about, but /var/chache is of 750 MB

the /var/chache/apt folder is of 534MB it contains the setups of the packages i downloaded using sudo apt-get.

so do i run sudo apt-get clean

---

