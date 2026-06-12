---
title: "installing windows 7 after ubuntu?"
date: 2011-09-04
forum: New to Ubuntu
---

### Post by Jonas thomas on 2011-09-04
Ok.. So here's the deal... I'm taking a C# class for work and need windows on my currently ubuntu only laptop. (where it not for this class I don't think I would want windows on my laptop... Since at home %99 I'm in Linux and quite happy with that)

I basically have my laptop running nice(except my wife complains that see can't dim the screen) and all my other stuff is installed and configured.

So.. Would like to  install windows 7 and visual studio without wiping out my current Ubuntu configuration? 

Is there any easy way to do this? That is Ubuntu installed first and then put windows 7 on? If someone could recommend a how to guide that would be nice.

Thanks
JT

---

### Post by Basher101 on 2011-09-04
it will be more troublesome installing windows after ubuntu but it is possible. How big is your installation WITHOUT documents, music, downloads and everything else you can move? If you can get below 18 GB you can make a live .iso from that installation and wipe your whole drive, install windows and use the live .iso you made to reinstall your whole system as it was back and move your huge files back. This is the easiest way i can think off anyways.

---

### Post by Bucky Ball on 2011-09-04
There is an issue as we discovered [HERE]("http://ubuntuforums.org/showthread.php?t=1836671"). Win7 makes two partitions, not one, so if you have three primary partitions on your drive already it won't go on! Sucks a bit but ...
It can get convoluted. If you could take a screen shot in Gparted would be helpful or post the output of:

```
sudo blkid
```In a nutshell, if you have /, /home and /swap on primary partitions (not in an extended partition) and Win7 creates two more you have gone over  the limit of four primary partitions on one physical drive. Installing Win7 makes five as it creates a small recovery partition as well as the Win7 partition (cheeky). Therefore, desirable would be to have Win7 on a primary partition, its recovery on a primary (think that's only option), / on a primary and everything else in an extended partition (/home, /swap, NTFS partition for sharing between two for instance).

Note well: Extended partition counts as a primary partition, BUT, you can have, theoretically, as many logical partitions inside that as your hardware will handle. 

Good luck.

PS: you need to update the Ubuntu grub and fiddle around there from a LiveCD once you have it installed also. My advice: Create enough free space at the beginning of the drive for Win7. With luck you might be able to boot from a LiveCD, open GParted, move your Linux (EXT*) partitions to make room and plop Win7 there. It is easier when it is SDA1. There is a problem there, of course, if Win7 doesn't consider itself sda1 but consider that when and if you get there.

Another option is to save your Ubuntu setup/config using Remastersys or something else, backup your data, install Win7, install your custom Ubuntu with your previous apps and settings from the ISO you created with Remastersys and you're good. You might want to have some time on your hands though. ;)

You can program with c# in Linux. You might want to look at mono. [http://www.mono-project.com/Main_Page](http://www.mono-project.com/Main_Page)

Are you learning a specific piece of programming software rather than a specific programming language ... or both??

---

### Post by Mark Phelps on 2011-09-04
In my experience, Win7 only creates two partitions if the drive is completely unformatted.  You can also get around that by creating an empty partition, formatting it NTFS, and then, letting Win7 reformat that.

---

### Post by thiebaude on 2011-09-04
If it were me I would just start over, meaning I would wipe everything on the hard drive and install windows 7 then install ubuntu after you install win7. I'm not sure how to install win7 after ubuntu, because i have always had windows on the computer first, then ubuntu, because grub creates a boot menu for a choice of OS's at boot-up.

---

### Post by directhex on 2011-09-04
Windows will not create more than one partition on MBR-partitioned drives (drives below 2T in size). For drives partitioned with GPT, an EFI Boot Partition is needed as well as the OS partition.

---

### Post by Jonas thomas on 2011-09-05
> **Basher101 said:**
> it will be more troublesome installing windows after ubuntu but it is possible. How big is your installation WITHOUT documents, music, downloads and everything else you can move? If you can get below 18 GB you can make a live .iso from that installation and wipe your whole drive, install windows and use the live .iso you made to reinstall your whole system as it was back and move your huge files back. This is the easiest way i can think off anyways.

Easy is good...
I did a bit of googling looking for a good how to...
Is this "the" link for making a live ISO?  [http://ubuntuforums.org/showthread.php?t=352460]("http://ubuntuforums.org/showthread.php?t=352460")

---

### Post by PatrickD-52761 on 2011-09-05
> **Mark Phelps said:**
> In my experience, Win7 only creates two partitions if the drive is completely unformatted.  You can also get around that by creating an empty partition, formatting it NTFS, and then, letting Win7 reformat that.

This is the route that I would take also. Create a partition, format it NTFS (or just leave it unformatted) and install Windows 7 there (You'll have to use the "Custom" installation, and format the partition under the Advanced button in the drives box).

Then, I would run a live CD, and repair GRUB. It'll work like a charm (at least for getting everything bootable again).  

The caveat that I would put here is to back up everything on your linux drive first.  Just in case something does go haywire.

[Here]("http://www.linuxplanet.com/linuxplanet/tutorials/6480/3/") is a tutorial that I found on repairing GRUB (back in 2009). And for a bit more clarification, [here]("http://patscompservices.blogspot.com/2009/09/restoring-your-grub-bootloader-after.html") is a link to the blog post that I did about the tutorial.

Truth is, this entire process would be simpler, if Microsoft would FIX Visual Studio. I say this, because it doesn't like (nor play well) being installed on a Virtual Machine. If they fixed that issue, then your life would be even simpler.  Create a virtual machine, install Windows 7 on it, install Visual Studio, and go.

***You COULD try this route, as I haven't tried installing Visual Studio 2010 on a VM lately--so it may work.  Install VirtualBox or VMWare Player, and make the virtual machine (I prefer VirtualBox, but your mileage may vary).  Then try installing Windows 7 in it, and try installing Visual Studio in that. If it works, activate everything and go. If not, delete it, and make a partition.

Have a great weekend :)
Patrick.

---

### Post by subhadip_sky on 2011-09-05
Read this..
[http://subhadipghosh.wordpress.com/2011/07/31/installing-windows-xp-after-ubuntu/](http://subhadipghosh.wordpress.com/2011/07/31/installing-windows-xp-after-ubuntu/)
You will need a separate partition on your hard disk to install windows. If you have that, then it should be a cake walk, just follow the instructions.
Good luck

---

### Post by afz12 on 2011-09-05
Hi Jonas

Would you consider running Win7 on a Virtual Machine? I use Virtualbox quite a lot and XP, for example, sits very well on an Ubuntu OS. It's a bit slower than running "native" but you don't need to sign out of one OS (Ubuntu) and then boot into another (Windows).

I have another notebook running Win 7 - XP and Ubuntu both sit quite well on this OS. However they only use one of the 4 cores on this notebook. Virtualbox suggests that all 4 can be used but so far this has never worked!

I would be extremely cautious myself on installing an Ubuntu OS alongside Win7 on this notebook. Win 7 probably exhausts the available drive partitions for Ubuntu and its swap partition. Also, if it fails I doubt that any recovery CD's etc will work with any confidence - for example my older Acer5920 had a known issue with these not working! (However I assume you have real installation disks). After the exercise, I lost Win7 so now this notebook runs Ubuntu and I Virtualize other OSs on top.

Good luck!

---

### Post by nipunshakya on 2011-09-05
> **Jonas thomas said:**
> Ok.. So here's the deal... I'm taking a C# class for work and need windows on my currently ubuntu only laptop. (where it not for this class I don't think I would want windows on my laptop... Since at home %99 I'm in Linux and quite happy with that)


In my opinion, if you are happy wth only ubuntu in your laptop then let it be as it is....don't install windows 7. Just for running visual studio for c# class won't be a good idea for installing windows 7(don't take pressure for yourself.)..... there is a software called codeblocks that is a open source platform.....you can try that instead of visual studio....... and as a mate suggested earlier, you can run VMware if u want only visual studio for c#.  

Still if you want to install windows seven after ubuntu, following links might help you.....
[http://ubuntuforums.org/showthread.php?t=1647103](http://ubuntuforums.org/showthread.php?t=1647103)
[http://ubuntuguide.net/how-to-install-windows-7-from-ubuntu-without-burnning-a-disc](http://ubuntuguide.net/how-to-install-windows-7-from-ubuntu-without-burnning-a-disc)

Regards, NeptuneTech

---

### Post by YesWeCan on 2011-09-05
> **Jonas thomas said:**
> Ok.. So here's the deal... I'm taking a C# class for work and need windows on my currently ubuntu only laptop. (where it not for this class I don't think I would want windows on my laptop... Since at home %99 I'm in Linux and quite happy with that)

I basically have my laptop running nice(except my wife complains that see can't dim the screen) and all my other stuff is installed and configured.

So.. Would like to  install windows 7 and visual studio without wiping out my current Ubuntu configuration? 

Is there any easy way to do this? That is Ubuntu installed first and then put windows 7 on? If someone could recommend a how to guide that would be nice.

Thanks
JT

Easy.
All you need is one primary partition slot free and, say, 20GB of unallocated disk space.

In Ububtu run
sudo sfdisk -d /dev/sda
and see if one of four slots is empty. If not, you'll have to delete one: post the output of sudo fdisk -lu for help.

If you need to make more unallocated space, boot live CD and use GParted to resize existing partition(s).

Install Win7

Boot live CD.
sudo fdisk -lu
to see the partition number of Ubuntu root, say sda1 (change as needed):
sudo mount /dev/sda1
sudo grub-install --root-partition=/mnt /dev/sda

---

### Post by YesWeCan on 2011-09-05
Alternatively, use VirtualBox
[http://www.virtualbox.org/](http://www.virtualbox.org/)

---

### Post by srs5694 on 2011-09-05
> **afz12 said:**
> Would you consider running Win7 on a Virtual Machine? I use Virtualbox quite a lot and XP, for example, sits very well on an Ubuntu OS. It's a bit slower than running "native" but you don't need to sign out of one OS (Ubuntu) and then boot into another (Windows).

I also think VirtualBox (or VMware or QEMU or some other virtualization solution) is the way to go for you. You won't need to mess with repartitioning your disk (which always creates risks), boot loader configuration, or the need to reboot into Windows. You can run your virtual machine simultaneously with your normal Linux tools.

It might even be possible to run Visual Studio in WINE, although WINE's [AppDB entry for Visual Studio](http://appdb.winehq.org/objectManager.php?sClass=application&iId=892) doesn't sound very promising. If you could get it working, it'd be a slightly cleaner solution than running a virtual machine, since Visual Studio would then run directly on your desktop and have more direct access to your system's resources (files, memory, etc.). OTOH, given the AppDB description, you could waste a lot of time just trying to get it to work and end up with nothing to show for it.

---

### Post by Cpierce on 2011-09-05
It really isn't that difficult. I install win7 on Ubuntu machines quite often. YesWeCan and the boys are telling you right. Make a backup, then use gparted on a liveCD to resize your Ubuntu partition where you want it. Then in the new unallocated space, create a new partition and format it for windows. gparted will flag this new partition as primary. Boot up on your win7 installation disk and install in the new partition. Your laptop will boot up only to windows at this point, so take advantage and finish your whole windows installation with all the rebooting that is needed. Once done, boot up on your Ubuntu liveCD and run the commands outlined by YesWeCan to repair grub startup. Then you will have the option to pick Ubuntu or Win7 at startup.

---

