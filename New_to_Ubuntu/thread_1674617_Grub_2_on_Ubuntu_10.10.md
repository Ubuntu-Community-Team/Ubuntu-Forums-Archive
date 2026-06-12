---
title: "Grub 2 on Ubuntu 10.10?"
date: 2011-01-24
forum: New to Ubuntu
---

### Post by apanton on 2011-01-24
I was planning on installing Ubuntu 10.10, on a new primary partition I have made. But before so I was wondering what Grub 2 is like (I have no experience with Grub 2). Is it alright to use (I was planning on installing it to the partition).

Is there any way to use Grub 1 with Ubuntu 10.10 and install it to the partition rather than overwiriting the MBR.

---

### Post by drs305 on 2011-01-24
apanton

Welcome to Ubuntu and the Ubuntu forums. Grub 2 is much different from Grub legacy and requires a bit of learning if you want to tweak things. There is now enough experience with Grub 2 to help out if you experience any problems with it.

Grub 2 can be installed on a partition, but it will complain and it is not recommended. The reason is the way it is written on the partition - if files subsequently get moved around Grub 2 can break. On the other hand, if you allow G2 to overwrite the MBR it can handle other OS's as well (including Windows). You could even back up your current MBR settings before the installation so you could revert back, or there is a simple 2 command process to restore the MBR to point to Windows again.

Once Ubuntu is installed, you *can* remove it and install Grub legacy, but in general I would strongly recommend sticking with Grub 2. It generally works and will automatically recognize your other systems. If not, we can help you take whatever steps might be necessary to get it to work.

There are links in my signature line to various aspects of the new grub. The 'Basics' link provides an overview on Grub 2.

---

### Post by sadaruwan12 on 2011-01-24
No worries frnd just install it the installer will do every thing automatically nothing to you have to do. If something happens we're here to help.

---

### Post by apanton on 2011-01-25
I think I'll stick with Grub 2 if I install Ubuntu 10.10 but I still want to install it to the partition. But reading through again it sounds like a lot of trouble.
What would you advise? Also what would I do if I wanted to restore the MBR back to how it was with windows

---

### Post by drs305 on 2011-01-25
> **apanton said:**
> 
What would you advise? Also what would I do if I wanted to restore the MBR back to how it was with windows

You can make a backup copy of the MBR using the "dd" command but a more normal method would be to install an app called 'lilo' and let it point the MBR back to the partition with the boot flag (Windows). If you lose Ubuntu, boot the Live CD to the Desktop, open a terminal, and:
```

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
This assumes Windows is on the *sda* drive and has the boot flag set (which it should). Don't run any other lilo commands, as lilo will want to fully install itself. All you need are the two above.

---

### Post by mathgeek2000 on 2011-01-25
> **sadaruwan12 said:**
> No worries frnd just install it the installer will do every thing automatically nothing to you have to do. If something happens we're here to help.

If you're installing 10.10 to a clean HDD -- No partitions, or other OSs installed it will use Grub2 by default. At least an older Ubuntu would leave Legacy Grub in place, if you upgraded.

I have 10.10 now as the only OS, w/ Grub2. -- It took a while, but I was able to add a 'full color' background image. Legacy Grub backgrounds are more limited in color, but easier to setup.

The second advantage to Grub2 is the ability to boot an ISO file located on the Hard Drive. -- I have a copy of Parted Magic 5.9, which I could boot to instead of Ubuntu. -- It's handy for making backups.

---

