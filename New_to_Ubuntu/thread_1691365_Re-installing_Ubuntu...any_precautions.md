---
title: "Re-installing Ubuntu...any precautions?"
date: 2011-02-19
forum: New to Ubuntu
---

### Post by Procreate on 2011-02-19
I'm gonna re-install Ubuntu as I think I've messed up some settings and installed a lot of unnecessary applications. It's no longer running as it did the first few days I've had it.

So what I plan to do is...boot from the LiveCD (Ubuntu 10.10), select "use the entire disk" and just install as regular.

Are there any precautions I should take before doing a clean re-install?
I don't need to keep my settings, nor backup any files- those don't matter to me.

---

### Post by lightningfox on 2011-02-19
There are no precautions, the way you described will work fine.

---

### Post by Old *ix Geek on 2011-02-19
Sounds like you're good to go since you don't have to worry about saving settings and/or data.

I've never used the default, "use entire disk" method of installing. My only suggestion would be that if you want more control over how the disk is allocated, go with the manual partitioning option. That way you can choose how much space to allow for each partition; you can also choose how many partitions you want.

I'm such a creature of habit I can do my default installation in my sleep:

/
/home
/data
swap

Where / is relatively small, /home and /data are big, and swap is a reasonable number.

---

### Post by Procreate on 2011-02-19
> **Old *ix Geek said:**
> Sounds like you're good to go since you don't have to worry about saving settings and/or data.

I've never used the default, "use entire disk" method of installing. My only suggestion would be that if you want more control over how the disk is allocated, go with the manual partitioning option. That way you can choose how much space to allow for each partition; you can also choose how many partitions you want.

I'm such a creature of habit I can do my default installation in my sleep:

/
/home
/data
swap

Where / is relatively small, /home and /data are big, and swap is a reasonable number.

What are the benefits of partitioning when installing? Can I partition later on or is it only at the time of installation?

---

### Post by deconstrained on 2011-02-19
> **Procreate said:**
> I'm gonna re-install Ubuntu as I think I've messed up some settings and installed a lot of unnecessary applications.
This is not a sufficiently good reason to spend the time completely reinstalling Ubuntu, in my opinion.

