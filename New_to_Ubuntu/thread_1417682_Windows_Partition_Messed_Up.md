---
title: "Windows Partition Messed Up"
date: 2010-02-27
forum: New to Ubuntu
---

### Post by Sly-.- on 2010-02-27
Hey. So I'm running Windows 7 64bit, I partitioned my drive like normal so I could install Arch on a seperate partition. So it rebooted like normal, was doing its business to create the new partition then I tried to boot into Windows and received the following error:

pwNative not found - skipping autocheck
autochk not found - skipping autocheck

This is weird to me as I've never received this error before and I've partitioned my drive many times without having any issues.

Can anyone help me fix this? I really do not want to format my drive unless that is the only option.

Cheers.

---

### Post by cozmicharlie on 2010-02-27
What a coincidence - I have just finished dealing with this same issue.  On my system I had to reinstall Windows but maybe you won't have to. I believe this is a bootloader problem but I am not knowledgeable enough in this area to know for sure.  Are you able to boot into the Arch partition?  Does Grub show the Windows partition as an option at boot-up?  I was able to access my Win7 partition using Super Grub ([http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)).  This is a great utility.  Download the image file and burn it to a disk (or the one for usb if you prefer but I find the cd to be easier).  Insert the cd when you start the computer and boot into the CD (just like any live linux cd).  It has a number of options including repairing the mbr and reinstalling grub. Just go into the menus and you will see a section for Windows - it is straightforward.  I hope this helps.  maybe someone else with more knowledge than me will come along and offer a better solution but this is what worked for me.

---

