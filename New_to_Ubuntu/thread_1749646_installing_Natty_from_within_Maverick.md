---
title: "installing Natty from within Maverick"
date: 2011-05-04
forum: New to Ubuntu
---

### Post by Jmob on 2011-05-04
So, I'm only a few months into linux, been learning slowly but haven't really been digging.  I'd been using a dual-boot scheme w/W7 and Maverick that was working fine, but I just wiped Maverick and reinstalled.  I shrank the w7 partition beforehand, and installed more intelligently (I'd made multiple partitions before but didn't properly set a different one as /home, plus my swap was too small (maybe?  How big swap for 4gb ram?).  Anyway, it was easiest to just make more space overall and set partitions manually.  I made 8gb for swap, 10gb for /, and the rest for a bit /home partition.  So far, so good.

Here's the thing: I also want to install Natty to try it out, but I don't want to replace maverick.  I've already got a separate 10gb (logical) partition to put it on, but I'd like to do it from WITHIN my main ubuntu program, rather than just running the autoloading installer from the liveCD.  I just want to learn how, is all.  But that's where I realize I'm a newbie, since I really don't know where to start.  I considered the startup disk creator, but it only sees the whole 500gb hard drive, not the partition.  Anxious about overwriting things.)

Anyone able to give me some direction?  I'd also like to use the same /home for the different versions, if possible.  I've heard conflicting reports of whether this works, but regardless, I still want to do the install w/o wiping my data on /home.  Again, any direction? 

I really appreciate it.

---

### Post by dniMretsaM on 2011-05-04
You could use a virtual machine. No partitionng or anything like that. Your computer should run it fine with 4GB of RAM. I would recommend VirtualBox (don't ge the one from the repositories, it has no USB support), but I've heard good things about VMware. Not sure if you could use the same ~/ partition or not in a VM, though.

---

### Post by Dr. Nick on 2011-05-04
In a virtual machine you cant share the home, technically if you install natty to a partition you can share the same home, however all the programs config files are store in /home and since each distro will have a different version of each program that will get real messy real fast and will likely create issues that will drive you crazy.

8 GB swap is probably overkill, but if you have plenty of HD room them it really does not matter, I heard 1.5 times the physical mem for swap, but that was back when 512mb was a lot of memory and 1gb was "insane" lol. With 4gb you could probably do without any swap if you wanted.

If you want to run the install from within Maverick you will need to learn how to use "chroot" I imagine it is possible to install natty to a new partition from within maverick using chroot, not sure exactly how or why you would want to though; except to prove it can be done. If you just want to test it a live CD is probably your easiest and safest bet

[Here]("https://help.ubuntu.com/6.10/ubuntu/installation-guide/i386/linux-upgrade.html") are instructions, but they are 5yrs old so it may not work

---

### Post by Jmob on 2011-05-04
Hey, thanks.

Yep, Dr. Nick, you're pretty much spot on.  Mostly, I just want to do it so that I'll know how.  But that's at least partly because doing so makes me work with several areas I'm learning, partitions, installations, directing mount points, etc., that I want to know better.  I'm more interested in that than Natty itself, to be honest.  

But maybe it's also that it just seems strange to me that it would be otherwise.  Linux is largely about flexibility and capability with the right knowhow, knowhow you're supposed to develop.  And so it just seems strange when the best way to get a new Ubuntu partition up and running is to LEAVE Ubuntu, or at least to go over to a pre-made, limited-case version on a CD.  I mean, I can easily install Ubuntu from Windows now, but not Ubuntu itself?  I get it, yeah, but it's still a bit strange.

If that perspective is wrong, and it's not done because it's not the best solution, then fine.  But maybe you can see why I might go in thinking that way.

I'll look into chroot.  Might not do it, but knowing about such tools is the kind of growth I want.  

on /home stuff: I'd heard about the config problem...but is there a way to keep that stuff (that's unique to each distro) separate while keeping a common pool of my data?  Preferably without drastically reinventing the native structure?  

on swap: yeah, I'd heard that.  On Windows, I'd even heard that past a certain RAM threshold you get better performance without it.  Perhaps I should partition that space for something else?  Any recommendations?

---

### Post by Dr. Nick on 2011-05-04
You could repartition part of swap and use it as a common ground between distros to share files, Technically if you had 2 separate login names (1 for each) you could use the same /home partition and you would just two folders /home/user1 and /home/user2. Not sure if that would cause permission problems though if you were to copy between them. That should be able to workaround though.

The link I gave earlier should be able to be modified to install from a chroot, I use to be into these "odd" install scenarios before the made a installer from USB, I hated burning tons of CD's and some of my computers would not boot from a CD so I did alot of network type installations by editing grub to boot into an installer on a pre made partition; but haven't done it lately. I think it is just a bit involved for a new person and thats why its not real popular, for people that know all about partitions, mounts etc its not terribly confusing, but it would be a lot to throw at someone who is only use to windows or just installed from the live cd and didnt have to mess with those things.

