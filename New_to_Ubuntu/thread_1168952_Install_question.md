---
title: "Install question"
date: 2009-05-24
forum: New to Ubuntu
---

### Post by Vir Quisque Vir on 2009-05-24
I have XP Pro installed on D: with NTFS.  I have another internal drive C: that is formatted with NTFS as well.  

Is it better to install Ubuntu 9.04 on the "empty" NTFS formatted drive, rather than repartition the current boot XP drive?  The D: drive is nominally 120 GB and the C: drive is 160 GB.  I would rather put Ubuntu on the free drive, unless there are reasons not to do so.

Are there any installation differences in 9.04 from the previous version? (Things to watch out for)

I would like to have XP be the default boot for the time being, but anticipate that I will be booting to Ubuntu subsequently as the primary.  My desktop computer is a Dell 650 workstation with a Xeon processor runnng at 2.4 GHz.  Currently using Firefox 3 and Thunderbird.  I DID have Vista on one of my computers, for ONE day, reformatted the drive and threw the installation CD out.  One day was enough for me.  Thanks for the help.

---

### Post by lisati on 2009-05-24
If you have free space or even a free drive available, go for it! To cut a potentially long story short, it can play a part in avoiding complications in the event of something not going quite right.

---

### Post by unutbu on 2009-05-24
You should have no problem installing Ubuntu on the internal C: drive.

I think most people find the latest Ubuntu release works the best, but there are so many types of hardware out there that some people find the latest version does not work well for them. It's hard to say for sure if you'll run into any problem, but chances are good that most problems (if there are any) can be worked out.

When you install Ubuntu, let it install the GRUB bootloader on the C: drive's MBR (master boot record). This is the default option. Make sure your BIOS is set to boot the C: drive first. 

After you install Ubuntu, and reboot, Ubuntu will be the default boot option.
However, there is a simple way to change the boot option to XP:
You boot into Ubuntu, click System>Admin>Synaptic (the package manager), and 
install the startupmanager package. Then you run startupmanager (click Applications>...>StartUpManager) and use the GUI to select XP as your default boot option.

---

