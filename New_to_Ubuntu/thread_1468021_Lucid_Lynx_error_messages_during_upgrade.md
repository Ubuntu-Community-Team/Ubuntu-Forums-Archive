---
title: "Lucid Lynx error messages during upgrade"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by carusoswi on 2010-05-01
When I fired up my 9.10 version of Ubuntu Studio this morning, there were upgrades available.  I downloaded/installed them.  Then, I noticed that an upgrade was also available, so I clicked the button to upgrade the system to 10.04 LTS.

During the install, I received the following error message with suggestions that I might want to file a bug report (tried to do that, but, as simple as it sounds, I was unsuccessful - I'll post elsewhere on that).

The error messages involve the following two items:

/var/cache/apt/archives/gvfs-bin-1.6.0+git20100414-0ubuntu1_i386.deb

gvfs-bin

It appears that these two items are related.  I do not know what they do or what effect their current state is on my system.

As the upgrade routine finished, it presented me with a message that my system could not be upgraded due to problems related to this gvfs-bin.  However, when I rebooted my system, it appears that I am now running version 10.04 - at least, that's what the 'about Ubuntu' screen is reporting.

I haven't done much exploring, so I cannot tell you what is different about the system at this time.  It does appear pretty much the same to me.

Advice would be most welcome.

Please note that I did setup a Launchpad account and tried to post a bug report, but got only as far as the ALT F2, screen.  I don't really know what package name to enter there.

Thanks in advance for your assistance.

Caruso

---

### Post by dracayr on 2010-05-01
[http://en.wikipedia.org/wiki/GVFS](http://en.wikipedia.org/wiki/GVFS)

do you know what the errors were? In any case, just try ```
sudo apt-get update
sudo apt-get upgrade
```

If anything wasn't correctly upgraded, those commands will do that (And you'll be able to copy-paste the error messages, if any)

---

### Post by carusoswi on 2010-05-01
> **dracayr said:**
> [http://en.wikipedia.org/wiki/GVFS](http://en.wikipedia.org/wiki/GVFS)

do you know what the errors were? In any case, just try ```
sudo apt-get update
sudo apt-get upgrade
```

If anything wasn't correctly upgraded, those commands will do that (And you'll be able to copy-paste the error messages, if any)

Thanks for the quick response.  I'll run those commands.  I also note that I cannot access my dual boot XP OS.  It shows up as a choice when I re-boot, but if I select it, the result is a blinking cursor on a blank black screen.

As I recall, version 9.04 and forward do no longer use Grub as I used to know it.  Suggestions on how to fix the dual boot issue would also be welcome.

Caruso

---

### Post by carusoswi on 2010-05-01
> **dracayr said:**
> [http://en.wikipedia.org/wiki/GVFS](http://en.wikipedia.org/wiki/GVFS)

do you know what the errors were? In any case, just try ```
sudo apt-get update
sudo apt-get upgrade
```

If anything wasn't correctly upgraded, those commands will do that (And you'll be able to copy-paste the error messages, if any)

Oh, and the errors were not explained in any detail at all.  Just that there was a problem with them.

Caruso

---

### Post by carusoswi on 2010-05-01
> **dracayr said:**
> [http://en.wikipedia.org/wiki/GVFS](http://en.wikipedia.org/wiki/GVFS)

do you know what the errors were? In any case, just try ```
sudo apt-get update
sudo apt-get upgrade
```

If anything wasn't correctly upgraded, those commands will do that (And you'll be able to copy-paste the error messages, if any)

Ok, running apt-get upgrade returned an unmet dependency message.  Running again with -f corrected the problem.

Now, I'll try rebooting to see if XP is available.

Thanks.

Caruso

---

### Post by carusoswi on 2010-05-01
Ok, still no go with XP dual boot.  Still need some help to correct that.
Thanks.

Caruso

---

### Post by gwpryz on 2010-05-01
> **carusoswi said:**
> When I fired up my 9.10 version of Ubuntu Studio this morning, there were upgrades available.  I downloaded/installed them.  Then, I noticed that an upgrade was also available, so I clicked the button to upgrade the system to 10.04 LTS.

During the install, I received the following error message with suggestions that I might want to file a bug report (tried to do that, but, as simple as it sounds, I was unsuccessful - I'll post elsewhere on that).

The error messages involve the following two items:

/var/cache/apt/archives/gvfs-bin-1.6.0+git20100414-0ubuntu1_i386.deb

gvfs-bin

It appears that these two items are related.  I do not know what they do or what effect their current state is on my system.

As the upgrade routine finished, it presented me with a message that my system could not be upgraded due to problems related to this gvfs-bin.  However, when I rebooted my system, it appears that I am now running version 10.04 - at least, that's what the 'about Ubuntu' screen is reporting.

I haven't done much exploring, so I cannot tell you what is different about the system at this time.  It does appear pretty much the same to me.

Advice would be most welcome.

Please note that I did setup a Launchpad account and tried to post a bug report, but got only as far as the ALT F2, screen.  I don't really know what package name to enter there.

Thanks in advance for your assistance.

Caruso

Karmic offered an upgrade to 10.04 LTS this morning, and the result was disaster. On reboot I had the following message: "[  07115221 Kernel Panic] - not syncing VFS: Unable to mount rootfs on unknown block (0,0)" Before exiting Ubuntu I had been warned, however, that the system was now corrupted. During installation I received several error messages about unsuccessful installs, along with invitations to file bug reports. Just to mention a couple of examples: linux-image-generic and memtest (the last mention of error). The question which might be asked is how stable the final release of Lucid Lynx really is.

---

### Post by vuthailinh on 2010-05-01
last week I've updated karmic to lucid RC by using alternative cd . Today, Update manager report 252 parkage available but I don't want using internet connection because it very slow... I've downloaded final cd but cannot upgrade ubuntu by using cd, update manager requires me using internet connection....
Please help me up-to-date...

---

### Post by carusoswi on 2010-05-01
> **gwpryz said:**
> Karmic offered an upgrade to 10.04 LTS this morning, and the result was disaster. On reboot I had the following message: "[  07115221 Kernel Panic] - not syncing VFS: Unable to mount rootfs on unknown block (0,0)" Before exiting Ubuntu I had been warned, however, that the system was now corrupted. During installation I received several error messages about unsuccessful installs, along with invitations to file bug reports. Just to mention a couple of examples: linux-image-generic and memtest (the last mention of error). The question which might be asked is how stable the final release of Lucid Lynx really is.

This is not typical of Ubuntu to mess up my system during an upgrade.  I guess I'll have to use my XP install disc to go to the XP repair console and fix the XP mbr which will restore XP accessibility, but will likely require me to reinstall Ubuntu from scratch.

I used to be able to just back up my Grub file, but the last time I tried, I came to understand that newer versions of Ubuntu don't use the old type Grub file anymore.

Hopefully, someone with more knowledge of the problem can offer a solution.  I have work to do in XP today, so I'll need to get in there soon, although I was not relishing spending any large amount of time rebuilding my system today.

I regret having run that ugrade, now.

The good news is that no matter to what degree my OS's are messed up, I will not lose any important data.  I just didn't want to spend the time to have to reinstall everything.

Caruso

---

### Post by zatnuviz on 2010-05-02
Well i have had the same problem you had, im running windows 7 and lucid by now, but was running karmic, and after the upgrade due to upgrade errors lost my close, maximize, restore, buttons and at teh last step my pc stop at grub telling me it cant load further, and after that what i have done is

Using a karmic Koala (ubuntu 9.10) disc or an lucid linx (10.4) disc ( even better ) i do the following to recover my system



  Reinstalling GRUB 2
There may be times when a user needs to either move or reinstall a GRUB 2 installation. GRUB 2 needs to be reinstalled when a user is presented with a blank screen with only the word "GRUB", no prompt, and no ability to enter commands. This often happens when the MBR of the booting device is altered and GRUB 2 is removed, such as when Windows is installed after Ubuntu. Additionally, if a user cannot boot into an operating system at all, even using the rescue mode mode, a complete reinstallation of GRUB 2 may be necessary.

Reinstalling from LiveCD
If you cannot boot from GRUB 2 review the section Boot Problems & Rescue Mode. If a reinstall becomes necessary follow these instructions. Two methods are presented; both require booting from a LiveCD (Ubuntu 9.10, Karmic Koala or later version). If the first method does not work, follow the second method, which is more complex and contains more options and instructions.

SIMPLEST - Copy GRUB 2 Files from the LiveCD
This is a quick and simple method of restoring a broken system's GRUB 2 files. The terminal is used for entering commands and the user must know the device name/partition of the installed system (sda1, sdb5, etc). The problem partition is located and mounted from the LiveCD. The files are then copied from the LiveCD libraries to the proper locations and MBR. It requires the least steps and fewer command line entries than the following methods.

Boot to the LiveCD Desktop (Ubuntu 9.10 or later).
Open a terminal by selecting Applications, Accessories, Terminal from the menu bar.
Determine the partition with the Ubuntu installation. The fdisk option "-l" is a lowercase "L".

sudo fdisk -l

If the user isn't sure of the partition, look for one of the appropriate size or formatting.
Running sudo blkid may provide more information to help locate the proper partition, especially if the partitions are labeled. The device/drive is designated by sdX, with X being the device designation. sda is the first device, sdb is the second, etc. For most users the MBR will be installed to sda, the first drive on their system. The partition is designated by the Y. The first partition is 1, the second is 2. Note the devices and partitions are counted differently.
Mount the partition containing the Ubuntu installation.

sudo mount /dev/sd''xY'' /mnt

Example: sudo mount /dev/sda1 Note: If the user has a separate /boot partition, this must be mounted to /mnt/boot
Run the grub-install command as described below. This will reinstall the GRUB 2 files on the mounted partition to the proper location and to the MBR of the designated device.

sudo grub-install --root-directory=/mnt/ /dev/sdX

Example: sudo grub-install --root-directory=/mnt/ /dev/sda

Reboot
Refresh the GRUB 2 menu with sudo update-grub

If the user wishes to explore why the system failed, refer to Post-Restoration Commands section below.

i get this from [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) ( thx for it )

Basically you need to install it in the linux partition, and dont forget to do the last step after reboot because if not, it will not load your windows, after that you can start enjoying lucid, btw, is faster that karmic.:popcorn:

---

### Post by carusoswi on 2010-05-02
> **zatnuviz said:**
> Well i have had the same problem you had, im running windows 7 and lucid by now, but was running karmic, and after the upgrade due to upgrade errors lost my close, maximize, restore, buttons and at teh last step my pc stop at grub telling me it cant load further, and after that what i have done is

Using a karmic Koala (ubuntu 9.10) disc or an lucid linx (10.4) disc ( even better ) i do the following to recover my system



  Reinstalling GRUB 2
There may be times when a user needs to either move or reinstall a GRUB 2 installation. GRUB 2 needs to be reinstalled when a user is presented with a blank screen with only the word "GRUB", no prompt, and no ability to enter commands. This often happens when the MBR of the booting device is altered and GRUB 2 is removed, such as when Windows is installed after Ubuntu. Additionally, if a user cannot boot into an operating system at all, even using the rescue mode mode, a complete reinstallation of GRUB 2 may be necessary.

Reinstalling from LiveCD
If you cannot boot from GRUB 2 review the section Boot Problems & Rescue Mode. If a reinstall becomes necessary follow these instructions. Two methods are presented; both require booting from a LiveCD (Ubuntu 9.10, Karmic Koala or later version). If the first method does not work, follow the second method, which is more complex and contains more options and instructions.

SIMPLEST - Copy GRUB 2 Files from the LiveCD
This is a quick and simple method of restoring a broken system's GRUB 2 files. The terminal is used for entering commands and the user must know the device name/partition of the installed system (sda1, sdb5, etc). The problem partition is located and mounted from the LiveCD. The files are then copied from the LiveCD libraries to the proper locations and MBR. It requires the least steps and fewer command line entries than the following methods.

Boot to the LiveCD Desktop (Ubuntu 9.10 or later).
Open a terminal by selecting Applications, Accessories, Terminal from the menu bar.
Determine the partition with the Ubuntu installation. The fdisk option "-l" is a lowercase "L".

sudo fdisk -l

If the user isn't sure of the partition, look for one of the appropriate size or formatting.
Running sudo blkid may provide more information to help locate the proper partition, especially if the partitions are labeled. The device/drive is designated by sdX, with X being the device designation. sda is the first device, sdb is the second, etc. For most users the MBR will be installed to sda, the first drive on their system. The partition is designated by the Y. The first partition is 1, the second is 2. Note the devices and partitions are counted differently.
Mount the partition containing the Ubuntu installation.

sudo mount /dev/sd''xY'' /mnt

Example: sudo mount /dev/sda1 Note: If the user has a separate /boot partition, this must be mounted to /mnt/boot
Run the grub-install command as described below. This will reinstall the GRUB 2 files on the mounted partition to the proper location and to the MBR of the designated device.

sudo grub-install --root-directory=/mnt/ /dev/sdX

Example: sudo grub-install --root-directory=/mnt/ /dev/sda

Reboot
Refresh the GRUB 2 menu with sudo update-grub

If the user wishes to explore why the system failed, refer to Post-Restoration Commands section below.

i get this from [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) ( thx for it )

Basically you need to install it in the linux partition, and dont forget to do the last step after reboot because if not, it will not load your windows, after that you can start enjoying lucid, btw, is faster that karmic.:popcorn:

Thanks for an informative answer.
I downloaded the live cd, tried to install it, but after completion, boot up returned an error message that none of the basic folders required for Ubuntu were present (no desktop, no home, etc.).  I am then greeted by a blank Ubuntu background screen.

I did repair my XP installation using the XP install disk, so that's working.  No idea what went wrong with the 10.04 live cd install (or the upgrade for that matter).

I am becoming suspicious of this 10.04 release.

Caruso (communicating from a different machine now).

---

