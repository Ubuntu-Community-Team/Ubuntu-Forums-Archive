---
title: "Upgrade jitters"
date: 2011-09-05
forum: New to Ubuntu
---

### Post by vasa1 on 2011-09-05
With 11.10 around the corner, I'm getting the upgrade jitters since this will be my first upgrade and I'm just starting off with Linux.

**Background**
[LIST]
[*]I'm on 11.04 dual-booting with MS Windows 7, **not** Wubi.
[*]I have just the one hard disk, 500 GB, and 4 GB RAM.
[*]The computer is a Dell Inspiron 1545 (from 2009).
[*]I had MS Windows 7 installed first and then installed Ubuntu 11.04 without any advanced partitioning. In other other words, I chose the "install alongside Win 7" option and let Ubuntu do its stuff. So the booting is supervised by the GRUB loader provided by the Ubuntu install and not under control of MS Windows.
[*]I have Unity running.
[*]My internet connection is **not** 100% reliable.
[*]The only serious "customization" that I've done so far is
[LIST]
[*]to switch from the Firefox supplied by Ubuntu's repository to one direct from Mozilla
[*]to install an appindicator --- System Load Indicator 0.2 (A system load monitor capable of displaying graphs for CPU, ram, and swap space use, plus network traffic. © 2011 Michael Hofmann)
[/LIST]
[/LIST]

This is what my **fdisk -l** and **parted -l** information is:
> fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x768837b7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13        6375    51096576    7  HPFS/NTFS
/dev/sda3            6375       32508   209920000    7  HPFS/NTFS
/dev/sda4           32509       60802   227264513    5  Extended
/dev/sda5           32509       60284   223109120   83  Linux
/dev/sda6           60284       60802     4154368   82  Linux swap / Solaris


parted -l
Model: ATA WDC WD5000BPVT-0 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  106MB   105MB   primary   ntfs            boot
 2      106MB   52.4GB  52.3GB  primary   ntfs
 3      52.4GB  267GB   215GB   primary   ntfs
 4      267GB   500GB   233GB   extended
 5      267GB   496GB   228GB   logical   ext4
 6      496GB   500GB   4254MB  logical   linux-swap(v1)


With that background, I've started reading up on what the upgrade entails.