You can look for the software you no longer want by opening Synaptic and doing a word search for them. Then, select the relevant packages, right click and select the action "mark for complete removal", which will do exactly the same thing as an 'apt-get purge', which removes both the software and the affiliated configuration files (I believe it also removes the package from apt's cache).

To clear up some space, run 'sudo apt-get autoremove' and then 'sudo apt-get clean' to clear your package cache. That, and/or run 'computer janitor' found in the menu under System->Administration.

If the settings you've messed up are core system settings in /etc, here's what you can do to find out exactly where you messed up:
```
sudo -i
```
THEN: pick a time before which your system was working properly, and:
```
touch -d [date] ./timefile
```
Where [date] is a string (enclose it in single quotes to be on the safe side). See the manual page of touch for more details ('man touch')
Then: 
```
find /etc/ -anewer ./timefile
```
That should print a list of files that were accessed/modified later than the timestamp that you put in 'timefile', and you can then go through them and look for mistakes.

> **Procreate said:**
> What are the benefits of partitioning when installing? Can I partition later on or is it only at the time of installation?
You can resize your partitions after installing, provided you didn't format your partition with a filesystem like JFS that can't be resized, **but:** if you delete/re-create the partitions your entire system and its data will be lost. The main advantage of partitioning once is that resizing partitions takes time and could nuke all your data if you aren't careful.

---

### Post by Kixtosh on 2011-02-19
One of the major benefits that I can think of is having a separate /home. This means that if you ever need to install again, of if you just want to try different variants of Ubuntu (and/or Linux in general) to figure out what you prefer most, your documents should be secure in your home folder and won't be wiped off the disk during the installation process.

---

### Post by Old *ix Geek on 2011-02-19
> **Procreate said:**
> [QUOTE=Old *ix Geek;10474828]Sounds like you're good to go since you don't have to worry about saving settings and/or data.

I've never used the default, "use entire disk" method of installing. My only suggestion would be that if you want more control over how the disk is allocated, go with the manual partitioning option. That way you can choose how much space to allow for each partition; you can also choose how many partitions you want.

I'm such a creature of habit I can do my default installation in my sleep:

/
/home
/data
swap

Where / is relatively small, /home and /data are big, and swap is a reasonable number.

What are the benefits of partitioning when installing? Can I partition later on or is it only at the time of installation?[/QUOTE]For all practical purposes, you can only partition at installation. (You CAN do it later, but then you'll be looking at losing data.)

There are several benefits, not the least of which is learning more about your system! By taking control of things like how many partitions there are, what they're named, how big they are, etc., you get to feel like you're in charge--not the OS. :) But in practical terms, the above allows you to make the pertinent decisions, such as keeping one or more partitions for user data--so you don't lose anything when you upgrade the OS or even do a clean reinstall (which generally is unnecessary in the Linux world).

If you'd like, post the size of your hard drive and then wait for input on how best to divvy it up during the partitioning process. Or just go ahead with the 'whole disk' method if you'd prefer.

---

### Post by Procreate on 2011-02-19
Thanks for the input, all. :D

I'll try the command lines and see if I can find out anything about where the files got screwed.

As for the partitioning, I'm limited to 60GB of HD. How should I partition?

I remember reading for:

swap = 2x your RAM (which in my case would be 2GB of RAM, so 4GB)
/ = 20GB
/boot = 500MB
/home = whatever's leftover (~35 GB)

How do these numbers look?

---

### Post by fabricator4 on 2011-02-19
> **Procreate said:**
> What are the benefits of partitioning when installing? Can I partition later on or is it only at the time of installation?

Partitioning is part of the installation process.  It's part of setting up the file system, namely, somewhere to put it. :-)

The suggestion to make a separate home directory is a good one, since all your personal data and settings reside in /home. If you want to upgrade or reinstall later you can do so without formating the home directory, just tell the installer to mount it as /home again.

You don't have to partition all of the hard drive if you don't want to, leaving some for later to put another ubuntu release or even another operating system entirely (except windows which likes to have 1st primary partition as it doesn't acknowledge that any other OSs might be on the same computer).

Boot the live CD, then run Gparted out of system/administration.  Delete any existing partitions then set it up how you want.

Currently I have a 30 GB partition for Ubuntu / (root), and the rest of my hard drive for /home.  Others may prefer even more partitions such as /var /usr etc. Have a look at [this primer]("http://guides.radified.com/magoo/guides/linux/linux_partition_explanation.html") for more information.

You'll also need to make a swap partition.  This should be at least as big as your RAM size.  Some say twice as big if you use suspend on your computer.  I have a small swap on my Eee PC and it works OK, but care is required.

My hard drive looks like:
```

| 30 GB primary ext4- mounts as / | 100+ GB ext4 mounts as /home | 1024 MB swap | 

```

Now run install and when it give you options for the install, select manually set partitions, just make sure that you select which ones are to mount as /, /home etc.


Chris

---

### Post by Kixtosh on 2011-02-19
> **Procreate said:**
> ... I remember reading for:

swap = 2x your RAM (which in my case would be 2GB of RAM, so 4GB) ...I've read that rule myself too, but I believe that after a certain point, there's no need to follow it. 

I have two laptops with a 60 GB drive, like yours (although both share that drive for dual boot purposes, so in reality, Linux only gets half of that space to itself, or less ... Windows can be very greedy sometimes!). Using a default installation, the first laptop, with 1.28 GB of RAM, was allocated just 884 MB of swap. The second laptop, with 2.05 GB of RAM was allocated just 1.3 GB of swap by default during the automated installation process. That's less than the total RAM available for swap, and both work very well. They are completely stable, and suspend normally. 

Of course, in general usage, neither of those laptops is ever near the limit of RAM available, and the System Monitor rarely shows more than just a few percent of swap being used. To illustrate this: right now, laptop 1 is using 33% of RAM, and 0.2% of swap; laptop 2 is using 9.6% of RAM and 0.0% of swap. So, 4 GB of RAM sounds like a waste of space to me (but others may advise you differently).

---

### Post by deconstrained on 2011-02-19
> **Procreate said:**
> As for the partitioning, I'm limited to 60GB of HD. How should I partition?

I remember reading for:

swap = 2x your RAM (which in my case would be 2GB of RAM, so 4GB)
/ = 20GB
/boot = 500MB
/home = whatever's leftover (~35 GB)
Unless you want to install some heavy programs, like Matlab or VMware, you're probably never going to use more than about 12 GB for Ubuntu. Heck I ran it on a netbook I owned for a while on a 5 GB root partition, though I had to clear the cache to make room whenever I ran a release upgrade.

Personally, I'd just make one boot partition and one root partition, unless you plan on experimenting with other distros, and don't routinely make backup copies of your home directory (which is not a good thing anyway; backup backup backup). Also, 120-300 MB is more appropriate for boot; just uninstall the kernels/kernel images that you're not using when it gets full.

---