I understand your reasoning though, maybe they do not expect the average user to run 2 different versions of the same OS since their is not really any problem with backwards compatibly. Maybe they think providing the ability to upgrade from within is sufficient enough.

If you decide to give it a try good luck and have fun, sometimes its fun to do things just to prove it can be done.

---

### Post by beew on 2011-05-04
If you have a spare external hard drive you can install 11.04 in it and boot it from your computer (or any computer for that matter, as long as the hardware is compatible)

It is a full install so it has the same performance and operating conditions as an internal install but it would not change anything of your internal hard drive.

---

### Post by beew on 2011-05-04
> **Jmob said:**
> Hey, thanks.


on /home stuff: I'd heard about the config problem...but is there a way to keep that stuff (that's unique to each distro) separate while keeping a common pool of my data?  Preferably without drastically reinventing the native structure?  

on swap: yeah, I'd heard that.  On Windows, I'd even heard that past a certain RAM threshold you get better performance without it.  Perhaps I should partition that space for something else?  Any recommendations?

Instead of having a shared /home using some mojo I would recommend separate /home partitions if you choose the internal install route (i would prefer installing in an external drive) You can access each Ubuntu's /home from another Ubuntu anyway so it doesn't matter whether you put all the data in the same parrtition or not (it wouldn't be the case if you say, dual boot Ubuntu with Fedora) It is much cleaner to have separate /homes so settings don't get mixed up.  Some people would like to have two small /home partitions with a common data partition, but since it seems eventually you will go back to one Ubuntu (either getting rid of 10.10 or 11.04) this doesn't seem to make sense.

The important thing to decide is which Ubuntu do you want to control grub. If you want 10.10 to control it then install the bootloader for 11.04 in the partition where the OS is installed instead of the drive (so if the / partition for 11.04 is installed in sda2, install grub in sda2 instead of sda. You have choice of where to install grub if you choose manual partition (advanced option?0 when you install 11.04.

---

### Post by Jmob on 2011-05-06
Thanks for the info, everyone.

I have to admit I'm a bit confused by the picture you're painting for choice of bootloader location.  What does it mean here to "control grub"?  On my current install, I've got 10.10 on sda6, bootloader on sda, directing to 10.10 or w7.  What would installing it into another partition (sda7, say) accomplish?

Maybe it's a terminological thing: grub IS the bootloader, yes?  Or am I missing a nuance?

Sorry for being so confused.  Usually I can infer more and figure things out, but I'm obviously lacking some knowledge here.

---

### Post by QLee on 2011-05-06
[QUOTE=Jmob]...
Maybe it's a terminological thing: grub IS the bootloader, yes?  Or am I missing a nuance?
...[/QUOTE]

Probably missing a nuance, that would be easy to do with GRUB because people usually just write grub in a post when they might be referring to the bootloader generically, or to the portion of the bootloader that is written to the MBR, or what is written into /boot, or to the GRUB shell. Sometimes we even have to ask if a poster means GRUB (legacy GRUB) or GRUB2 (which is really grub-pc), so if you have some confusion that would not be unreasonable.

Beew has given you a sane approach. What is meant by "control" is using one (and only one of the installs) to update and provide the boot menu for the system. It is good advice. [Edit] One thing I might do differently would be to not install the bootloader (to MBR or partition) on the install that you choose to be the "test" install. But it would work the other way too.

---

### Post by beew on 2011-05-06
> **QLee said:**
> One thing I might do differently would be to not install the bootloader (to MBR or partition) on the install that you choose to be the "test" install. But it would work the other way too.

I would  prefer that too but Ubuntu 11.04 (or Ubuntu since 10.04?) doesn't have the option of not installing the bootloader. In my dual boot with Fedora I chose not to install the bootloader for Fedora like you say.

---

### Post by Jmob on 2011-05-12
Thanks, everyone.  This has been useful.  I'm still trying out the LiveCD first, though.  Or at least I would be.  Now, I have to go post something else asking why I can't even get a liveCD of natty to run on either of the available Thinkpads I have, from CD or USB.  Oh well.

---

### Post by wildmanne39 on 2011-05-12
> **Jmob said:**
> Thanks, everyone.  This has been useful.  I'm still trying out the LiveCD first, though.  Or at least I would be.  Now, I have to go post something else asking why I can't even get a liveCD of natty to run on either of the available Thinkpads I have, from CD or USB.  Oh well.

Hi, I also wanted to get more understanding of setting up linux from scratch so I installed gentoo in virtualbox from the ground up and believe me it was a challenge. I use my ubuntu but I do have a fully working gentoo now I just do not use it. I just wanted to know I could do it.

---

### Post by Jmob on 2011-05-13
Interesting.  Any particular tips stemming from the experience?

---

