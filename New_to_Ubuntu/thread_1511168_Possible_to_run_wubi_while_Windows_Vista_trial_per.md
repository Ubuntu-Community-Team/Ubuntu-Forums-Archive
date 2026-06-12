---
title: "Possible to run wubi while Windows Vista trial period has expired?"
date: 2010-06-16
forum: New to Ubuntu
---

### Post by Ferto on 2010-06-16
I had to re-install Windows Vista, but I lost my registration code. I've got 11 days left to register. If I install wubi next to Vista, will it be possible for me to boot it when the 11 days have passed? Is there a better alternative for installing Ubuntu that can be done in 11 days by a novice?

---

### Post by mbzn on 2010-06-16
Takes about 30minutes to format and install Ubuntu only

---

### Post by warfacegod on 2010-06-16
I've managed to get the process down to about seven minutes. To answer your question, probably not.

---

### Post by mbzn on 2010-06-16
yeh yeh ok... I use ultimate edition it's a 9.5 GiB install so takes me about 1 hour from cd and 30min from flash drive(never actually used a stopwatch)

---

### Post by AlanR8 on 2010-06-16
Just phone "MicroI'll takeallyourmoney" and ask for a new activation code.......

OR

Install 10.04 and enjoy!

---

### Post by Ferto on 2010-06-16
Can anyone please give me instructions on how to install Ubuntu only?

---

### Post by irv on 2010-06-16
If you installed wubi, I take it you have the CD. Just put it in the CD drive and boot your PC. if you BIOS is set to boot from the CD it should boot the live CD and you will find a Icon on the desktop to install Ubuntu. When it come to installing on the Hard Drive just select use the entire drive and then set back and let it install.
Edit: maybe I should have told you to backup all your data files before doing this and then after the install you will need to copy your files over to your /home/"yourname" directory.

---

### Post by Ferto on 2010-06-16
> **irv said:**
> If you installed wubi, I take it you have the CD. Just put it in the CD drive and boot your PC. if you BIOS is set to boot from the CD it should boot the live CD and you will find a Icon on the desktop to install Ubuntu. When it come to installing on the Hard Drive just select use the entire drive and then set back and let it install.
Edit: maybe I should have told you to backup all your data files before doing this and then after the install you will need to copy your files over to your /home/"yourname" directory.

I don't have a cd. I just install it via Windows. Also, my cd drive is broken. :\ I think. Or I just can't use it because Windows is not registered or something, but Windows doesn't even connect to it.

---

### Post by irv on 2010-06-16
> **Ferto said:**
> I don't have a cd. I just install it via Windows. Also, my cd drive is broken. :\ I think. Or I just can't use it because Windows is not registered or something, but Windows doesn't even connect to it.

There is a way to install it with a USB stick. I have never done this so maybe someone who has can tell you how to do it.

---

### Post by bodhi.zazen on 2010-06-16
1. IMO, wubi is for trial only. If you have decided to stay with Ubuntu , perform a standard install.

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

You can boot from a USB. Download and install unetbootin in Windows and use that to make a bootable USB driver.

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

2. If you wish to continue to use Windows, contact Microsoft ;)

---

### Post by mbzn on 2010-06-16
Try 'Startup Disk Creator' from your current wubi install.
System>Administration>Startup Disk Creator
Use the iso you installed Ubuntu from.

---

### Post by QIII on 2010-06-16
If your CD/DVD is really tango uniform, your BIOS will not let you boot from USB and you can't follow  bodhi.zazen's advice, go over to a geeky friend's house and see if he has an external CD/DVD burner he'll lend you for a few hours.

Download, burn, install and give your friend his CD/DVD burner back.  Make a copy of the CD/DVD for your buddy while you're at it.

That, or you can probably pick up a CD/DVD burner for a few dollars if that's possible.

---

### Post by Ferto on 2010-06-17
So if I understand everything correctly, using Unetbootin, it's possible to go from Windows Vista to ubuntu only without using any removable devices? So do I just select Ubuntu and then the C:\ drive and start installing? Is it that easy?

---

### Post by CharlesA on 2010-06-17
Unetbootin is used to create a bootable USB from an ISO, not install to the hard drive.

You would boot off the USB drive and install Ubuntu that way.

---

### Post by steveneddy on 2010-06-17
> **bodhi.zazen said:**
> 1. IMO, wubi is for trial only. If you have decided to stay with Ubuntu , perform a standard install.

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

