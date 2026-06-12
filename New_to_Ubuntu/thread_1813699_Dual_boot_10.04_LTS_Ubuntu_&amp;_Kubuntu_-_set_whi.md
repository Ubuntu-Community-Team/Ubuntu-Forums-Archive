---
title: "Dual boot 10.04 LTS: Ubuntu &amp; Kubuntu - set which first?"
date: 2011-07-28
forum: New to Ubuntu
---

### Post by scruffyeagle on 2011-07-28
Hi!

What I've done so far:
I've downloaded, md5'ed, burned, & verified disks for both Ubuntu & Kubuntu; both, in the 32-bit v10.04 LTS versions.

What I intend to do:
I intend to install both Ubuntu & Kubuntu on the same machine, for the sake of "living with" each of them for a while. Then, eventually, I'll probably make up mind which I like best, followed by re-partitioning to make the disposed of one's space be turned into personal data space.

How I hope to do it:
I intend to re-partition the 60 GB HD in a Dell Inspiron 9400 laptop as:
1)  2 GB swap,
2) 20 GB OS,
3) 20 GB OS,
4) 18 GB home partition.

Questions I need answered:
1) Will Linux let me set all 4 as primary partitions, or am I limited to 3 primaries as in Windows?
2) Can I place the swap as partion #1, or am I required to make partition #1 bootable?
3) Given 2 partitions for OS's, is there a most beneficial order for installing & placement of Ubuntu & Kubuntu? (I say it that way, because for example it might be best to load Kubuntu first into the 3rd partition.)
4) Is 20 GB per OS overkill, or could I easily get by with half that and never run out of OS programs storage space?
5) Is 2 GB enough for the swap, or would the OS's work more efficiently if given more?
6) Will there be difficulties re. ownership of personal data files in partition #4, re. files that were created while using Ubuntu & Kubuntu?

I realize I've thrown out a lot of question here. But really, it's all stuff I need to know. I'd appreciate any advice or insight you could give me, to help me achieve my Ubuntu/Kubuntu dual-boot system. Thanks in advance!

---

### Post by ryan! on 2011-07-28
as for #4 i have 10gb and it works fine

---

### Post by Paqman on 2011-07-28
> **scruffyeagle said:**
> Hi!
1) Will Linux let me set all 4 as primary partitions, or am I limited to 3 primaries as in Windows?


It's actually 4 primaries, and I believe it's a limitation in BIOS not Windows, so affects Linux too. If you're worried about losing flexibility, create some or all inside an extended partition. An extended partition is a primary partition that can many partitions inside it, breaking the four partitions rule.

> 
2) Can I place the swap as partion #1, or am I required to make partition #1 bootable?.

3) Given 2 partitions for OS's, is there a most beneficial order for installing & placement of Ubuntu & Kubuntu? (I say it that way, because for example it might be best to load Kubuntu first into the 3rd partition.)

You can have them in any order you like

> 
4) Is 20 GB per OS overkill, or could I easily get by with half that and never run out of OS programs storage space?


You probably could get by on 10GB if you never do anything that creates really huge temp files, like authoring DVDs.

> 
5) Is 2 GB enough for the swap, or would the OS's work more efficiently if given more?

Should be plenty. Swap is only ever used when you're running low on RAM, so only improves performance on older machines or those running really intense programs.

It's also used for hibernation. If you want to hibernate the machine, make sure your swap is as big as your RAM.

> 
6) Will there be difficulties re. ownership of personal data files in partition #4, re. files that were created while using Ubuntu & Kubuntu?

Yes. The simple solution is to use a different user name on each system. That way the two folders in /home won't affect each other.

BTW, were you aware that you don't have to set up a dual-boot to have both regular Ubuntu and Kubuntu packages on the same system? You can just add the KDE packages to Ubuntu, and vice versa. The main disadvantage of that is that things can get a little cluttered, as you'll end up with two different apps for each job.

---

### Post by theozzlives on 2011-07-28
They are basically the same "under the hood". Just install one and add the desktop for the other one. You can pick and choose at the login screen and use the same /home.

---

### Post by westie457 on 2011-07-28
> **scruffyeagle said:**
> Hi!

