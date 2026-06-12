---
title: "Dual XP Maverick partition confusion"
date: 2011-03-15
forum: New to Ubuntu
---

### Post by widda on 2011-03-15
About a year after going exclusively Ubu, and pretty well forgetting Windows ways, I got a Dell Dimension PC with XP on it, and so installed Maverick via Wubi. 
XP had already been partitioned into "drives" C and D - I don't THINK there are 2 physical drives in it.
I'm  confused by the 2 systems together, and my favourite thought is to nuke XP.
But first I'm asking here if anyone, with the help of these screenshots taken  in both OS's filesystems, could tell me if there is anything really crazy in the setup that could be straightened out. It feels like there is, but I don't even know what question to ask at this point. two xpshots following

---

### Post by widda on 2011-03-15
two more xpshots:

---

### Post by Dutch70 on 2011-03-15
Typically your D drive is a recovery partition, but it shouldn't be 54GB, or even 20GB & almost full.

If you want to dual boot Ubuntu & XP, you need to create a live cd or usb stick. The usb stick is easier & faster if you have one. Actually, you need to do that even if you decide to wipe XP off the disk. 

Post back with a pic of your hdd on gparted from the live cd/usb & I or someone else will be glad to help you with it.

---

### Post by widda on 2011-03-15
Thanks Dutch70, my second post above actually has shots of the menus of C and D (taken from inside XP).
I'll have a look at the live usb creation.
I do get dual boot screen in current setup, can use either OS, 
Glad you think something looks wrong with drives.

---

### Post by Dutch70 on 2011-03-15
> **widda said:**
> Thanks Dutch70, my second post above actually has shots of the menus of C and D (taken from inside XP).
I'll have a look at the live usb creation.
I do get dual boot screen in current setup, can use either OS, 
Glad you think something looks wrong with drives.

By dual boot, I mean a native boot/install for Ubuntu, not inside of windows, as it's dependant on windows. If/when windows fails, it will take Ubuntu with it. My question is, do you want to partition your hard drive & give Ubuntu it's own partition to reside in and Keep XP also? Or, what exactly is your question? :D

Can you wipe the D drive or do you have important files on it? It doesn't look like there is much on there, but if you want to keep XP, you may also want to expand the partition it's on to give it a little more room. 

Also, I don't think there is really anything wrong with your file system, it's just odd to me. Probably b/c it's Wubi.

Edit: I'm not real keen on wubi, but I think you may get a different picture of your hdd from the live cd/usb. It looks like all of your files from Ubuntu are on the D drive. You may want to get some advice from someone who knows more about wubi than I.

---

### Post by mastablasta on 2011-03-15
wubi installs in a large file inside windows. if you delete windows you delete wubi or make it unusable.
 
to make a propper side by side you need to:
1. defragment drive (2 times at least), run chkdsk
2. create a separate partition and not format it - you will need 20-30GB for your linux.
3. boot from LiveCD or LiveUSB and start the install process
4. during install process select to install to largest free space
 
Linux will then install into new partition and it iwll add a bootloader named GRUB before the windows boot loader. That way you will be able to choose which system you want to use on boot.

---

### Post by widda on 2011-03-16
> **Dutch70 said:**
> By dual boot, I mean a native boot/install for Ubuntu, not inside of windows, as it's dependant on windows. If/when windows fails, it will take Ubuntu with it. My question is, do you want to partition your hard drive & give Ubuntu it's own partition to reside in and Keep XP also? Or, what exactly is your question? :D

Can you wipe the D drive or do you have important files on it? It doesn't look like there is much on there, but if you want to keep XP, you may also want to expand the partition it's on to give it a little more room. 

Also, I don't think there is really anything wrong with your file system, it's just odd to me. Probably b/c it's Wubi.

Edit: I'm not real keen on wubi, but I think you may get a different picture of your hdd from the live cd/usb. It looks like all of your files from Ubuntu are on the D drive. You may want to get some advice from someone who knows more about wubi than I.

Thanks, I used Wubi because it was simple and enabled me to get ubuntu immediately without doing battle with the partitioning process.
However, the XP being split in two (C&D) is a confusion I don't need (I found out from prev. owner of PC that D was created by shop guy during XP recovery.
How can i most simply remove D?
I want ubuntu in own partition, not inside XP, but not sure yet whether to ditch XP, tho if it saves confusion I wont hesitate!
I have a few things to do next anyway, such as dload live usb, and study up the partitioning some more, and have a go at deleting D, thanks, I know it was a vague post to tackle !

---

### Post by widda on 2011-03-16
> **mastablasta said:**
> wubi installs in a large file inside windows. if you delete windows you delete wubi or make it unusable.
 
