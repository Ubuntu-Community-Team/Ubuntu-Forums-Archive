---
title: "Syslinux path for USB installer"
date: 2010-09-07
forum: New to Ubuntu
---

### Post by LastElf on 2010-09-07
Ok, I never thought I'd have to join to get my answer, but here it goes anyway. Warning, Linux newbie.

What I want to do is have a LiveUSB of Ubuntu, but with Ubuntu in it's own folder and not just strewn all over the root. I used Universal-USB-Installer-v1.7.3 to install Ubuntu 9.10 to the USB first off. That works fine and I've done it a few times without any kind of problems. The problem is when I put all those files into an /Ubuntu/ folder and try to use my own syslinux config to reroute to the original boot files.

The reason I want to use a custom config file is that I also want to be able to boot into a USB install of UBCD, and have the USB as my all in one support disk. So basically, it's a switching config between the Ubuntu boot loader and the UBCD boot loader, and then anything else I may want to add in the future (Like BartPE).

What do I need in the syslinux.cfg file to accomplish this? And what else do I need to add to make it selectable with the arrow keys instead of numbers (I did actually get that far that it would boot, I just had error after error trying to get to the Ubuntu loader)?

And will there be any conflicts if I give the files and folders +s +h attributes in Win7? I don't want them to be seen when I give the USB to friends to copy files on or off.

---

### Post by LastElf on 2010-09-09
Bump. Does anyone have any ideas?

---

### Post by Saint_ on 2010-09-11
Wait..what? So you want several bootable ISOs on one USB stick? Sorry lol having a hard time following your post

---

### Post by LastElf on 2010-09-11
My first thought was unpack the ISOs into their own folders on the stick, and then use syslinux to point to either boot menu. Since I have a huge Windows background, I didn't know ISO files could be run natively from the boot sector. This would probably be much easier in the long run, and easier to update when new versions come out.

Same question as before though, how do I use a custom boot menu to choose between the different images on the one stick?

---

