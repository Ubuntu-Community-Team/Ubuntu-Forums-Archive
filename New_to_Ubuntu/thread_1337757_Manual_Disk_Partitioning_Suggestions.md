---
title: "Manual Disk Partitioning Suggestions?"
date: 2009-11-25
forum: New to Ubuntu
---

### Post by BT1 on 2009-11-25
So, I want to manually install Xubuntu using a manual partition scheme. What size do you suggest for the various mounts (i.e. /home, /var, /opt, etc.).

I have two drives that are 320G each (280 usable for some odd reason). The second HD I am going to be using something else, so I'll be using the first HD to set this up. I'm going to have heavy HD usage such as storing ISOs and my own ripped DVD back ups.

If you could, could you explain the mounts like...

What is...

/home for (I know mostly)
/var (what does it do)
/opt (what is it for)

etc.

And could you give size suggestions for each?

Also it asks me if I should enable "bootable" option. What is that for? Does it meaaan?!?!

Thanks!

---

### Post by pi.boy.travis on 2009-11-25
> **BT1 said:**
> So, I want to manually install Xubuntu using a manual partition scheme. What size do you suggest for the various mounts (i.e. /home, /var, /opt, etc.).

I have two drives that are 320G each (280 usable for some odd reason). The second HD I am going to be using something else, so I'll be using the first HD to set this up. I'm going to have heavy HD usage such as storing ISOs and my own ripped DVD back ups.

If you could, could you explain the mounts like...

What is...

/home for (I know mostly)
/var (what does it do)
/opt (what is it for)

etc.

And could you give size suggestions for each?

Also it asks me if I should enable "bootable" option. What is that for? Does it meaaan?!?!

Thanks!

I would recommend:

2X your RAM = swap size

30-50 GB for /

Remaining space for /home.

Unless you are running a high-load server, that should suffice.

---

### Post by bryanl on 2009-11-25
I find 12 GB for / works, even with a swapfile of 2 GB. Remainder for /home is same here. I don't worry about var, temp, usr, etc as I see no need on a modern PC with only one user.