You can boot from a USB. Download and install unetbootin in Windows and use that to make a bootable USB driver.

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

2. If you wish to continue to use Windows, contact Microsoft ;)

Best advice.

I agree with bodi - partition the drive and install Ubuntu on it's own drive.

From a [link in my sig]("http://ubuntuguide.org/wiki/Ubuntu:Lucid"):

>  ...the installation requires an intact functioning Windows system...

 A permanent Ubuntu installation should be installed in its own partition, with its own filesystem, and should not rely on Windows.

Follow the links to instruction on installing Ubuntu separately from Windows.

---

### Post by Ferto on 2010-06-17
> **steveneddy said:**
> Best advice.

I agree with bodi - partition the drive and install Ubuntu on it's own drive.

From a [link in my sig]("http://ubuntuguide.org/wiki/Ubuntu:Lucid"):



Follow the links to instruction on installing Ubuntu separately from Windows.

And this can be done without using removable devices?

---

### Post by sadaruwan12 on 2010-06-17
You could get a key from uSoft if you have lost your key I think and if your google you might be able to find some ways to extend your trail period any way come into the enlightened world of Linux and see the difference.

To install Ubuntu 10.04 on to your HDD you need to boot it from a optical device or a USB pen drive. So you've said that your optical drive is not working the best way is to use the USB pen drive.

If you Vista is still working follow this [link]("http://unetbootin.sourceforge.net/") and download the bootable pen creator software download the windows version.

After that you need the .ISO file to write to the USB pen you can get it from [here]("http://www.ubuntu.com/desktop/get-ubuntu/download"). This page also shows you how to install the system as well.

Moving on after downloading the .ISO file use Unebootin to crate your bootable USB pen drive it's very simple to create it and follow these [instructions]("http://unetbootin.sourceforge.net/#install").

And also when your installing just choose to use the entire hard disk for you Ubuntu that'll wipe the other unwanted things.

Also remember to back up your important data before you do the complete system install.

I hope this helps you

---

### Post by warfacegod on 2010-06-17
> **CharlesA said:**
> Unetbootin is used to create a bootable USB from an ISO, not install to the hard drive.

You would boot off the USB drive and install Ubuntu that way.

You can tell unetbootin to use an HDD as well. I have no idea what it will do or if it even works, having never tried it.

---

### Post by Ferto on 2010-06-17
Thanks for all the replies explaining how this can be done with a USB drive. However, I'm not sure whether my notebook is able to boot from USB at all. It has failed in the past, so I'm only trying it again if there is no other way.

So there is no way at all to install Ubuntu that is is independant from Windows Vista without the use of removable media such as disc's or usb drives?

---

### Post by warfacegod on 2010-06-17
> **Ferto said:**
> Thanks for all the replies explaining how this can be done with a USB drive. However, I'm not sure whether my notebook is able to boot from USB at all. It has failed in the past, so I'm only trying it again if there is no other way.

So there is no way at all to install Ubuntu that is is independant from Windows Vista without the use of removable media such as disc's or usb drives?

There *might* be. Try Gizmo (I think that's the name. Google it.) from Windows and use it to mount an Ubuntu CD. If it loads properly (or at all), you *should* be able to use it then to create a partition with Gparted  and then install Ubuntu into that partition.

**_Fair Warning:_** This is totally theoretical on my part from an app I'm remembering from over three years ago. I have no idea if this will work and, if it does, I don't know if the system will even be bootable. This may just cause serious damage or it might work flawlessly.

---

### Post by Ferto on 2010-06-17
Googling Gizmo resulted in something entirely different.

Has anyone ever tried such a thing succesfully?
What happens when you perform Unetbootin an select drive C:\ instead of a usb drive? Or drive D:\?

---

### Post by warfacegod on 2010-06-17
Here's Gizmo: [http://arainia.com/software/gizmo/overview.php?nID=4]("http://arainia.com/software/gizmo/overview.php?nID=4")

---

### Post by RJ12 on 2010-06-18
These are from the unetbootin

```
...Otherwise, if you did a "frugal install" by selecting "Hard Disk" as your install target, select the UNetbootin entry from the Windows Boot Menu as the system boots up.
```

I don't know how well this would work, if you install Ubuntu to the full hard drive, won't that wipe out the install source? Or is everything loaded into memory?

---

### Post by jimv on 2010-06-18
Since you never actually boot into Windows when using Ubuntu that's been installed with Wubi, it doesn't matter if Windows expires or not.

---

### Post by Ferto on 2010-06-18
> **jimv said:**
> Since you never actually boot into Windows when using Ubuntu that's been installed with Wubi, it doesn't matter if Windows expires or not.

That's a good thing to hear. But you do use Windows Startup Manager. Doesn't that expire as well?

---

### Post by warfacegod on 2010-06-18
Okay. I just used unetbootin on my wife's computer to turn her (my) 40 GB IDE drive into a massive LiveUSB. I then had to disassemble my external DVD burner and connect the HDD instead. It worked! Flawlessly, in fact. I used it to reinstall GRUB2 to make my laptop bootable again (don't ask).

