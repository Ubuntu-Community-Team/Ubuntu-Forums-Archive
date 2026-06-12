---
title: "Dual boot"
date: 2010-08-14
forum: New to Ubuntu
---

### Post by LadyA on 2010-08-14
I have Mint installed and want to add Ubuntu 10.04 from live CD as a dual boot. I never did this before and I don't want to mess up Mint, so how do I do it?

---

### Post by Rubi1200 on 2010-08-14
First we need to know how your drive is partitioned.

Have you created space for Ubuntu?

Here are some guides which may help:

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

Feel free to ask as many questions as you want if anything is unclear.

By the way, which version of Mint are you using and are you aware that Mint is a derivative of Ubuntu (meaning you will find basically the same things)?

:)

---

### Post by LadyA on 2010-08-14
I have a screenshot of the hard drive partitioning, but I dont know how to put it in the post. When I installed Mint I let the install do the partitioning by using the whole drive.I don't have space made for Ubuntu yet. I know a little about partitioning, but I will have to read it over again.
I am using Mint 9 and I know that it is a derivative of Ubuntu, but it is a little different and I really like it as well as Ubuntu.

---

### Post by Rubi1200 on 2010-08-14
Hi,
my suggestion would be to boot the computer with the Ubuntu CD choosing to try not install. 
Then, use GParted to resize your main partition (sda1), giving Ubuntu as much space as you feel is needed. I would recommend at least 15-20GB.

Then, use the installer on the desktop and install Ubuntu. When you get to the partitioning stage you want to choose Manual because otherwise you will end up with an additional swap partition, which is unnecessary.

Once done, reboot and all should be well.

The GRUB bootloader will take care of everything and recognize Mint and Ubuntu so you can choose between them at boot.

If you need more information or anything is unclear, please ask.

---

### Post by mapes12 on 2010-08-14
Backup any data you want to keep in Mint, just in case.

If you're experimenting, I would try creating one /home partition and using this for both Mint and Ubu. This would save duplication and disk space.

On your current system you can create a separate /home in this [HowTo]("http://ubuntuforums.org/showthread.php?t=46866").

---

### Post by LadyA on 2010-08-15
Rubi1200, I have a few questions. I don't quite understand this partitioning stuff. If I resize the main partition (sda1), what would the part I put Ubuntu in be called?
When I get to the partitioning part and choose manual, what do I do about the swap file.
When I get to the last step before install, do I uncheck the boot loader and not install it or leave it checked and install it. If I am supposed to install it, where would I install it to?
Sorry for so many stupid questions, but I just can't seem to get this in my head.

---

### Post by murderslastcrow on 2010-08-15
Whenever I face this situation, I always just run the installation and do the automatic option that allows me to drag the slider in the installer itself. Looking at your set up, unless you want to share swap areas between each OS (which is very specialist and not always a good idea), doing this default should work just as well as GParted, since the installer uses GParted itself to perform this operation.

I've never personally had any issues doing it this way, but if you want to be extra careful, use GParted first to free up the space. Be aware that the Ubuntu setup will write a new GRUB, so you'll find it easier to edit GRUB or install things like BURG in Ubuntu than trying to get it to work in Linux Mint.

---

### Post by candtalan on 2010-08-15
> **LadyA said:**
> Rubi1200, I have a few questions. I don't quite understand this partitioning stuff. If I resize the main partition (sda1), what would the part I put Ubuntu in be called?
When I get to the partitioning part and choose manual, what do I do about the swap file.
When I get to the last step before install, do I uncheck the boot loader and not install it or leave it checked and install it. If I am supposed to install it, where would I install it to?
Sorry for so many stupid questions, but I just can't seem to get this in my head.

Using the live CD, go to the
system>administration>partition editor gparted
then resize the main partition (looks like it is  /dev/sda1 ) to be smaller, say to about 260GB size. Then apply this. You will see you have a blank unused space on the drive then, leave it without any new partition  at all, just unused.

Then reboot with the live CD and choose to install Ubuntu, and when you get to the partitioner install choices, choose the option 
to install Ubuntu 
'into the largest unused space on the drive'

this will make an Ubuntu installation in the space with whatever it needs, and will automatically also pick up your other operating system (mint) so that when booting up the grub menu will include both ubuntu and mint, although I am not sure if mint will declare itself as 'mint' in grub, but, whatever, it will be there, it will remain in /dev/sda1 and probably be labelled as such.

hth

---

### Post by malspa on 2010-08-15
> **murderslastcrow said:**
> Be aware that the Ubuntu setup will write a new GRUB

If you want to keep the old GRUB you can install Ubuntu with the alternate installation CD.  It isn't a live CD, but unlike the Ubuntu live CD it lets you install GRUB to Ubuntu's /root partition instead of overwriting the MBR.

I installed Lucid using the alternate CD, on my system that includes Mepis 8, Mint Isadora, and now Lucid and Debian Squeeze, with Mepis 8's grub-legacy booting the other distros.

In the OP's case, it probably doesn't matter much, however, whether Mint's GRUB or Ubuntu's GRUB is used -- they amount to pretty much the same thing.

---

### Post by LadyA on 2010-08-16
Thankyou everyone for helping me dual boot Ubuntu and Mint. With everyone's instructions,  everything went smooth. All is well.

---

