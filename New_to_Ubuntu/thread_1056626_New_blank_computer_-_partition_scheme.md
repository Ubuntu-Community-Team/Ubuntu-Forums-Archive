---
title: "New blank computer - partition scheme?"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by Kellemora on 2009-01-31
Hi Gang

I know, I know, I've set up 6 computers already, but that don't mean I learned much. 

NEED SUGGESTIONS on a GOOD Partition Scheme here.

WHY am I asking?

When I originally set up Ubuntu Hardy for the first time, Here is what was suggested from the WIKI on Partitioning.

Suggested - Actually Needed or currently USED
/ 250 Mb - 12 Gb
/usr 500 Mb - 2.2 Gb
/var 3 Gb - 400 Mb
/tmp 100 Mb - 70 Kb
swap 1 Gb - 2 Gb
/home 65 Gb (on a separate partition)

As you can see from the above, I've had to go into GParted several times to keep INCREASING the amounts used over the suggestions, except for home which actually holds fairly little since I have a Data File Server.

The new computer is an Asus MOBO, dual core AMD 5200, 680 watt power supply, 500 Sata 3g, way overkill considering.  Will NOT be dual boot, for Ubuntu ONLY!
Have added NOTHING, not even a CD to this computer yet!
Anything I should KNOW about a BLANK NEW Computer would be welcomed also!

What SIZE should I make ROOT and the rest too, to insure it and they don't run out.  
Here are my thoughts:

