---
title: "How the hell do I remove grub from xp drive"
date: 2010-03-19
forum: New to Ubuntu
---

### Post by Doctor Mike on 2010-03-19
grub got installed on my xp drive during an update from karmic 9.10 to lucid beta1. It also won't boot my xp. Ubuntu is on second drive and that's where the grub should be. Hate grub, that's why I isolated my xp drive before installing ubuntu. Please help as my imaging software is on xp and I'd like to be rid of the current lucid.

---

### Post by NightwishFan on 2010-03-19
Restore the MBR from a Windows Xp repair disk or the Super Grub Disk.
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by Doctor Mike on 2010-03-19
> **NightwishFan said:**
> Restore the MBR from a Windows Xp repair disk or the Super Grub Disk.
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)Ya did the repair disk... no joy so I resored OS from image (macrium & bart pe). Funny I thought I should back up both OS's before trying the beta, but only made a fresh copy of ubuntu 9.10 (xp was only ten days old and underused).

Any idea what the heck a ubuntu upgrade was doing installing grub to my second drive, or did it get confused not recognizing (or using) bios boot order?

In any case ubuntu should not install additional copies of the grub without specific user confirmation at install/upgrade.

---

### Post by NightwishFan on 2010-03-19
Honestly I have never had such issues happen to me. In hindsight you could have manually restored grub from ubuntu, which is easy, but I assumed you wanted a restored windows install first.

---

### Post by Doctor Mike on 2010-03-19
> **NightwishFan said:**
> Honestly I have never had such issues happen to me. In hindsight you could have manually restored grub from ubuntu, which is easy, but I assumed you wanted a restored windows install first.the copy of grub on the ubuntu drive works when xp is selected without fix, but a second copy of grub got installed on xp drive. I think it's because ubuntu does not use bios info and the first boot drive without boot order change is the xp drive. Still sounds like a confirmation with user script would be useful.

heads up don't update your lucid beta1 at this time... updates are causing serious problems. Check development testing before you update.

---

### Post by oldfred on 2010-03-19
We have seen this on removeable drives where it keeps installing to the internal. I found a note that it has been fixed in Lucid.

Comments I have saved from other posts:
Important for external removeable drives: Fixed 2010-02-04 for Lucid
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/496435](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/496435)
reinstalls grub and allows choice of which drive to install to. Choose boot drive if not sda
sudo dpkg-reconfigure grub-pc
I finally found out how to prevent the MBR to be overwritten.
I ran dpkg-reconfigure grub-pc and deselected /dev/sda which meant that the values field for grub-pc/install_devices in /var/cache/apt/config.dat is now empty. Then nothing is written to the MBR or the boot sector when grub-pc gets updated. Occasionally I should probably rerun manually grub-install /dev/sda2 after grub-pc package updates to keep stage1 install in sync.

---

### Post by Doctor Mike on 2010-03-23
> **oldfred said:**
> We have seen this on removeable drives where it keeps installing to the internal. I found a note that it has been fixed in Lucid.

Comments I have saved from other posts:
Important for external removeable drives: Fixed 2010-02-04 for Lucid
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/496435](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/496435)
reinstalls grub and allows choice of which drive to install to. Choose boot drive if not sda
sudo dpkg-reconfigure grub-pc
I finally found out how to prevent the MBR to be overwritten.
I ran dpkg-reconfigure grub-pc and deselected /dev/sda which meant that the values field for grub-pc/install_devices in /var/cache/apt/config.dat is now empty. Then nothing is written to the MBR or the boot sector when grub-pc gets updated. Occasionally I should probably rerun manually grub-install /dev/sda2 after grub-pc package updates to keep stage1 install in sync.
Even though I've marked this thread as solved, it appears that I was not clear about my system configuration and installation of karmic 9.10 contributing to the problem I had.

I've two internal drives. sda & sdb. XP is installed on sda and does not like to be the slave drive, so it will always be sda. Karmic 9.10 was installed on sdb, but I physically disconnected the sda drive to ensure that grub was not installed to it. So grub would have thought it was being installed on sda.

The reason for dong this was to ensure that a failure of the bootloader would not prevent me from accessing my XP system where I have my imaging tools.

After installing Karmic 9.10 I updated the grub so I could boot sda XP from the grub on sdb HDD.

What bothered me was that when I choose to test run lucid beta the update installed grub2 to, not one, but both drives (the sda install being corrupt and not removable for some reason) without a confirmation dialog popping up saying, 'do you wish to install grub2 on sda, sdb, or both'. I was only able to recover because I had tools for recovery of total data loss.

Lots of windows users are not so well prepared, so I think this is a significant issue on install or update. There's rarely just one person who uses the wrong end of a monkey wrench.

Edit: read bug report and it seems that the issue is fully understood and fix is underway... I will now change my signature line, "Grub2 likes both your HDDs, Both HDD's don't like Grub2, MMMMMMMMMMMMMM  Chocolate Computer Brick."

---

### Post by oldfred on 2010-03-23
I also just installed Lucid beta and I boot from sdc, but it installed to sda. The first time I installed I missed the advanced button but it is on the last install screen #9 where you select which drive to install grub to with the advanced button. 

They probably should highlight the advanced button as boot loader location, but most users still would not know what that means.

---

### Post by Doctor Mike on 2010-03-23
> **oldfred said:**
> I also just installed Lucid beta and I boot from sdc, but it installed to sda. The first time I installed I missed the advanced button but it is on the last install screen #9 where you select which drive to install grub to with the advanced button. 

They probably should highlight the advanced button as boot loader location, but most users still would not know what that means.Thank you. I will watch most carefully when the next beta comes around.

---