to make a propper side by side you need to:
1. defragment drive (2 times at least), run chkdsk
2. create a separate partition and not format it - you will need 20-30GB for your linux.
3. boot from LiveCD or LiveUSB and start the install process
4. during install process select to install to largest free space
 
Linux will then install into new partition and it iwll add a bootloader named GRUB before the windows boot loader. That way you will be able to choose which system you want to use on boot.

Thanks mastablasta, that is helpful

---

### Post by Dutch70 on 2011-03-16
First, uninstall wubi from windows & lets get a look at what you have then.

---

### Post by Mark Phelps on 2011-03-16
Unless they changed the installer from when I last looked at it, there is no "largest free space" option anymore ...

You now have to go through Manual Partitioning, and be very careful when you do, because if you accidentally select the wrong partition, you will erase your XP install.

---

### Post by widda on 2011-03-16
I now have Maverick live usb (10hour download) - untested so far.
I don't want to uninstall Wubi YET b/c it is now the only keeper of my files from crashed 10.4 laptop.
Plan so far is:
Convert xp into a simple Drive C instead of C & D, defrag and chekdisk
Install Mavrk from USB on own partition
Pull files out from wubiMvrck in xp to new installed Mavrck.
Shrink partition of or dispose of XP
My plans may exceed my skills, but there are some clues here ,thanks,

---

