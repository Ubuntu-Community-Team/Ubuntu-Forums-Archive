---
title: "GRUB doesn't start, computer keeps restarting (XP and ubuntu 9.04 dual boot)"
date: 2009-12-20
forum: New to Ubuntu
---

### Post by fahadghani on 2009-12-20
Hi
Please help me with a problem with dual boot: Windows XP and Ubuntu 9.04 on separate HD partitions. I installed Ubuntu after XP and have three partitions: /boot, /root and swap (dont know if we even need that anymore, i last used linux during the Fedora Core 3 release :???:)

It was working fine for about 2 months before booting into windows started creating issues. Whenever i log into XP, somehow GRUB gets corrupted or something so that when i restart the laptop, it displays "Grub 1.5 loading..." and restarts again. This seems to go on in an infinite loop, restarting the machine again and again trying to load grub.

When I re-install grub, everything is fine (I am able to see the Grub menu of ubuntu and windows and able to boot into both) until i boot into XP. XP works absolutely fine w/o any hiccups but the same problem resurfaces when i shut it down (or hibernate) and restart the machine: the same infinite loop. And I hv to re-install the grub again. 
Somehow, logging into windows is corrupting Grub. 

I am using a Dell vostro 1520:

[LIST]
[*]3GB DDR2 800MHZ 2 DIMM Vostro
[*]250GB 7200RPM SATA Hard Drive
[*]WINDOWS XP PRO SP3
[*]Intel Core 2 Duo Processor
[/LIST]
In case this is a specific hardware issue, which I don't think it is (i could be wrong though :confused:)

Please also find attached the **RESULTS.txt** file (using the Boot info script in this thread: [http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)). This file was generated through Live session of ubuntu after the last grub corruption. 

I have seen a few similar threads in the forums but there doesn't seem to be a proper answer (i might have missed it somewhere perhaps). Please help!

Thanks for any help!!

---

### Post by Bucky Ball on 2009-12-21
Hardware is a possibility. Disk might be failing right where the boot sector for windows is (and grub if that is there). The endless loop maybe happening because Windows does not shut the partition properly and exit out when it fails the first time. So that is what it's trying to do over and over. Therefore, grub would no longer be able to find the partition as it isn't closed. 

Might pay to do a disk check booting from a live CD.

---

### Post by oldfred on 2009-12-21
There have been issues with grub2 and HP and Dells. I have not seen the issue with grub legacy which you have. Are you running any of these or does it work ok on reboot from windows. You never should go into Ubuntu from a hibernate. If you happen to modify something in windows while hibernated you may not be able to reboot as now the hibernate may not match the modified system.


HP ProtectTools and Dell Recovery Tool write into MBR
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941)
Dell Media direct issues with MBR
[http://ubuntuforums.org/showthread.php?t=923576](http://ubuntuforums.org/showthread.php?t=923576)
[http://ubuntuforums.org/showthread.php?t=1344828](http://ubuntuforums.org/showthread.php?t=1344828)
[http://ubuntuforums.org/showthread.php?p=8433673](http://ubuntuforums.org/showthread.php?p=8433673)
Found out today after numerous searches the issue. I found the answer here -- I had heard dynamic disk partioning may be the cause (which I don't have) or virus software (which I removed). I have a Compaq netbook -- HP product. Turns out they have HP Recovery tools that will overwrite parts of the MBR. The thing is, I uninstalled every single piece of their recovery software, sync software, etc, cuz I didn't want any of that crap. I went into services, and lo-and -behold -- there was the hpqwmiex service running. So I disabled it, did the update-grub thing again, logged into Windows then back into Ubuntu, and all is well!
Another windows issue that caused grub2 issues.
Looks like I found the culprit. It was Norton Ghost running in the background, that I had just recently installed. I disabled it during startup through msconfig and no more trouble. Thanks for the links!

---