What I've done so far:
I've downloaded, md5'ed, burned, & verified disks for both Ubuntu & Kubuntu; both, in the 32-bit v10.04 LTS versions.

What I intend to do:
I intend to install both Ubuntu & Kubuntu on the same machine, for the sake of "living with" each of them for a while. Then, eventually, I'll probably make up mind which I like best, followed by re-partitioning to make the disposed of one's space be turned into personal data space.

How I hope to do it:
I intend to re-partition the 60 GB HD in a Dell Inspiron 9400 laptop as:
1)  2 GB swap,
2) 20 GB OS,
3) 20 GB OS,
4) 18 GB home partition.

Questions I need answered:
1) Will Linux let me set all 4 as primary partitions, or am I limited to 3 primaries as in Windows?
2) Can I place the swap as partion #1, or am I required to make partition #1 bootable?
3) Given 2 partitions for OS's, is there a most beneficial order for installing & placement of Ubuntu & Kubuntu? (I say it that way, because for example it might be best to load Kubuntu first into the 3rd partition.)
4) Is 20 GB per OS overkill, or could I easily get by with half that and never run out of OS programs storage space?
5) Is 2 GB enough for the swap, or would the OS's work more efficiently if given more?
6) Will there be difficulties re. ownership of personal data files in partition #4, re. files that were created while using Ubuntu & Kubuntu?

I realize I've thrown out a lot of question here. But really, it's all stuff I need to know. I'd appreciate any advice or insight you could give me, to help me achieve my Ubuntu/Kubuntu dual-boot system. Thanks in advance!

Hi, This is advice only and my humble opinion.

1 Any hard drive that uses the mbr-style of partitioning is limited to 4 primary partitions. To have more than 4 on a hard drive there has to be at least one extended partition to allow the creation of logical partitions.

2 Personally I would have Swap as the last partition at the end of the drive (partition 4). The bootable partition is decided by Grub which has to be installed to the mbr of the hard drive.

3 Install how you want. That is a matter of personal choice. It makes no difference really.

4 Personally I would cut the root of each OS to around 10GB leaving the most space for the home folder.

5 2GB is more than enough for Swap. Depending on how much RAM you have you will hardly ever use it unless you want to hibernate your system. Something I do not do as it boots fast enough already.

6 I have absolutely no idea on this as my system is set up in a different way and each one has its own home folder. Also I have a separate storage area on a different drive, this is so Windows and the other OSes can access the files.

---

### Post by anewguy on 2011-07-28
> **theozzlives said:**
> They are basically the same "under the hood". Just install one and add the desktop for the other one. You can pick and choose at the login screen and use the same /home.

+1  you don't need separate installs and partitions - Ubuntu is Ubuntu (basically).  The only difference is in the desktop environment you use.  So what would I do?

[LIST]
[*]Partition the drive as you want for your "final" installation
[*]Install the default Ubuntu from the LiveCD (or USB).  This will install the Gnome desktop manager - what you think of as regular Ubuntu
[*]Once up and running, go to synaptic package manager and install the KDE desktop - it will want other things installed as well.
[*]When you boot Ubuntu and it asks for you to select your userid, enter your userid, then go to the bottom of the screen where it says "Sessions" and click - you'll see options there for regular Gnome (it may say Classic) Ubuntu, an option to select KDE and others as well.  Just click on what you want to try for a given session.
[*]Now enter your password and logon.
[/LIST]

As with any install, remember there will probably be things you want to add.  Some may be specific to Gnome, others specific to KDE, but practically everything should run in either.

---

### Post by scruffyeagle on 2011-07-29
Hi, all! Thanks for all the feedback. I think I understand better now, my options in setting up for testing/comparing Gnome vs. KDE.

I'll probably go w/ a 3 partition setup:
sda1 primary Ext4 OS /
sda2 primary swap
sda3 primary Ext4 home

sda1 + sda2 will approximate 20 GB (either 17+3 or 18+2), w/ sda3 being 40 GB. Swap will be sda2 instead of sda3, because it minimizes latency when working on large files that require using swap space.

I'll be installing Ubuntu then downloading KDE from Synaptic, & using the desktop selection at login time to switch between.

I'll update this thread, if I do anything differently than I've said here.

Thanks again!

---

