---
title: "Kernel panic - not syncing: VFS: Unable to mount root fs on unkown block(8,1)"
date: 2009-11-18
forum: New to Ubuntu
---

### Post by curpin on 2009-11-18
Guys,
I am a newbie here, so please easy easy.
I have been using the kubuntu 9.10 for a while now and I am very excited with it.  Nice work!
Two days ago, while downloading the package for chromium and virtualbox the download got stuck somewhere, so I thought I would reboot.
After rebooting I got the following:
[Linux-bzImage, setup=0x3400, size=0x3b26e0]
[Initrd, addr=0x37863000, size=0x78cfb8]
[B][    1.786905] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(8,1)
[/B]
My Kubuntu is installed on ntfs alongside Windows 7.
I am not sure how this can be solved! I tried chkdsk /f from Windows but that did not cure it.
Any help is appreciated.

---

### Post by twisted_steel on 2009-11-19
Welcome to the forums :)

The closest I can find to your problem is this thread: [http://ubuntuforums.org/showthread.php?t=495366](http://ubuntuforums.org/showthread.php?t=495366).

The original poster found that the /wubi folder had to be defragmented.  I would try running the Disk Defragmenter in Windows 7 and see if that helps.

---

### Post by curpin on 2009-11-20
Well, thank you for the reply.  I did defragment all my Windows installation and did as well chkdsk /f but that did not help.
I have as well been able to mount the disk after booting from the CD and I can browse it, but not sure what to do at this stage.

---

### Post by twisted_steel on 2009-11-20
I'm not sure of the best way to fix the problem.  I have never used Wubi before.  The last Linux I installed 'on' Windows was in 2000 or so when I put it on Windows 98 ;)

I did find a bug on Launchpad and another recent thread on the forums with other people experiencing the problem.

Bug: [https://bugs.launchpad.net/wubi/+bug/477169](https://bugs.launchpad.net/wubi/+bug/477169)
Forum thread: [http://ubuntuforums.org/showthread.php?t=1317397](http://ubuntuforums.org/showthread.php?t=1317397)

I would try booting via the LiveCD and backing up any files to either a USB drive or possibly your Windows drive (NTFS) if it will let you.  Maybe a reinstall will help.  I would add any information you can to that bug report before you do so.  Maybe that will help confirm the problem for the developers.

I've been running Windows 7 in VirtualBox for the past few months, so you may want to look into doing something like that (Kubuntu in a Virtual Machine in Windows or Windows 7 in a VM in Kubuntu).  Another option if this does not pan out is to resize your Windows 7 partition and install Kubuntu in a new partition on the drive.

---

### Post by curpin on 2009-11-21
Hi,
Well, I have used it in VirtualBox for a while, but that is restrictive a bit, for example 3D doesn't work straight forwards.
Anyway, I have yesterday miraculously sorted it out by doing what the users LuxY2k suggested in the forum:
[http://ubuntuforums.org/showthread.php?t=1317397&page=4](http://ubuntuforums.org/showthread.php?t=1317397&page=4)

So now it is running as before...

Thanks anyway for your help

---

### Post by twisted_steel on 2009-11-21
Weird.  At least all is well now.

---