### Post by rosencrantz on 2011-03-16
I'd highly recommend keeping a multi-partition setup - use dedicated partitions for operating systems and keep your personal data on another. You'll be glad about it when Windows decides to eat your system partition one day, and it's also much less risky to share files between operating systems that way. 
If it works for you (depends on whether your Wubi version is supported), you might also want to consider LVPM, which transfers the Wubi install to a hard drive partition: [http://ubuntuforums.org/showthread.php?t=438591](http://ubuntuforums.org/showthread.php?t=438591)
After that, you can do the upgrade to a recent Ubuntu version without losing files or settings.

Cheers,
rosencrantz

---

### Post by bcbc on 2011-03-17
Don't use LVPM - it doesn't work well since 8.04. Since you have an extended partition already, and the logical partition is only using 3GB, you can split that with GParted (from Wubi), create two new logical partitions in the space for root and swap and then either install fresh to them or you can migrate with this: [http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

---

### Post by widda on 2011-03-17
> **rosencrantz said:**
> I'd highly recommend keeping a multi-partition setup - use dedicated partitions for operating systems and keep your personal data on another. You'll be glad about it when Windows decides to eat your system partition one day, and it's also much less risky to share files between operating systems that way

Yeah that does seem a much less disturbing setup, that is goal prior to decision about removing xp.

---

### Post by widda on 2011-03-17
[QUOTE=bcbc; Since you have an extended partition already, and the logical partition is only using 3GB, you can split that with GParted (from Wubi), create two new logical partitions in the space for root and swap ...[/QUOTE]


That sounds pretty neat, i'm not sure I can translate it into action when confronted with GParted GUI, but .. (off to inspect "GParted-from-Wubi")

---

### Post by Ditchdoc7893 on 2011-03-17
> **widda said:**
> I don't THINK there are 2 physical drives in it.

This may sound completely asinine, but if you're wondering how many physical drives are in the machine, pull the cover off.  Otherwise it looks like you have a single physical drive.  My idea would be to just go get another HD and drop it in (not expensive for something just to run Ubuntu).  Keep XP like it is (assuming you really want to keep it), and then load up Ubuntu on the new drive.  You'll still be able to get to any files you need on the XP OS, that way you're not risking losing any information or files you need or want to keep.  All you should have to do on boot-up is to decide which OS you want to startup and go with it.  Do this on the initial startup (my system uses the F-12 key for boot menu).  Then choose which HD you want to boot from.  I've had virtually no problems doing things this way.  Obviously if you run into problems, this is the place to be!  :D

---

### Post by bcbc on 2011-03-17
> **widda said:**
> That sounds pretty neat, i'm not sure I can  translate it into action when confronted with GParted GUI, but .. (off  to inspect "GParted-from-Wubi")
Well /dev/sda5 is your "D:" drive. And it shouldn't mount automatically  when you boot Wubi since that's installed on C: (/dev/sda1) which is mounted as /host. 

Also, since it's not the windows boot partition you shouldn't have to worry  about defragging and other Windows boot issues. (I'd still consider rebooting  into windows after shrinking /dev/sda5 to be safe, but I doubt it would  cause Windows to have any fits).

So basically the steps would be:
1. Boot Ubuntu and run GParted
2. Shrink /dev/sda5 
3. If concerned reboot into Windows to make sure it's OK
4. Back to Ubuntu/Gparted, create /dev/sda6 as Root and /dev/sda7 for swap in the free space you created
5. Either download and run the migration script in that link I showed before or install fresh

---

### Post by widda on 2011-03-17
[QUOTE=widda
...Plan so far is:
Convert xp into a simple Drive C instead of C & D, defrag and chekdisk
Install Mavrk from USB on own partition
Pull files out from wubiMvrck in xp to new installed Mavrck.
Shrink partition of or dispose of XP...[/QUOTE]

Ouch. 
So, a partition called "Drive D" in Windows and called "Hard Drive" in Ubuntu  in /Media has 50+gB while Drive C has only 20GB including said Ubuntu.
But I don't know what to do about it
Can't boot from live usb Maverick,
Maybe this has to be sorted via Windows anyway??

I need another plan,
starting with re-reading this thread :|

---

### Post by widda on 2011-03-17
ah ditchdoc and bbc , two late posts i hadnt read before  my last,  thanks, i needed idea right now. about to read them

---

### Post by Ditchdoc7893 on 2011-03-17
Hey widda, just glad I could give you a light bulb.  I'm a noob to Ubuntu and Linux myself, and I'm definitely learning, but I've found that if I think of problems in physical terms themselves I can figure out what I need to do to make things work the way I want them to.

---

### Post by Ditchdoc7893 on 2011-03-17
> **Ditchdoc7893 said:**
>  I've found that if I think of problems in physical terms themselves I can figure out what I need to do to make things work the way I want them to.

Of course with A LOT of help from this forum!  These guys are phenomenal!

---

### Post by widda on 2011-03-17
Not sure if I could identify a HD (or 2) by sight:oops:
Would like to spend 20 hours uninterrupted on this, or even 3, but life is not permitting that. These forums are great yup, and my enforced delays between accessing regrettable.

---

### Post by Ditchdoc7893 on 2011-03-18
On my system (Gigabyte motherboard, 3 HDDs, 2 DVD-RWs, multiple flash and usb drives), when I use the F-12 on startup and get to the boot menu, it asks me which drive I want to boot from, whether that be from hard drive(s), CD-ROM, USB, Flash, etc.  When I arrow down to HDD, because I am running 3 separate hard drives (one with XP, bootable; one with nothing but storage, and one with Ubuntu that is bootable), I can choose which drive to boot from.  The key to this is knowing which drive has which OS installed on it).  If you can identify the drive that windows is installed on, write it down.  Then on the new drive, it should have a different label when you boot up.  My guess is that the exact steps to getting to this point is determined by your motherboard and how it handles the boot process.  When your system initially boots up, you should be given the option to press a key to choose your boot device.  You can set the boot order in BIOS if you wish, which will tell the mobo what drive to automatically boot from.  I usually choose to do this manually because my husband is much more familiar with Windows, while I choose to use Ubuntu.  So to make it easier, I give him the option of booting into XP.  Do a little research on your system.  Check out what your Windows drive is labeled as (when I say that, I mean in the BIOS, should show something like Maxtor879xyz4blahblahblah).  

When you drop in another HDD, it will show some other different label.  Load Ubuntu up on that 2nd HDD.  Then use the boot menu (described above) to get to that drive and make it boot.  Hope that helps.  If you do decide to get another HDD and do it this way, I can try to walk you through it.  I just did it a couple months ago.

---

### Post by Dutch70 on 2011-03-18
As far as whether you have one physical hdd or two, all you have to do is open Gparted. In the upper right hand corner, there is a little drop down box. If you have 2 hdd's, you will be presented with the option to select the other one from there. Typically one  will be labeled sda & one  will be sdb, and so on for the more drives you have, including temporary ones such as usb sticks. Although they will usually be called sdf or sdg, on my system anyway.

---

### Post by bcbc on 2011-03-18
If you look at your second post you show the D: drive from Windows and it says 51.2GB Free space, and 54.4GB total size.

If you look at post #1 your gparted shot says: /dev/sda5 is 54.42GiB with 51.29GiB Unused and 3.12GiB used.

I don't think there is any doubt that your D: drive is /dev/sda5.

---

### Post by widda on 2011-03-18
> **Dutch70 said:**
> As far as whether you have one physical hdd or two, all you have to do is open Gparted. In the upper right hand corner, there is a little drop down box... 

Ok, didnt see *that* lil arrow...Only one HDD it is.

---

### Post by widda on 2011-03-25
**Thank you all**,
After a certain amount of messing about, amidst a busy life, I realised that keeping XP was not worth one more thought, and clean installed my 10.04LTS disk over the former setup of XPdriveC&D/10.10.
Feeling better already.
Now to get the inexplicably-to-me non bundled GParted and see what it looks like and (groan) briefly investigate how unoptimal the swap, home, arrangement is.

---

### Post by widda on 2011-03-25
Well here it is, as installed by disk (except for 7Gb of files I put back so far)

---