You could do something similar connecting the drive internally to the computer.

---

### Post by Ferto on 2010-06-22
> **warfacegod said:**
> Okay. I just used unetbootin on my wife's computer to turn her (my) 40 GB IDE drive into a massive LiveUSB. I then had to disassemble my external DVD burner and connect the HDD instead. It worked! Flawlessly, in fact. I used it to reinstall GRUB2 to make my laptop bootable again (don't ask).

You could do something similar connecting the drive internally to the computer.

So what do I do? Use Unetbootin on drive D:\?

---

### Post by warfacegod on 2010-06-22
Assuming there is nothing of value on the D: drive then yes.

---

### Post by Ferto on 2010-06-23
Thanks a lot guys! You really are great. Really shows why Ubuntu is so great. It has such an awesome community. But I'm afraid I'm stuck again.

For some reason, it didn't work with D:\ so I did it with C:\. It worked, but now I'm here... Well, I gues I'll just make a screenshot to show what's up.

[http://img155.imageshack.us/img155/8192/screenshotdr.png](http://img155.imageshack.us/img155/8192/screenshotdr.png)

How do I define a root file system?

EDIT: On the other side, my "usb drive" is actually on the C:\ drive, so I can't lose it anyway. Is there even a reason why I would want to install Ubuntu on my hard drive another time? Does my current way of booting hold any limitations?

---

### Post by RJ12 on 2010-06-23
> **Ferto said:**
> Thanks a lot guys! You really are great. Really shows why Ubuntu is so great. It has such an awesome community. But I'm afraid I'm stuck again.

For some reason, it didn't work with D:\ so I did it with C:\. It worked, but now I'm here... Well, I gues I'll just make a screenshot to show what's up.

[http://img155.imageshack.us/img155/8192/screenshotdr.png](http://img155.imageshack.us/img155/8192/screenshotdr.png)

How do I define a root file system?

EDIT: On the other side, my "usb drive" is actually on the C:\ drive, so I can't lose it anyway. Is there even a reason why I would want to install Ubuntu on my hard drive another time? Does my current way of booting hold any limitations?


On the partition that you are going to install it to, click change and where it says Mount Point or Use as, click the drop down box and choose / this will set it as the root file system

It looks as the one you would be doing is /dev/sda5

you will not be able to do /dev/sda2, as you are using that to install from.

---

### Post by RJ12 on 2010-06-23
> **Ferto said:**
> ...

EDIT: On the other side, my "usb drive" is actually on the C:\ drive, so I can't lose it anyway. Is there even a reason why I would want to install Ubuntu on my hard drive another time? Does my current way of booting hold any limitations?

Well, it is supposed to be slower the "WUBI" way, and is more sensitive to hard resets. WUBI was never made to be a permanent dual boot solution.

---

### Post by Ferto on 2010-06-23
> **RJ12 said:**
> On the partition that you are going to install it to, click change and where it says Mount Point or Use as, click the drop down box and choose / this will set it as the root file system

It looks as the one you would be doing is /dev/sda5

you will not be able to do /dev/sda2, as you are using that to install from.

There's two drop-down boxes. One is called Mount Point, but it doesn't work. It's gray in the sense when you can't click on it. The other one is called Use As. It's option are:
- Ext4 journaling file system
- Ext3 journaling file system
- Ext2 file system
- ReiserFS journaling file system
- JFS journaling file system
- XFS journaling file system
- FAT16 file system
- FAT32 file system
- nfts
- swap area
- do not use the partition

Also there's a check box that says "Format the partition". Then, there's a fill-in box that says "New partition size in megabytes". Currently, the number "45913" is filled in.

---

### Post by RJ12 on 2010-06-23
> **Ferto said:**
> There's two drop-down boxes. One is called Mount Point, but it doesn't work. It's gray in the sense when you can't click on it. The other one is called Use As. It's option are:
- Ext4 journaling file system
- Ext3 journaling file system
- Ext2 file system
- ReiserFS journaling file system
- JFS journaling file system
- XFS journaling file system
- FAT16 file system
- FAT32 file system
- nfts
- swap area
- do not use the partition

Also there's a check box that says "Format the partition". Then, there's a fill-in box that says "New partition size in megabytes". Currently, the number "45913" is filled in.

You will need to choose the EXT4 File System under Use As and check the box "Format" (I think it checks auto.) Then it should allow you to choose mount point.

Make sure all information you need on this partition is backed up. I think this would be "D:\" on Windows

---

### Post by Ferto on 2010-06-23
> **RJ12 said:**
> You will need to choose the EXT4 File System under Use As and check the box "Format" (I think it checks auto.) Then it should allow you to choose mount point.

Make sure all information you need on this partition is backed up. I think this would be "D:\" on Windows

Thanks a lot! It's working. But now it's suggesting I use one of the partitions as a swapspace. Is this necessary?

---

### Post by RJ12 on 2010-06-23
How much RAM is in the computer?

---

### Post by Ferto on 2010-06-23
> **RJ12 said:**
> How much RAM is in the computer?

994 mb.

---

### Post by RJ12 on 2010-06-23
> **Ferto said:**
> 994 mb.

Ok, we will want at least a partition with at least 1 gb of space for swap (after all you will need this for sleep function).

Open GParted (System > Admin. > GParted (or Partition Editor))

Now lets shrink /dev/sda5

Shrink it down about 1 GB

Then close the Ubuntu Installer and open it again, choose manual and follow the steps you have been doing.

Only now for the 1 GB partition you need to click change, and where it says Use As, choose Swap Area


I don't know if there is a better way, but this seems pretty safe

---

### Post by Ferto on 2010-06-23
> **RJ12 said:**
> Ok, we will want at least a partition with at least 1 gb of space for swap (after all you will need this for sleep function).

Open GParted (System > Admin. > GParted (or Partition Editor))

Now lets shrink /dev/sda5

Shrink it down about 1 GB

Then close the Ubuntu Installer and open it again, choose manual and follow the steps you have been doing.

Only now for the 1 GB partition you need to click change, and where it says Use As, choose Swap Area


I don't know if there is a better way, but this seems pretty safe

There already was around 3 gb in use so I figured I'd shrink it to 5 gb. It' still busy. It's a pity you can't see a progress bar or something. Thanks a lot in advance. I've got the feeling this is gonna work. :P I'll post again when I succeed and boot.

---

### Post by RJ12 on 2010-06-23
Cool, you welcome!! Hope to see you in Ubuntu :KS
:popcorn:

---

### Post by Ferto on 2010-06-23
Halfway through it says it cannot unmount the partitions on /cdrom. My cd-drive doesn't work. I don't know if that's part of the problem.

---

### Post by RJ12 on 2010-06-23
Is the installer running yet? If not close it, then open a terminal and try typing this command in

```
sudo umount -l -r -f /cdrom
```

Then press enter, and then try the installer again.

---

### Post by penguinv on 2010-06-23
> **Ferto said:**
> I had to re-install Windows Vista, but I lost my registration code. I've got 11 days left to register. If I install wubi next to Vista, will it be possible for me to boot it when the 11 days have passed? Is there a better alternative for installing Ubuntu that can be done in 11 days by a novice?

Yes it is because you choose which you enter from Grub which comes up in advance of any windows startup. So you are safe with that.

The annoying thing is that you can get your data out of a wubi (fake partition) section _only_ by booting up from that drive. Be warned. You cannot copy the drive and find your wubi info later.

More Caveat: Remember on any drive, Windows insists on reformatting the entire drive when it installs. So if you ever want Windows on a driev that comes first. Then you can repartion, install anything/s, then fix Grub/2 if needed to give access to both partitions as boot.

Remember please: Think from clarity, not wishes. It is what it is.

Best of Luck!

---

### Post by Windows Nerd on 2010-06-23
> **Ferto said:**
> I don't have a cd. I just install it via Windows. Also, my cd drive is broken. :\ I think. Or I just can't use it because Windows is not registered or something, but Windows doesn't even connect to it.
If your CD drive is not working in Windows it may be due to a broken driver. My CD drive stopped working last summer this way, but it worked fine to boot from a CD from BIOS and it worked fine on Linux.

Scott

---

