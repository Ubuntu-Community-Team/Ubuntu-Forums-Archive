---
title: "Installing 8.10 on existing partition"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by MaxVK on 2009-01-09
Hi, my son has an existing Windows XP installation, but now wants to play with the dark side and install Ubuntu alongside it.

He booted from the live disk and went through the installation procedure right up to the point where it wants to know where to install.

The hard disk is set up like this:
sda1 - Windows XP
sda2 - Empty for Ubuntu
sda3 - Tiny recovery drive

At this point we are both a bit lost - The installation choice we need is most likely the 'Manual' selection, but I'm not entirely sure what to expect next since Iv never been down this road before.

Is it as simple as typing in sda2 as the destination or do I need to consider other things along the way? 

Any advice would be very much appreciated at this point.

regards

Max

---

### Post by Michael.Godawski on 2009-01-09
hi,

how big is the sda2 and what format of this partition?

Perhaps you can use the option use largest continues free space to install Ubuntu?


[LIST]
[*][http://www.psychocats.net/ubuntu/dualboot](http://www.psychocats.net/ubuntu/dualboot)
[/LIST]

---

### Post by jken146 on 2009-01-09
Go for manual.  Allocate a 10 GB ext3 partition for / and a small partition for swap (RAM x 1.5 but no bigger than 1 GB).  Let the rest of the space be ext3 for /home.

---

### Post by sadaruwan12 on 2009-01-09
> **MaxVK said:**
> Hi, my son has an existing Windows XP installation, but now wants to play with the dark side and install Ubuntu alongside it.

He booted from the live disk and went through the installation procedure right up to the point where it wants to know where to install.

The hard disk is set up like this:
sda1 - Windows XP
sda2 - Empty for Ubuntu
sda3 - Tiny recovery drive

At this point we are both a bit lost - The installation choice we need is most likely the 'Manual' selection, but I'm not entirely sure what to expect next since Iv never been down this road before.

Is it as simple as typing in sda2 as the destination or do I need to consider other things along the way? 

Any advice would be very much appreciated at this point.

regards

Max

Hi,

Use this guided it's written for Hardy Haron(8.04) but it's compatible with Interpid Ibex(8.10).

[*[FONT="Franklin Gothic Medium"]Take me there[/FONT]*]("http://www.howtoforge.com/the-perfect-desktop-ubuntu-8.04-lts-hardy-heron")

---

### Post by Michael.Godawski on 2009-01-09
ah 
forget to post this two articles too which might be helpful:

[LIST]
[*][http://godawski.oxyhost.com/switch.html](http://godawski.oxyhost.com/switch.html)
[*][http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)
[/LIST]
jken146 suggestion is also valid.

---

### Post by MaxVK on 2009-01-09
The partition for Ubuntu is 80Gig, so I have plenty of space to play with.

---

### Post by Son of MaxVK on 2009-01-09
Thanks everyone.

---

### Post by MaxVK on 2009-01-10
Okay, so we ran into a problem:

Booted from the livecd, clicked install and reached the partition section.

Accordingly we selected sda2 and chose to edit the partition. Of the whole space we set 10 gig aside as ext3 and mounted as root. I figured that once this was done we would see 70 gig as empty space as 10 assigned as root.

This didn't happen, and we ended up with an error that simply said that that the process could not continue, although we did end up with sda2 as ext3.

I tried again but got the same error and was then warned that no swap had been set up. I tried the same thing again, but again there was a problem and I was warned to go back and correct it or carry on with the error.

Can anyone give a clue what to do next? I have an 80 gig partition waiting for Ubuntu, but I cant seem to get it on there!

Cheers

Max

---

### Post by carml on 2009-01-10
IMHO I think you have to manually create at least a partition for root and  one for swap,then you'll be asked for the mount point,that is the first partition you created for Ubuntu. :P

---

### Post by MaxVK on 2009-01-10
Do you mean that we need to manually create the partitions we will use *before* we actually use the installer, and then just assign root, home and swap to the correct places?

So we need to split sda2 into 3 - one part for root, one for home and one for swap?

Max

---

### Post by Son of MaxVK on 2009-01-10
This is all so confusing. ](*,)

Thanks for everyone's help so far.

---

### Post by -kg- on 2009-01-10
If you are going to manually create your partitions during the installation (i.e., to have a separate / (which is the root partition) and /home partitions (as well as the requisite swap partition, of course), then my first suggestion would be to read the following page from the Community Documentation:

[How To Partition]("https://help.ubuntu.com/community/HowtoPartition")

This page covers basic hard drive partitioning and will up your knowledge of what you're trying to accomplish, and what you can and can not do.  Now for the specificities.

Yes, it has been said that it is desirable to have a separate / and /home partition, and I agree with this.  As matter of fact, I don't know why they don't incorporate this into a separate downloadable distro (for those who have the hard drive space to have it).  Anyway, in order to have this separate partition, you will need to manually create your installation partitions.

While you can do this pre-installation, you can also do it during installation using the "Manual Creation" selection during installation (as I'm sure you already know).  Using this selection, you are responsible for the creation of all the partitions to be used, and of course, you must *mark* them (i.e., set the mount point) as what they are to be used for.

I was unable to find any tutorial that specifically showed (in screen shots or photos) how to set the mount point during manually creating the partitions, but [this page]("http://www.pcmech.com/article/installing-ubuntu-linux/") has good step-by-step instructions on how to manually create partitions during the installation process.  This particular How To was generated using Gutsy (7.10) but the instructions should be sufficiently similar that it can be used for 8.10 as well.

---

### Post by MaxVK on 2009-01-11
Thanks -kg-, I worked out how to do it from the link you posted, but Iv now given up on 8.10 entirely because having actually managed to set up the partitions, the installation failed when it came to copying files - presumably (If the error was anything to go by) because of a problem with the disk.

I have a 7.10 and an 8.04 disk here as well, so perhaps we will end up using one of those.

Thanks for your efforts.

Max

---

### Post by stanz on 2009-01-11
Are you burning your own .ios image?
and at a _slow_ burn speed?

Have the live cd's changed - that one has to boot into it? { install option @ boot?}
Michael option to use largest free space is easy...but it shouldn't be formatted.

---

### Post by MaxVK on 2009-01-11
Thanks stanz,

No, the disk comes from Canonical as an original.

The largest free space is no longer an issue since the last time around I managed to create the correct partitions (root, home and swap). The only problem seemed to be with the disk itself and copying files.

Since I had problems in the first place (and Id swear that I used the same procedure that just worked) I'm thinking that there is a problem with the disk itself, so Ill be falling back on the 8.04 disk (also from Canonical) and with any luck that will work.

regards

Max

---

### Post by stevoo on 2009-01-11
> **MaxVK said:**
> Do you mean that we need to manually create the partitions we will use *before* we actually use the installer, and then just assign root, home and swap to the correct places?

So we need to split sda2 into 3 - one part for root, one for home and one for swap?

Max

Actually two.

one for the root which is your home dir as well and a small one for swap.

When you do that, you should be fine

---

### Post by MaxVK on 2009-01-11
Thanks stevoo, but I generally have /home on its own partition, just to make life easier if things go wrong, or I choose to play with another distro.

Regards

Max

---

