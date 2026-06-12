---
title: "I've lost everything!"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by tylden on 2009-01-03
I just updated from 8.4 to 8.10, followed the download instructions carefully, I thought. Now the laptop I've updated won't start at all - I've rebooted several times, it goes through the usual opening pages then I just get the following messages:

Starting up...
[0.000000] MPTABLE: bad signature [<3>BIOS bug, MP table errors detected!...
[0.000000]...disabling SMP support. (tell your hw vendor)
[1.316171] Kernel panic - not syncing :VFS: Unable to mount root fs on unknown-block(0,0)

This is just gibberish to me. Any suggestions, please?

---

### Post by semi_fiction on 2009-01-03
Hmm... is the hard drive dedicated to Ubuntu, or are you dual-booting?

---

### Post by 2hot6ft2 on 2009-01-03
Looks to me like the partition table is messed up. Are you duel booting or is it just ubuntu on your pc?

It may be able to be fixed.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
TestDisk is a powerful free data recovery software! It was primarily designed to help recover lost partitions and/or make non-booting disks bootable again when these symptoms are caused by faulty software, certain types of viruses or human error (such as accidentally deleting a Partition Table). Partition table recovery using TestDisk is really easy.

Livecd's here
[http://www.cgsecurity.org/wiki/TestDisk_Livecd](http://www.cgsecurity.org/wiki/TestDisk_Livecd)

---

### Post by Michael.Godawski on 2009-01-03
hi,

several things ahead. 

Before upgrading the system you should always do a backup of your important data.

Upgrading via the graphical UI is somewhat risky in my opinion; I would always prefer a fresh install.

Also a separate home partition is very recommend so that all your personal data is well on a separate partition.

Perhaps this will help:

[http://ubuntuforums.org/showpost.php?p=231552&postcount=13](http://ubuntuforums.org/showpost.php?p=231552&postcount=13)

Are you able to boot into the old kernel?

---

### Post by NeonShadow on 2009-01-03
This is just a guess, but your data may be fine after all...

It almost seems like the issue I had with grub when converted my old Toshiba Qosmio to dual-boot with 7.10. Basically, something was incompatible with the BIOS and I would get "grub hard disk error".

However, despite that error, when I booted to CD first and then chose to boot from HDD, it worked just fine.

Try booting up and selecting to boot from liveCD. Then you can try to mount your hard drive and see if the data is still there. If it is, make a backup first! Then try to reboot, boot to CD again, but in the menu select boot from hard drive, instead of booting in to the live image itself.

Good luck!!!

---

### Post by tylden on 2009-01-04
I have only been playing with Ubuntu on my (wife's) laptop up to now. It's not dual boot as when I first downloaded 8.4 I made a mistake and took out the partitions and Windows XP. I've not lost any data that matters, so I can afford to do a clean start. Would it pay me to download a new copy of 8.10 on to CD via my desktop and would this then start up if I stuck it in the laptop?

I'm no computer wizard, just thought I'd like to try anything not connected with Windows. Thanks for your suggestions, any more gratefully received.

---

### Post by ranch hand on 2009-01-04
If you have a live CD you can boot up on it and check to see what you have on your HDD.

This would be a good place to start.  I would use the Hardy live CD if you have it as you inow that it runs on that box.

---

### Post by kansasnoob on 2009-01-04
Since data loss is not a problem a fresh install is the fastest option!

Just curious if you've checked the 8.10 release notes:

[http://www.ubuntu.com/getubuntu/releasenotes/810](http://www.ubuntu.com/getubuntu/releasenotes/810)

---

### Post by tylden on 2009-01-05
Thanks for all the advice. I've re-installed from the CD and it's up and running again, now I'll start from scratch. I've just found out that I am actually on 7.10 - I did say I'm a beginner - which could explain why the upgrade didn't work. Please excuse my stupidity, as I'm sure to be back.

By the way, I had read the 8.10 release notes, just didn't realise where I was starting from.

---

