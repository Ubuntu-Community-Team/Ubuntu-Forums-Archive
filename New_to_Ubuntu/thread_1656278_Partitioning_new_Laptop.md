---
title: "Partitioning new Laptop"
date: 2010-12-30
forum: New to Ubuntu
---

### Post by sdalgl72 on 2010-12-30
I plan on buying a new Laptop for Ubuntu only.  I was wondering if you guys could give advice on partitioning the HDD.  I would probably get something with about 3/4 gig of RAM and 500GB hard drive.

Would you put the home directory on a different partition and if so how big would it be?

How big would you have the root directory?

How big would you have the swap?

Also would you encrypt the home directory?

---

### Post by Drenriza on 2010-12-30
Regarding to put the home directory on another partition than the rest of a system, can i only see useful if you want to separate the (I/O) traffic.

My own swap is on 6.09 GB. Not that i ever use it. With 4 gigs of ram, i have plenty for ubuntu and what i use it for. (internet, work, HoN)

If you want to have your things in private in the event of your laptop gets lost or stolen, i can see an idea in encrypting the home folder. I encrypt my whole HDD, but this is because i have sensitive work related documents on it.

Their is a few tricks you can do in the event you want to backup the system, where partitioning can be a little helpful. But i wodent use alot of time on it. I went with the option (use the whole hdd)

---

### Post by TeoBigusGeekus on 2010-12-30
My go:
1(.5?)gb for swap
20gb for root
50gb for home (different partition of course)
The rest for data,torrents, etc.
I'd not encrypt anything.

---

### Post by sdalgl72 on 2010-12-30
@DrenrizaThanks for your reply.  I might just go with use whole drive and not bother with setting the partitions myself then.  Just out of interest if you encrypt your home directory then why would you need to encrypt the whole drive?

As all your documents and stuff would be in home surely?

@TeoBigusGeekus wouldn't you store torrents and data in the home directory?

---

### Post by perspectoff on 2010-12-30
More than 2 Gb swap is a waste and is never used. 

There are many programs that store user files in directories other than /home.

Many create subfolders in /usr or /var or even /etc subfolders.

If you are the only one using the laptop, though, what do you care if it is encrypted or not?

Only your folder with passwords and bank account info need be encrypted, really.

---

### Post by TeoBigusGeekus on 2010-12-30
> **sdalgl72 said:**
> @TeoBigusGeekus wouldn't you store torrents and data in the home directory?

I personally keep all my settings, scripts and documents in my home folder - I have a special partition for movies and music.
I suppose I could keep everything in my /home folder, without a separate data partition, but... I don't know... it feels tidier that way. ;)

---

### Post by srs5694 on 2010-12-30
> **sdalgl72 said:**
> I plan on buying a new Laptop for Ubuntu only.  I was wondering if you guys could give advice on partitioning the HDD.  I would probably get something with about 3/4 gig of RAM and 500GB hard drive.

If by "3/4 gig of RAM" you mean ~750 MB of RAM, then that's ridiculously small by today's standards. I suspect you mean "3-4 gig of RAM," as in 3 GiB or 4 GiB. That's more typical today.

> Would you put the home directory on a different partition and if so how big would it be?

Yes, create a separate /home partition. IMHO, Ubuntu does it wrong by not doing so by default. Using a separate /home partition has significant advantages, including:


[list]
[*]Certain re-installation and upgrade methods require wiping the root (/) partition. Keeping /home separate means that you can do this without backing up your user data.
[*]Similar to the previous reason, you can more easily switch from one distribution to another if you so decide by keeping a separate /home partition.
[*]You can use different filesystems on the different partitions -- for instance, ext3fs for root (/) and XFS for /home. This may not be important to you, but it may be; and if you keep them separate from the start, you'll be able to go this route if you decide to do so in the future.
[*]Some backup tools work on whole partitions. Keeping system files (in the root partition) and user files (in /home) separate means you can back them up separately using such tools.
[*]You can provide access to /home to a non-Linux OS without risking your Linux installation itself.
[/list]


You may not care about some of these issues, but if nothing else, the first one alone makes a separate /home partition worthwhile in almost all cases, IMHO.

As to the size issue, see below....

> How big would you have the root directory?

How big would you have the swap?

These days, the equation goes like this for a 3-partition (root/swap/home) setup:


[list]
[*]**root (/)**: 5-20 GiB, depending on available disk space and how much software you plan to install
[*]**swap**: 1-2x the computer's RAM size (see below)
[*]**/home**: The rest of the available space
[/list]


Concerning swap, it's not as useless as some have suggested, particularly on a laptop. Swap is used by the suspend-to-disk (aka hibernate) function, so if you ever want to use that function, having at least as much swap as RAM is necessary. Swap is also used if you have some unusual demand on RAM for some reason -- a need to run an unusual number of programs, a program with a memory leak, etc. Given that we're talking about a few gigabytes on a 500 GB disk, creating a big enough swap partition is not a big price to pay.

You might also consider setting aside an unused partition of the same size as your root (/) partition. This will enable you to install and test a new version of Ubuntu or another distribution entirely relatively painlessly.

> Also would you encrypt the home directory?

*I* wouldn't bother, but that's just me -- I don't store sensitive data on my laptop. You'll have to decide for yourself how sensitive your own data are and how likely it is that your laptop will fall into the wrong hands.

---

### Post by sdalgl72 on 2010-12-30
Thanks for the detailed reply I was referring to between 3 gig and 4 gig of RAM sorry for any confusion

---

