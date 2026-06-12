---
title: "Help! cant't re-install"
date: 2011-08-12
forum: New to Ubuntu
---

### Post by chuning on 2011-08-12
Hello - 

I think I may have been a bit stupid, and am now completely stuck.

I use Ubuntu 10.10 and Windows 7 on a laptop - I need Windows 7 because of Canon software that I need for my work as a photographer.  Two days ago I was setting up for a shoot, booted up my laptop and got 'grub rescue:' Not too much of a problem, just meant I had to use memory cards rather than the laptop hard drive.  When I got home, I loaded the Windows recovery disks, and then reloaded Ubuntu.  All fine, except when I started up Ubuntu, it told me there was hardly any memory.  I looked, using the partition manager in Windows, and there seemed to be an awful lot of partitions, presumably from re-installs of Ubuntu (as I was messing around with Ubuntu Studio).  This is where I think I've probably been foolish - I deleted all of those, and re-formatted it as one partition, leaving the Windows one alone.  Then, when I tried to reboot the computer, it came up with grub rescue again.  I thought that all I would have to do would be to re-install Ubuntu.  However, I don't seem to be able to.  I've tried a live CD of both 10.10 and 11.04, plus a USB stick with 11.04.  Both of the 11.04 media start off doing something, but then the screen just goes black and nothing further happens.  And the 10.10 disk either just goes to grub rescue, or shows a first line with copyright information, and just stays there

I'm completely stuck - can anyone help?

Many thanks

Chris

---

### Post by raja.genupula on 2011-08-12
do you have live cd of ubuntu 
boot from it 

then open terminal 

type **sudo update-grub**

---

### Post by raja.genupula on 2011-08-12
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)



one more URL 

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by varunendra on 2011-08-12
> **chuning said:**
> H I've tried a live CD of both 10.10 and 11.04, plus a USB stick with 11.04.  Both of the 11.04 media start off doing something, but then the screen just goes black and nothing further happens.  And the 10.10 disk either just goes to grub rescue, or shows a first line with copyright information, and just stays there
Getting grub rescue even with 10.10 CD in means either your laptop is refusing to read from the CD/USB or the waiting just times out before the device (cd/usb) gets ready. Live environment doesn't depend upon the state of installed version. So if the boot media is good and the laptop's specs are supported, it should boot fine.

If it is the same 10.10 disk that you used to install fine before, I'd suspect your drive first, RAM second (for being loose), and hard drive last (loose connection again).

As for a quick fix to get it working at least, I don't think you need this suggestion though, just use your win recovery discs to restore windows, then try live 10.10 to start over.

---

