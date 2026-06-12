---
title: "Worried about upgrading from Karmic Koala to Lucid Lynx"
date: 2010-08-14
forum: New to Ubuntu
---

### Post by dissembly on 2010-08-14
Hey all,

I am wondering whether I should upgrade.

I have everything working the way I want it to at the moment, but I am afraid that upgrading may cause my wireless driver to no longer work. 

When I updated Karmic Koala for the first time, it stopped working, and I had to go and get the most recent driver. But there are no drivers more recent than the one currently installed, so if it doesn't work with Lucid Lynx, then i would have to go back to Karmic Koala to get it working again.

The only thing that makes me sort-of want to upgrade at the moment is that the most recent version of Inform 7 doesn't work on my system, and it was designed for Lucid Lynx.

So:

*If i do upgrade, and breaks my wireless, will it be easy for me to go back to the previous state? Can i take some precaution to make it easier?

*Is it really worth upgrading? Except for Inform 7, everything works well at the moment (and i can always run an earlier version of I7, i just won't get whatever new features have been added) - if i don't upgrade, will that create problems me?

- David

---

### Post by ed-koala on 2010-08-14
Try Lucid from the Live CD first, see if wireless works out of the box, then upgrade if all works ok

---

### Post by Elmer Fudd on 2010-08-14
David,

Run from a liveCD first. 
If it all works, install Lucid as an additional operating system (leave Karmic as something you can pick from Grub/Burg). 
Then if everything is working or you can sort it out, you can abandon Karmic.

---

### Post by dissembly on 2010-08-14
Ooh good ideas.

Is there a tutorial somewhere for installing Lucid as an additional operating system?

---

### Post by Elmer Fudd on 2010-08-14
Did you install Karmic in a dual boot with windows or just as a sole OS.

---

### Post by dissembly on 2010-08-14
It is a sole OS on a 10" mini-laptop (so unfortunately the Live CD isn't an option, but the idea of having it side-by-side with Karmic sounds appealing).

---

### Post by ed-koala on 2010-08-14
When I do clean installs of Ubuntu it has an option to install side by side with <whatever>.  Just select that and let the installer do the work.

---

### Post by -kg- on 2010-08-14
> **dissembly said:**
> It is a sole OS on a 10" mini-laptop (so unfortunately the Live CD isn't an option, but the idea of having it side-by-side with Karmic sounds appealing).

Then [Unetbootin]("http://unetbootin.sourceforge.net/") will give you a Live CD on a flash drive that you can boot to.  You can burn the Live CD iso to the USB Flash drive and boot from that.

One thing, though.  I've had trouble with the included default downloads, which I think were corrupted downloads.  I would suggest downloading the iso (I prefer a torrent), checking the md5 checksum, then installing it to the Flash drive using that iso.  That method has worked for me every time.

To your "side-by-side" question:

Depends on how much hard drive space you have and how much of that you've used in your Karmic installation.  If you have plenty of hard drive space and plenty of room in your Karmic partition(s), then it would be relatively easy.

How big a hard drive do you have, what partitions do you have on it, and how full are they?

---

### Post by dissembly on 2010-08-14
-kg- - i am using a 320GB hard drive with no partitions (none that i can see). I ordered it made specially, and didn't request any partitions (it would have been $14 to do so), so i'm pretty sure it's un-partitioned.

---

### Post by muteXe on 2010-08-14
You can confirm this for sure with
```

sudo fdisk -l

```

(that's a little 'L', not a 1).

---

### Post by -kg- on 2010-08-14
If you are currently running Karmic Koala, the hard drive has at least one, and likely two partitions.  You will have to have "/" (root) and very likely a "swap" partition, unless you mean that you ordered the 320GB hard drive specially and intend on installing it.

The command, "fdisk -l" will tell you what partitions you have on your hard drive, but will not indicate how full they are.  You can pull up "Places/Computer" and right-click on the "System" icon and select "properties" from the menu.  At the bottom of the Properties window you will find how much free space you have in the partition (approximately).

You will not want to use all the free space, but if you have enough space (and I suspect you will, with a 320 GB hard drive), you will be able to shrink that partition and install side-by-side.  You will be able to do this by selecting "Install Side By Side" in the Partitioning section of the installer and it will do everything automatically.

One thing to keep in mind...when and if you decide to uninstall Karmic, normally it is done by deleting the partition it's in.  When you delete a partition, it changes the partition information for every partition that was created after that partition.

Since Karmic is already installed, it's partition is sda1.  Swap will be sda2.  When you install Lucid side-by-side, it's root partition will become sda3, and if you select side-by-side, you will also create another swap which will be sda4.  You can safely delete the extra swap partition later...both installations will use a single swap partition.  Make sure you delete the newly installed swap partition, though, or you will run into the above (and below) problem immediately.

Anyway, when you delete the Karmic partition, all following partitions' designations will be changed.  Lucid will change from sda3 to sda2, etc.  This means that GRUB will not be able to "find itself" and you will be unable to boot to it.

If you don't have an Extended partition, you may be able to forego this problem.  Just boot into the Live USB, select "Try Without Installing", launch "System/Administration/GParted", and resize your root partition, shrinking it to give you some space.

Give yourself about 1/2 the total size of your hard drive, if possible...if not, as much as you can give it without cramping your Karmic installation too much.  You'll want, say, 10 GB or so of room for Karmic to continue to function well, but 30 GB or so of free space should be a good amount to give to Lucid for the tryout, to see if it will work for you.

Then once you have created this free space, click on it in GParted and select "New" (that will be one of the few selections available for free space) and create a new partition.  You will want to create an Extended partition and it should encompass all the free space you just created.  Of course, click "Apply" after each operation.

You should read the information at the link in my signature block.  It will explain what you're doing and show you step-by-step how to perform basic partitioning operations.  The partition(s) you presently have on your hard drive are very likely Primary partitions, and you can only create 4 Primary partitions (due to size limitations in the Partition Table in the Master Boot Record (the MBR))

An Extended partition is a special type of Primary partition in which you can create many more partitions, called Logical partitions.  Windows requires a Primary partition from which to boot (except under special circumstances), but Linux will boot and run from either Primary or Extended.  This also allows you to have more than 4 partitions on your hard drive, in case you decide to have separate partitions, say, for a separate "/home" partition or such.

Once you have done this and closed GParted, you can launch the installer from the desktop and, when you reach the partitioning section of the installer, select "Install to largest contiguous free space", which will install to the Extended partition that you just created.

The thing about this is, Primary partitions are designated sda1 through sda4.  An Extended partition will be designated one of these, then Logical partitions will be designated sda5 through sda<however many Logical partitions you have created>.  If you delete a Primary partition, the Logical Partition designations will not change.  You ***_might_*** get around the boot problem with this method.

If not, you should be able to reinstall GRUB from the Live USB, but I wanted to make you aware of the possibility that you might break booting.  If absolutely nothing else, you should be able to reinstall Lucid using the "Whole Disk" selection in Partitioning, and it will put a nice fresh installation on it.

Another possibility for you to consider:

Install side by side and find out if it will work for you.  If it does, then you might want to try upgrading Karmic to Lucid and see if it works OK.  That would eliminate all the problems above, and you could delete the extra Lucid partitions and expand the old one back into the free space.

If the Upgrade doesn't go well, there is one more possibility to eliminate the problems I have indicated above.  From Lucid (once you have decided you know longer need Karmic, of course), install GParted from the repository.  Launch it and select sda1, which should be your Karmic root partition...make sure you select the right one.

Then select to format the partition (pretty well any format you want...just go with the default) and apply the operation.  Then select that partition again and shrink it to next to nothing (unless you want to mount and use it for something, but that's beyond the scope of this thread).

In doing that, you will preserve the partition numbering scheme and you should be able to boot normally into the new Lucid installation.  This is probably the best method for you to use, and it will waste only a little hard drive space, which you really have plenty of.

One final consideration:

You can get an external hard drive and install Lucid to that hard drive, or you can get one of the large flash drives and install to it rather than burning the Live CD iso to it.  There are other considerations you might want to know in doing that, but this post is already getting overly long (probably TMI-TS).

There are a lot of possibilities...pick one and go with it, and we'll be more than glad to walk you through it.

---

### Post by dissembly on 2010-08-24
Hey, sorry about the time it took to reply, have had an insane week!

Thank-you for the information and the support. I think i will try what looks like the easiest route - trying Lucid, then just upgrading Karmic if it works rather than going with a Lucid partition.

I just wanted to check one thing though: My wireless card uses a driver that i had to install myself. If i, for example, booted Lucid from a bootable USB drive, or booted it from a new partition that was freshly installed, would i need to somehow put the wireless driver into that version of Lucid, or would it search for the wireless driver that i have loaded already?

---

### Post by LiquidMeson on 2010-08-24
If when testing lucid out on the usb drive wifi works. Then you will have no wireless problems. If it doesn't simply don't upgrade. Let us know how it goes!

---

### Post by dissembly on 2010-08-24
LiquidMeson - yes, but the thing is that Karmic Koala would not work without downloading the right driver. If i run Lucid and it doesn't work, does that mean that it really doesn't work, or just that it cannot see the driver i installed earlier? I do not know how drivers work, and whether Lucid will see the driver i've already installed, or if i would need to install the driver separately on Lucid.

Because this would make a difference to the strategy i take - testing it out from a Live USB (where i presumably cannot install the driver) versus testing it out with a new partition (where there is much more room for me to do something that damages my computer, but i can easily install the driver).

---

### Post by kroq-gar78 on 2010-08-24
sorry for butting in, but did you have to restart your computer to install the driver? if you didn't, then you can test in on the live cd (or at least you should be able to). Otherwise, you have to probably just install it

---

