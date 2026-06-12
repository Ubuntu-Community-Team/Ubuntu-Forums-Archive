---
title: "How to partition ?"
date: 2010-04-23
forum: New to Ubuntu
---

### Post by Hydrokys on 2010-04-23
I want to do a fresh install of windows 7 x64 and dual boot Ubuntu x64 on a seperate hdd. I have made the cd but not sure if i have to partition the drive for ubuntu in windows before hand or will it do it automaticly?. I f i have to do it manually how many partitions do i need and what size . I will have windows 7 on a 500gb hdd and ubuntu on a 320gb hdd. O r maybe i should put them on seperate partitions on the 500gb drive. I want to try linux without using a live cd and im kinda lost . lol Thanks for the help in advance. :guitar:

---

### Post by arrrghhh on 2010-04-23
> **Hydrokys said:**
> I want to do a fresh install of windows 7 x64 and dual boot Ubuntu x64 on a seperate hdd. I have made the cd but not sure if i have to partition the drive for ubuntu in windows before hand or will it do it automaticly?. I f i have to do it manually how many partitions do i need and what size . I will have windows 7 on a 500gb hdd and ubuntu on a 320gb hdd. O r maybe i should put them on seperate partitions on the 500gb drive. I want to try linux without using a live cd and im kinda lost . lol Thanks for the help in advance. :guitar:

If I understand you correctly, Ubuntu and Win7 are on physically separate hard drives - correct?  If that's the case, no need to worry about partitioning.

However, install Win7 first, then Ubuntu.  Otherwise GRUB'll get knocked out when you install Win7.

---

### Post by Hydrokys on 2010-04-23
yes i want them on seperate hdd's if that is the best option. thnx

---

### Post by arrrghhh on 2010-04-23
> **Hydrokys said:**
> yes i want them on seperate hdd's if that is the best option. thnx

It depends on your needs, but having them on separate hdd's makes it easier, that's for sure.  Then you don't have to worry about partitioning ;)

Otherwise, assuming you did want Win7 and Ubuntu on the same hdd... install Win7 first, but leave some free space on the hdd (unpartitioned, raw space).  Then once 7 is running, reboot to Ubuntu disc, install it - using the rest of the free space during the install.

You can ignore all that since you're doing separate hdd's :D  I still recommend Win7 install first, to avoid having to fix GRUB.

---

### Post by Kellemora on 2010-04-23
Hi Hydro

Personally, on the drive you plan to install Ubuntu, I would leave about 30 gigs for Ubuntu's root, don't forget to set the root mountpoint as /
Then make a SEPARATE Home partition using most of the rest of your space
home would have a mountpoint of /home
Also make a SWAP FILE double the size of your RAM, even if you have so much RAM it may never be used.  That space might come in handy some day, hi hi....  If you are using GParted the drop down box lists SWAP as one of the choices.

Windows will reside on HD1, Ubuntu on HD2.
As stated, install Windows First, then install Ubuntu and it will FIND windows and add it to the Grub boot loader for you.

Welcome to the wonderful world of Ubuntu!

TTUL
Gary

---

### Post by Hydrokys on 2010-04-23
ok so once ubuntu is installed i partition with gparted and set what each partition is for?

---

### Post by arrrghhh on 2010-04-23
> **Hydrokys said:**
> ok so once ubuntu is installed i partition with gparted and set what each partition is for?

You partition during the Ubuntu install.  His recommendations are good for restoring (if you want to wipe you can wipe your / while still keeping your /home - most settings/docs go there...)

If you just do the guided partitioning, you'll be just fine... but you won't have the ability to format your main / partition without losing your /home...

---

### Post by Hydrokys on 2010-04-23
Awesome .. Thank you for the quick replies. sounds easy i cant wait thnx again all!

---

### Post by srs5694 on 2010-04-23
Kellemora's suggestions are good ones. Two possible further tweaks:


[list]
[*]On one drive or the other, create a separate partition for transferring or sharing files between the OSes. If you don't do this, the only way you'll be able to share such files (be they things you download from the Internet, your own documents, or whatever) is to give one or both OSes direct access to the other OSes' installation partitions. Such access can be dangerous, since each OS has slightly different rules for all sorts of things (file naming conventions, end-of-line conventions in text files, etc.), and the non-native filesystem drivers may not be 100% safe. The size of a file-sharing partition depends on your own anticipated needs and your available disk space.
[*]If you put the Linux swap partition on the Windows installation drive, Linux swap access won't interfere with non-swap disk access. This can provide a bit of a speed boost, assuming the disks are of similar speed. OTOH, if you've got plenty of RAM you probably won't be hitting the swap space much, so this benefit is likely to be very small. Also, if your shared-data partition is on the Windows boot drive, the swap location will be less important, at least if you use the shared-data partition very much.
[/list]

---

### Post by MoebusNet on 2010-04-23
Before you partition your drive(s) to install Ubuntu, I highly recommend doing a Google search on that very subject. For example, if you intend to dual-boot Windows and Ubuntu on the same hard-drive you should defragment Windows before you start  partitioning, etc.

I highly recommend Aysiu's writings on Ubuntu installation, configuration, etc: [http://www.psychocats.net/ubuntu](http://www.psychocats.net/ubuntu)

While Aysiu does not cover dual-boot Windows/Ubuntu as he once did, this option may merit consideration: [http://www.psychocats.net/ubuntu/wubi](http://www.psychocats.net/ubuntu/wubi)

Best of luck!

---

### Post by ajgreeny on 2010-04-23
> **Kellemora said:**
> Hi Hydro

Personally, on the drive you plan to install Ubuntu, I would leave about 30 gigs for Ubuntu's root, don't forget to set the root mountpoint as /
Then make a SEPARATE Home partition using most of the rest of your space
home would have a mountpoint of /home
Also make a SWAP FILE double the size of your RAM, even if you have so much RAM it may never be used.  That space might come in handy some day, hi hi....  If you are using GParted the drop down box lists SWAP as one of the choices.

Windows will reside on HD1, Ubuntu on HD2.
As stated, install Windows First, then install Ubuntu and it will FIND windows and add it to the Grub boot loader for you.

Welcome to the wonderful world of Ubuntu!

TTUL
Gary
+1

This is the way to go; if you mess up the install as a new user, which is not impossible, and could almost be said to be quite likely, all your personal home files will be still sitting in /home and you can reinstall without losing any of them.

See [http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome) for a lot more detailed info.

---

### Post by codemaniac on 2010-04-23
as our friend [srs5694]("http://ubuntuforums.org/member.php?u=1032238") has suggested a separate data partition is the best bet..you may consider the data partition to be a ntfs partition that way all modern linux os-es can access that partition with full fledged read-write access..

---

### Post by oldfred on 2010-04-23
Also with 2 drives you want to have your windows boot loader in the window drive and the grub boot loader in the MBR of the Ubuntu drive. Grub often installs to the first drive unless you select the advanced button to choose which drive to install grub to. The advance button during install is at the end of the partitioning just above the install button. You then can in BIOS set to boot the Ubuntu drive but if you ever have problems you can select to boot the windows drive with f12 or BIOS change.

Install karmic Screens shown with advanced button
[http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml)

---

### Post by MoebusNet on 2010-04-23
This should be of help: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