sda1 / 50 Gb (root) (boot)
sda2 Extended
sda3 /home 250 Gb
X sda4 /var 2 Gb
X sda5 swap 4 Gb
X sda6 /tmp 1 Gb
X sda7 /usr 20 Gb  (it's down here so I can extend into unallocated if needed)
175 Gb +- Unallocated

Also, should I use the 64 bit version of Hardy because of the dual core CPU?????

Thanks
TTUL
Gary

---

### Post by k3rnelmustard on 2009-01-31
Why in the world do you need that much swap?  How much RAM do you have?  That's one thing that's totally deprecated but no one feels like fixing, is the suggested swap size.  If your system ever swaps out 2GB much less 4GB you're in serious trouble for other reasons, and having that much swap won't fix it.  I would say just to have enough swap to make system that rely on it happy.  Like, 512MB or maybe even 256.

Other than that, I've never really understood the whole /usr, /var and /tmp on separate partitions thing, the only time I've seen that be useful is when they're mounted in to ram either straight-up or using something like AUFS.  But to each his own.  Any particular reason for doing that?  It's just that if you do that now, you're limiting potential activity in the future.

I definitely agree with /home on a separate part though, makes changing distributions or architectures way easier if you ever do!

Just my $.02 worth of (probably) useless bantering.

---

### Post by anjilslaire on 2009-01-31
On my desktop (not a server, I know) I go with:
10gig /
2 gig swap
the rest as /home

This way, I create any data directories under /home like 
/home/multimedia/
/home/backups/
etc.

It allows a simple partition structure with enough space to install apps in the OS under /,  and enough space to store everything else , including user directories abd data. Also, your data is safe when you reinstall the OS, leaving /home alone.

---

### Post by handydan918 on 2009-01-31
> **Kellemora said:**
> 
What SIZE should I make ROOT and the rest too, to insure it and they don't run out.  
Here are my thoughts:

sda1 / 50 Gb (root) (boot)
sda2 Extended
sda3 /home 250 Gb
X sda4 /var 2 Gb
X sda5 swap 4 Gb
X sda6 /tmp 1 Gb
X sda7 /usr 20 Gb  (it's down here so I can extend into unallocated if needed)
175 Gb +- Unallocated

Also, should I use the 64 bit version of Hardy because of the dual core CPU?????

Thanks
TTUL
Gary

> **k3rnelmustard said:**
> Why in the world do you need that much swap?  How much RAM do you have?  That's one thing that's totally deprecated but no one feels like fixing, is the suggested swap size.  If your system ever swaps out 2GB much less 4GB you're in serious trouble for other reasons, and having that much swap won't fix it.  I would say just to have enough swap to make system that rely on it happy.  Like, 512MB or maybe even 256.

Other than that, I've never really understood the whole /usr, /var and /tmp on separate partitions thing, the only time I've seen that be useful is when they're mounted in to ram either straight-up or using something like AUFS.  But to each his own.  Any particular reason for doing that?  It's just that if you do that now, you're limiting potential activity in the future.

I definitely agree with /home on a separate part though, makes changing distributions or architectures way easier if you ever do!

Just my $.02 worth of (probably) useless bantering.

agree with the mustard colonel re: swap. more isn't always better. 
As regards your basic partitions:
sda1 / 50 Gb (root) 10-12 GB should be more than ample. (boot) I would consider adding a separate /boot partition. Old school unix trick, but it can make reinstalls easier.
sda2 Extended
sda3 /home 250 Gb nothing wrong with this, but consider the use of a separate symlinked /data partition with a smaller /home. Again, makes backups and reinstalls easier. 
X sda4 /var 2 Gb A separate /var is a good idea in the event of a system problem that generates massive logfiles....but 2GB may be overkill. That is a LOT of text. You won't live long enough to parse it.
X sda5 swap 4 Gb Meh. 1 or 2 GB tops.
X sda6 /tmp 1 Gb This is a better place for a large partition, in case you want to copy large files.
X sda7 /usr 20 Gb  (it's down here so I can extend into unallocated if needed) What's gonna swell /usr by that much?


Pure opinion. Just like the lower extremity of the alimentary canal. Everybody has one, and they all stink.

:popcorn:

---

### Post by Kellemora on 2009-02-01
Hi Gang - Thanks for the input!
Although I've kept these old beasts running for years, I've never built a computer by myself completely from the ground up.  Still trying to figure out where to plug things into, hi hi......

For Kernel Mustard in the Den with a Knife.  Historically one made a Swap file double the size of memory up to 2 gig, then equal to memory.  I have 4 gigs of DDR2 memory (most this board will hold).  It probably wouldn't use that much swap for anything.  Except I do burn a lot of CD's, which could be in /tmp and I listen to streaming audio, have no idea where that hides either.

The reason for separate /usr /var /tmp was due to multiple users and Mailboxes, etc.  If each person gets spammed with 1,600 pieces of mail per day, that takes up space.

For Anji - My ROOT is ALREADY at 12 GB, have no idea why either, unless it's all these upgrades.  Some machines are around 7 to 9 GB.

Hi HandyDan - I had a symlinked data system before I built a new Data File Server last month (NOT a File Server file server, just data).  So technically a 40 to 80 gig hard drive would have been overkill on this new machine.  500 gig Sata 3g is like sending in the Marines for a squirrel in the attic! 
I will take your advice and make /tmp bigger 4 or 5 gigs.
I have NO idea why /usr is so bloated.  I went from the suggested 500Mb up to 1gig, then up to 1.5gig, then to 2gig and most recently I kicked that puppy up to 5 gig so I could quit changing it every 3 to 5 weeks.  WHY the suggested /var was 3Gb is beyond me.....  I just followed the WIKI and it's not right!
I'll use your Separate Boot idea also.

Instead of being SHORT on HD space as in the old days.  Since building the new Data File Server, I have about a terrabyte of unused drive space around here not, and adding a 500 gig Sata to the new computer was really totally unnecessary.  The ONLY reason I did was because I NEED the IDE slot to run a CD for loading the computer up and a multi card reader.  That leave ZERO connectors for another IDE, and I've heard Sata 3g is FAST.
I may use IT for my Data File Server and the File Server for the mirror and move the mirror to offsite redundant backup.

FWIW:  I've left everything except /home and swap on a single partition on a couple of other machines and that works out OK too!  When I first started, I let Ubuntu use the whole drive and moving HOME later is a royal PITA.

Thanks Guys!

One more question though!
If I left /var and /tmp in the / partition and allocated more space there, would it just fill the space as needed?  I could just leave /usr in there too I supposed.  And not have to deal with how much space each individual partition received.

TTUL
Gary

---

### Post by louieb on 2009-02-01
> **anjilslaire said:**
> On my desktop (not a server, I know) I go with:
10gig /
2 gig swap
the rest as /home

This way, I create any data directories under /home like 
/home/multimedia/
/home/backups/
etc.

It allows a simple partition structure with enough space to install apps in the OS under /,  and enough space to store everything else , including user directories abd data. Also, your data is safe when you reinstall the OS, leaving /home alone.

:KSHey I like that. One partition simpler that what I usually do - create a separate data partition and mount it on /media/stuff.

---

### Post by Bölvaður on 2009-02-01
I have adopted a scheme posted on this forum.
place	rough size
/	12 GiB
/data	100 GiB
swap	1.5 GiB


The reason I have /data but not /home is that /home has config files from various programs, which may not help if you have more than 1 distro, or if you want easy way to upgrade to next release with no fuzz at all.

swap doesnt need to be big, may depend on what you are doing, but I never use swap on my desktop at all. But I sometimes hibernate the laptop so I need equally big swap as my ram on there.

---

### Post by Mud.Knee.Havoc on 2009-02-01
> **anjilslaire said:**
> On my desktop (not a server, I know) I go with:
10gig /
2 gig swap
the rest as /home


This is almost exactly my setup, except since a $50 hard drive is so huge now, I go a bit overboard:

20GB  /
2GB swap
the rest as /home

This is great because I can install every new release of Ubuntu and Debian by formatting /

---

### Post by anjilslaire on 2009-02-01
> **louieb said:**
> :KSHey I like that. One partition simpler that what I usually do - create a separate data partition and mount it on /media/stuff.

I've also added a 2nd hard drive, that's mounted as /media/multimedia/ so I agree, but this was started as a single drive discussion.

and yes, var, usr, etc will all go in under / automatically

---

### Post by k3rnelmustard on 2009-02-01
> 
FWIW: I've left everything except /home and swap on a single partition on a couple of other machines and that works out OK too! When I first started, I let Ubuntu use the whole drive and moving HOME later is a royal PITA.

Thanks Guys!

One more question though!
If I left /var and /tmp in the / partition and allocated more space there, would it just fill the space as needed? I could just leave /usr in there too I supposed. And not have to deal with how much space each individual partition received.


Right, that was my only point with the whole making them separate partitions.  Unless you have a particular reason to, you'll have to determine how much space they need and hate yourself when it's off and you have to re-partition.  Also, I understand that historically swap is 2x RAM, but I think that thinking is quite antequated, I guess if you use hibernate it could be useful, I don't, so that didn't occur to me.  Beyond that, it's just a waste of hard-drive space.  Your cd-burning activity is in /tmp, as you said, which unless you mount /tmp into ram (as some do for performance reasons) burning cds wouldn't make it want to write to swap that I know of.  If someone knows better about that, correct me.

The only thing that I think is weird is that ubuntu doesn't suggest/enforce/allow /boot on a separate partition.  My primary system is gentoo, and having /boot on a separate partition is one of the first things I tell people to do when installing gentoo.  I tried to set it up on ubuntu once, but if you make it noauto in the mount options, (which is the whole point of having /boot on a separate part) it's like it doesn't know it needs to mount it when you install a new kernel.  This was, however, at least 3 or 4 ubuntu versions ago.  Has anyone had reliable success with an ext2 noauto mounted /boot partition in ubuntu recently?

---

### Post by handydan918 on 2009-02-01
> **Kellemora said:**
> 

One more question though!
If I left /var and /tmp in the / partition and allocated more space there, would it just fill the space as needed?  I could just leave /usr in there too I supposed.  And not have to deal with how much space each individual partition received.

TTUL
Gary
This issue is one good reason to put /var (and /tmp, too, maybe) on their own partition. 
/var is used mostly for logging system events. If something goes sideways and starts throwing log entries, /var can get big over the course of a day or two. If it's on / (root) it can result in a self imposed denial of service, via a full root partition....not good. If it's on it's own partition, then when it's full, it stops taking new entries, but the system stays up! Better, in my view.

---

### Post by anjilslaire on 2009-02-01
Or, you could just occasionally empty /var if needed. Mine is currently ~703mb. I've always used about 10gig for /, and hav never gotten it near being full.

---

### Post by Kellemora on 2009-02-01
Hi Gang

Thanks for all the info!!!!!

I decided to go with fairly simple
root 50 gig
extended
swap 2 gig
/home rest of drive
home and swap are inside of extended.

But I hit a super major problem that I will post about separately.
gparted worked to partition, THEN after everything was up and running, not only does it show the drive as unallocated, just merely booting into gparted wipes out the MBR, so I have to use Super Grub to get it back.

TTUL
Gary

---

