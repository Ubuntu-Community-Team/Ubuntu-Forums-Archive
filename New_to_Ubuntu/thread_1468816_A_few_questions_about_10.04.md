---
title: "A few questions about 10.04"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by Woolio1 on 2010-05-01
Hello there! It's me again, yes... After giving up for a while, I've decided to try this out again, since the new LTS just arrived. So I've got a few questions. 

One: Does it support Broadcom Wireless cards, or will I still have to get the BCMWL_Kernel_source? 

Two: Can I install it without installing GRUB? 

Three: Does it still have the Filesystem Check bug, that makes the hard disk near unbootable? 

I plan on installing on a Dell Mini Inspiron 1012, if that's of any importance... I could assume it is. 

Thanks in advance,

W1

---

### Post by Woolio1 on 2010-05-01
So, is anyone actually going to help me, or should I just forget about getting any help from the community whatsoever?

---

### Post by The Thunder Chimp on 2010-05-01
You didn't even wait a half an hour to bump the thread. Forum Dos and Don'ts suggest waiting 24 hours before bumping your thread.

One: I have wireless working without any driver whatsoever (on Karmic)
Two: You can install Ubuntu under Windows without Grub.
Three: Never heard of that.

---

### Post by Woolio1 on 2010-05-01
> **The Thunder Chimp said:**
> You didn't even wait a half an hour to bump the thread. Forum Dos and Don'ts suggest waiting 24 hours before bumping your thread.

One: I have wireless working without any driver whatsoever (on Karmic)
Two: You can install Ubuntu under Windows without Grub.
Three: Never heard of that.

It's the one where you have to go into /etc/fstab/ and edit the > # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc  /proc  proc  defaults  0  0
# /dev/sda5
**UUID=be35a709-c787-4198-a903-d5fdc80ab2f8  /  ext3  relatime,errors=remount-ro  _0  1_**
# /dev/sda6
UUID=cee15eca-5b2e-48ad-9735-eae5ac14bc90  none  swap  sw  0  0

/dev/scd0  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8  0  0 

to 

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc  /proc  proc  defaults  0  0
# /dev/sda5
**UUID=be35a709-c787-4198-a903-d5fdc80ab2f8  /  ext3  relatime,errors=remount-ro _ 0  0_**
# /dev/sda6
UUID=cee15eca-5b2e-48ad-9735-eae5ac14bc90  none  swap  sw  0  0

/dev/scd0  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8  0  0

*underlined and bolded to outline the problem*

---

### Post by overdrank on 2010-05-01
Moved to Absolute Beginner Talk

---

### Post by steveneddy on 2010-05-01
Remember that we are all volunteers here and we are not obligated to answer anyone's questions if we don't choose to.

If you must have help and immediate answers, there is paid support available to everyone who chooses to pay for it.

The best option for someone like yourself is to simply install Ubuntu using VirtualBox, which runs under Windows and will let you learn about Ubuntu without the partitioning and booting issues that Wubi would create.

Using Ubuntu in this way will allow you to run Ubuntu and Windows simultaneously without the need to configure your wireless card.

The other solution is to merely purchase supported from a vendor like [System76]("http://www.system76.com"), which offers Linux supported hardware with Ubuntu preinstalled.

Cheers

---

### Post by theozzlives on 2010-05-01
> **Woolio1 said:**
> Hello there! It's me again, yes... After giving up for a while, I've decided to try this out again, since the new LTS just arrived. So I've got a few questions. 

One: Does it support Broadcom Wireless cards, or will I still have to get the BCMWL_Kernel_source? 

Two: Can I install it without installing GRUB? 

Three: Does it still have the Filesystem Check bug, that makes the hard disk near unbootable? 

Thanks in advance,

W1

1. My broadcom works out of the box since 8.10
2. you need GRUB, why don't you want it?
3. Never had an issue with that.

---

### Post by henry cow on 2010-05-01
I am a newbie myself, but I wasted a week on wubi, VMware, and VirtualBox, and I must say that wubi is the way to go. VMware was plain unusable, VirtualBox was OK but cumbersome, but wubi worked great

<AFTER> 

I got past the roadblocks it threw at me. There were no partitioning issues, since it is itself a program that runs under Windows, but I did have to click "ignore" or "retry" countless times to get past something in the installation process, I can't remember what, something silly.

Now I have a nice little dual boot partition on my Windows 7 laptop and all is well, but I definately think that wuibi is the best non-partition option.

just my humble opinion

---

### Post by Woolio1 on 2010-05-01
> **steveneddy said:**
> Remember that we are all volunteers here and we are not obligated to answer anyone's questions if we don't choose to.

If you must have help and immediate answers, there is paid support available to everyone who chooses to pay for it.

The best option for someone like yourself is to simply install Ubuntu using VirtualBox, which runs under Windows and will let you learn about Ubuntu without the partitioning and booting issues that Wubi would create.

Using Ubuntu in this way will allow you to run Ubuntu and Windows simultaneously without the need to configure your wireless card.

The other solution is to merely purchase supported from a vendor like [System76]("http://www.system76.com"), which offers Linux supported hardware with Ubuntu preinstalled.

Cheers

Well, I'm planning on installing it onto a Dell Mini 1012, so I can't exactly buy a new PC... And I don't want to virtualize, since that's never worked well for me.

---

### Post by cmwatford on 2010-05-01
1: It depends on the card. My first experience with Ubuntu saw no wireless problems but with my latest laptop I had to install the non-free drivers. Both are broadcom.

2: Lilo perhaps? [http://freshmeat.net/projects/lilo/](http://freshmeat.net/projects/lilo/)

3: Never heard of it.

---

### Post by Woolio1 on 2010-05-01
Actually, I just want to use the default Windows bootloader, in conjunction with [iReboot]("http://neosmart.net/dl.php?id=11").

---