I prefer to make a swapfile rather than a swap partition ([Move to swapfile rather than swap partition](http://tcl.leipper.org/?p=992))/

If I have two drives. I set up one with root and home and then put one partition on the second for the whole works then mount it in a convenient place depending upon how I plan to use it.

I see Handbrake just came out with the 64 bit Ubuntu version - that is a good way to rip DVD's and fill up a hard drive!

The manual setup in the Ubuntu install will take care of bootable flags and Grub stuff so you don't need to worry about that either.

---

### Post by bodhi.zazen on 2009-11-25
See if this helps : [http://www.cyberciti.biz/tips/the-importance-of-linux-partitions.html](http://www.cyberciti.biz/tips/the-importance-of-linux-partitions.html)

@ bryanl : With a desktop having more then 2 Gb of ram, why have a swap file at all ? 

Unless you are performing very ram intense applications you may not even need a swap file and can increase performance by reducing swappiness.

---

### Post by handydan918 on 2009-11-25
Just a note about /var....
That is where temp lives, and it's not uncommon to fill a root partition by some unfortunate series of events, like ripping vids, a malfunctioning server writing endless logfiles, etc....
If you put /var on it's own partition, you woll not suffer a DOS when the partition fills up, because it won't be writing to /

Very likely unneeded on 90+% of all personal computers...but the other 10% is where all these posts come from!

---

### Post by pi.boy.travis on 2009-11-25
You still need a swap partition.  A separate swap partition will provide better performance than a swapfile, from my experience anyways.  It is always good to have one.

---

### Post by francisco_athens on 2009-11-25
I like to partition this way:


| 10-15GB UBUNTU / | 10-15GB UNFORMATTED | REMAINDER /home/ | MAYBE some common storage area as /media/storage | SWAP |

This way the second partition can be used for a future ubuntu installation and you can always go back to the first in case things go pear-shaped. A new Ubuntu installation will auto detect the previous and add it to a new grub boot menu.  

you can also do this


| 10+GB* UBUNTU / | 10+GB* UNFORMATTED | REMAINDER /media/storage | SWAP |
*depending on how much space your home folder users need.

this way the home folders reside in their respective sytem roots and is a more cautious route.  So after you install a new Ubuntu, you copy the home folder of the previous install with rsync -a 

in either case, on your third install you write over your first partition (as you probably dont need it anymore) on your fourth you write over your second, etc.

This approach has saved me many times.  Basically instead of "upgrading" you are doing nice clean installs and just leaving your home folders intact or copying over your old home folders to the new install.

---

### Post by Shpongle on 2009-11-25
> **pi.boy.travis said:**
> I would recommend:

2X your RAM = swap size

30-50 GB for /

Remaining space for /home.

Unless you are running a high-load server, that should suffice.

yea this would well cover you!!

---

### Post by grandsatrap on 2009-11-27
> **handydan918 said:**
> Just a note about /var....
That is where temp lives, and it's not uncommon to fill a root partition by some unfortunate series of events, like ripping vids, a malfunctioning server writing endless logfiles, etc....
If you put /var on it's own partition, you woll not suffer a DOS when the partition fills up, because it won't be writing to /

Very likely unneeded on 90+% of all personal computers...but the other 10% is where all these posts come from!

I have some questions:
Do you mean /var/tmp? I don't have a /var/temp. I do have /tmp and it is not linked to /var/tmp -- so there are two /tmp directories. Do you know what the /tmp and /var/tmp folders are for?
Yes, it looks like /var could get filled up quickly because it has mail and logfiles and other stuff in it.

---

### Post by Captain_tux on 2009-11-28
> **grandsatrap said:**
> I have some questions:
Do you mean /var/tmp? I don't have a /var/temp. I do have /tmp and it is not linked to /var/tmp -- so there are two /tmp directories. Do you know what the /tmp and /var/tmp folders are for?
Yes, it looks like /var could get filled up quickly because it has mail and logfiles and other stuff in it.

Forget what you've heard or read about /tmp, /var, /whatever... unless you're installing a server or are using the system for high-end gaming, all you need is **/**, **swap**, and **/home** (10-12Gigs for /, twice your RAM for swap, and the rest for /home). 

With most modern systems running 2Gigs of RAM and higher, whether you even need a swap partition is open for debate (Word to the wise: Use a swap partition)... for the average, everyday use of a laptop or desktop, swap is recommended at twice your RAM.

Run some Google queries for the use of the various other partitions... but again, not needed for normal use of a system.

---

### Post by shaggy999 on 2009-11-28
> **Captain_tux said:**
> Forget what you've heard or read about /tmp, /var, /whatever... unless you're installing a server or are using the system for high-end gaming, all you need is **/**, **swap**, and **/home** (10-12Gigs for /, twice your RAM for swap, and the rest for /home). 

With most modern systems running 2Gigs of RAM and higher, whether you even need a swap partition is open for debate (Word to the wise: Use a swap partition)... for the average, everyday use of a laptop or desktop, swap is recommended at twice your RAM.

Run some Google queries for the use of the various other partitions... but again, not needed for normal use of a system.

+1

There's a lot of bad information in this thread. For desktop use you really only need seperate partitions for /, /home, and swap at the max.

/ - 15G-20G is more than enough. I rarely hit 10G even with a ton of apps installed.
swap - If you use the hibernate function then you need as much swap space as you have RAM at the minimum. But if not I question the need for swap at all if you're not doing memory-intensive apps like 3D modeling/major gimp work/video editing/etc and you have 2+GB.
/home - This gets all of your leftover space because all your programs will save your personal files to your home directory.

For informational purposes /var usually contains information that is volatile and somewhat temporary like log files, apt cache, etc. /opt is a usual install location for custom programs that are outside of the distribution (for example, applications that you compile yourself). /usr is for "unix system resources" and is where most system libraries/help documentation/system programs/etc are stored. /tmp is for all users to store temporary files and /boot is for boot files. /etc contains all of the system configuration files for all of the programs.

Another thing to look at is "linux volume management". Using lvm2 as a middle layer between the hard drive and the partitions it can allow you to easily resize partitions at a later date if need be. But that's kind of more complicated to set up.

---

### Post by Captain_tux on 2009-11-28
Well said, Shaggy... and thanks for the info on the other partitions!

---