This link implies that the upgrade is relatively easy: [https://help.ubuntu.com/community/Upgrades](https://help.ubuntu.com/community/Upgrades)

Then there's this quote though it *may* be about Wubi:
> *Special considerations regarding wubi.*

Upgrading from 10.10 to 11.04 using the update manager should be painless, despite some reports to the contrary that have appeared on this forum. I have done it myself, leading to a perfectly good 11.04 installation. The problems that are reported may be due to specific hardware issues or a heavily-customised system which has affected the upgrade process. from here: [http://ubuntuforums.org/showpost.php?p=11144889&postcount=22](http://ubuntuforums.org/showpost.php?p=11144889&postcount=22)

But this link gets me worried: [http://www.dedoimedo.com/computers/ubuntu-upgrade.html](http://www.dedoimedo.com/computers/ubuntu-upgrade.html) and it links to this thread in the forum: [http://ubuntuforums.org/showthread.php?t=1305924](http://ubuntuforums.org/showthread.php?t=1305924)
[center]****[/center]
I also came across this: [http://www.linuxbsdos.com/2011/05/31/how-to-triple-boot-fedora-15-ubuntu-11-04-and-windows-7/](http://www.linuxbsdos.com/2011/05/31/how-to-triple-boot-fedora-15-ubuntu-11-04-and-windows-7/). The reason I'm mentioning this link is because I'm wondering whether it would not be a totally ridiculous, **but far safer**, way to have 11.10. I would like to know what people think about keeping 11.04 and doing a fresh install of 11.10 alongside. So I'd have Win 7, 11.04, and 11.10 all on the same hard disk. From the fdisk and parted information provided above, disk space shouldn't be an issue.
And, perhaps, if all goes well, I could later uninstall 11.04 and just have MS Windows and 11.10 dual-booting?

I hope you guys can help. This is my "work" PC and I don't want to break it by making silly mistakes!

---

### Post by saltmarshlamb on 2011-09-05
Given this
> My internet connection is not 100% reliable.
and this
> This is my "work" PC and I don't want to break it by making silly mistakes!I would not upgrade using the internet, if you decide to upgrade you can use the alternate cd rather than the livecd. 

If this is your work machine then I would say you'd be better installing 11.10 alongside the other 2 - then when you're sure all is ok - transfer anything you need from the 11.04 and remove it.

If you search the forum as far back aas you like then you'll find people who had issues with an upgrade and others who didn't - that's to be expected as the dev version only gets tried on the machines that the testers are using. 

Personally I've upgrade once since 7.04 and generally do clean installs.

---

### Post by nothingspecial on 2011-09-05
If I were you I would

1. Back up all your data.

2. Download the new version when it is released and make a live cd.

3. Test that the live cd version does what you need it to do.

4. If it does, do an upgrade either with the cd or update manager. I suggest doing it from the cd if your connection is dodgy.

5. If something goes wrong do not panic. It can go wrong but this is rare.

6. Do a clean install over your broken one. This time instead of letting the installer do the partition, during the install, choose the "something else" option.

Select the Ubuntu partition.

Choose to use it as an ext4 journaling file system

Choose to format it

Give it a mountpoint of /

Choose to use the swap partition as swap space

[SIZE="2"]**DO NOT TOUCH THE WINDOWS PARTITION**[/SIZE]

That will completely overwrite your old install, but then you already backed up your data. :)

---

### Post by vasa1 on 2011-09-05
Thank you, **saltmarshlamb** and **nothingspecial** ...

**Saltmarshlamb**, please could you clarify what you mean by **alternate CD**? I know that there is this site, [http://www.ubuntu.com/download/ubuntu/alternative-download](http://www.ubuntu.com/download/ubuntu/alternative-download), but I'm not sure the downloads over there will be what I want:
> This installation CD is suited for computers unable to run the graphical desktop based installation, either because their computer does not meet the minimum requirements for the live cd or because their computer requires configuration after the installation is complete in order to use the desktop.

**nothingspecial**, you wrote:
1. Back up all your data.
2. Download the new version when it is released and make a live cd.
3. Test that the live cd version does what you need it to do.
4. If it does, do an upgrade either with the cd or update manager. I suggest doing it from the cd if your connection is dodgy.
5. If something goes wrong do not panic. It can go wrong but this is rare.
6. Do a clean install over your broken one. This time instead of letting the installer do the partition, during the install, choose the "something else" option.
Select the Ubuntu partition.
Choose to use it as an ext4 journaling file system
Choose to format it
Give it a mountpoint of /
Choose to use the swap partition as swap space
DO NOT TOUCH THE WINDOWS PARTITION
That will completely overwrite your old install, but then you already backed up your data.

Re. points 1-3, no arguments there.
Re. 4, is there, or will there be, a provision to upgrade from the live CD? I can remember only the option to "install". It could be that I saw only that because there wasn't an existing Ubuntu version on the PC and so the option of upgrade wasn't presented.

I'm really uneasy about point 6 and hope that I won't need to go there!

I also hoped you'd comment about installing 11.10 alongside 11.04 and Windows. I'd like to take the _safest_ route. Wouldn't that be the safest route? Even if something happens, at least I'd have one functional Ubuntu ... that's my point.

And I would also like comments on the suitability of **unticking** "Download updates while installing" and "Install this third-party software" at the time of installation. I could always get them later after getting the stressful (for me) installation out of the way.

---

### Post by westie457 on 2011-09-05
> Re. 4, is there, or will there be, a provision to upgrade from the live CD? I can remember only the option to "install". It could be that I saw only that because there wasn't an existing Ubuntu version on the PC and so the option of upgrade wasn't presented.

What is implied by nothingspecial is you boot as normal then insert the LiveCD/USB, when this has been detected aurorun gives you a window that says something like 

"A medium has been inserted with executable files in it. Do you wish to install?" and 2 boxes "Cancel" & "Install".

Clicking Install will give you the option to upgrade or clean install.

---

### Post by Johnb0y on 2011-09-05
or if you have the space... use virtualbox to get the hang of it first... i would... :P

---

### Post by nothingspecial on 2011-09-05
> **vasa1 said:**
> 
Re. points 1-3, no arguments there.
Re. 4, is there, or will there be, a provision to upgrade from the live CD? I can remember only the option to "install". It could be that I saw only that because there wasn't an existing Ubuntu version on the PC and so the option of upgrade wasn't presented.

I'm really uneasy about point 6 and hope that I won't need to go there!

I also hoped you'd comment about installing 11.10 alongside 11.04 and Windows. I'd like to take the _safest_ route. Wouldn't that be the safest route? Even if something happens, at least I'd have one functional Ubuntu ... that's my point.

And I would also like comments on the suitability of **unticking** "Download updates while installing" and "Install this third-party software" at the time of installation. I could always get them later after getting the stressful (for me) installation out of the way.


The option to upgrade from the cd has only been present since 11.04. You are right about it not detecting a previous Ubuntu.

If you choose to install it alongside windows you will end up with 2 ubuntus and windows, if the installer allows it.

The upgrade, if you do it from the cd rather than the update manager should not go wrong. Unfortunately as with all things computer related sometimes they do......

.....otherwise we wouldn't have forums like these.

As long as you have your stuff backed up there should not be a problem with number 6.

You will have a clean new Ubuntu that you will have to tweak to your liking again but sometimes that's half the fun.

The partitioner will show you which partition is which. Ubuntu will be ext4 and windows will be ntfs, just make sure you pick the right one.

Like I said, In all probability nothing will go wrong, I just laid out what to do just in case.

---

### Post by vasa1 on 2011-09-05
> **nothingspecial said:**
> The option to upgrade from the cd has only been present since 11.04. You are right about it not detecting a previous Ubuntu.

If you choose to install it alongside windows you will end up with 2 ubuntus and windows, if the installer allows it.

The upgrade, if you do it from the cd rather than the update manager should not go wrong. Unfortunately as with all things computer related sometimes they do......

.....otherwise we wouldn't have forums like these.

As long as you have your stuff backed up there should not be a problem with number 6.

You will have a clean new Ubuntu that you will have to tweak to your liking again but sometimes that's half the fun.

The partitioner will show you which partition is which. Ubuntu will be ext4 and windows will be ntfs, just make sure you pick the right one.

Like I said, In all probability nothing will go wrong, I just laid out what to do just in case.

Thanks for taking the time to respond. I agree that something *can* go wrong but I'm hoping to make it as difficult as possible for that to happen :D

Here's hoping that the new upgrade will go smoothly for as many folks as possible :)

---

### Post by bodhi.zazen on 2011-09-05
> **Johnb0y said:**
> or if you have the space... use virtualbox to get the hang of it first... i would... :P

The only problem with virtualbox is that it does not run on your hardware, so it is of limited utility.

The most important part of upgrading is to make a backup of you data first, after then everything else is rather trivial.

---

### Post by Johnb0y on 2011-09-05
> **bodhi.zazen said:**
> The only problem with virtualbox is that it does not run on your hardware, so it is of limited utility.

The most important part of upgrading is to make a backup of you data first, after then everything else is rather trivial.

was basically meaning the "steps" and "dealing" with the backups, saving settings, etc... 

> to get the hang of it first...

---

### Post by Johnb0y on 2011-09-05
> **nothingspecial said:**
> As long as you have your stuff backed up there should not be a problem

p.s. as nothingspecial says... just back up the stuff and basically give it a shot!:P

---

