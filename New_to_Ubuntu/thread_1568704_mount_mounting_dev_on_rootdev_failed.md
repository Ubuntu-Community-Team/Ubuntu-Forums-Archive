---
title: "mount: mounting /dev on /root/dev failed"
date: 2010-09-05
forum: New to Ubuntu
---

### Post by JauntyJack on 2010-09-05
[LIST]
[*]I recently upgraded from Karmic to Lucid, which cleared up the  Broadcom 4318 wireless card issue, but led to a new problem.
[*] I used the Software Center to try to install K3B, but it hung up after I clicked Install. After that if I tried to log off or open Synaptic, I got blank dialog boxes with no text.
[*]Eventually I pulled the battery to do a hard restart. Since then on boot up I get the following message.
[*] =================
[*][B]mount: mounting /dev on /root/dev failed: No such file or directory 
[/B]
[*][B]mount: mounting / sys/ on root/sys failed: No such file or directory 
[/B]
[*][B]mount: mounting /proc on /root/proc failed: No such file or dirctory 
[/B]
[*][B]Target filesystem doesn't have /sbin/init. No init found. Try passing init= boot arg 
[/B]
[*][B]BusyBox v1.10.2 (Ubuntu 1:1.10.2.2ubuntu7) built-in shell (ash) 
[/B]
[*]**(initramfs) **
[*]==================
[*]I searched and found several references to this problem, always around batteries dying, but no resolution posted.
[*](I saw a reference to booting from a live CD, but that doesn't work for me - I put in  a USB live CD I have here, it recognized it but wouldn't boot from it.) - just says ''assuming cache write-through''.
[*]Any ideas welcome!!
[*](Also if anyone knows how to insert hard returns in this message without bullets, lemme know.)
[*]By the way, I have no important data on that laptop, it's my ''try Ubuntu'' machine and I have been cautious. I have no objection to wiping and reinstalling all, if anyone knows how to do that, given that it's not dealing with the live cd.
[/LIST]

---

### Post by JauntyJack on 2010-09-05
Update: I found a tip about holding down Shift during boot and was able to select a different kernel: 22, rather than 24. This seems to have resolved the issue, as I no longer get bumped to Busybox during boot.   (As an aside, I have an unusually long wait between startup and Grub loading. For 20-30 seconds, I only have a black screen and blinking cursor. Any info on that would be welcome.)

---

### Post by Rubi1200 on 2010-09-06
> **JauntyJack said:**
> Update: I found a tip about holding down Shift during boot and was able to select a different kernel: 22, rather than 24. This seems to have resolved the issue, as I no longer get bumped to Busybox during boot.   (As an aside, I have an unusually long wait between startup and Grub loading. For 20-30 seconds, I only have a black screen and blinking cursor. Any info on that would be welcome.)
Hardware compatibility is the most likely answer; it seems that some people can boot in just a few seconds, while others (you...me) experience this delay you mention. If an older kernel works, stick with it until the next update and see if the issue(?) is resolved.

---

### Post by HorseBox on 2011-02-25
I'm having this problem right now and I tried holding shift down during startup but it didn't work. GRUB loads fine but if I even select Ubuntu recovery mode it just loads BusyBox. I'm on a live ubuntu CD now and heres what it says when I run fdisk:
> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8f800000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       12158    97656832   83  Linux
/dev/sda2           12159       12644     3903764+   5  Extended
/dev/sda3   *       12645       12657      102400    7  HPFS/NTFS
/dev/sda4           12657       19458    54623232    7  HPFS/NTFS
/dev/sda5           12159       12644     3903763+  82  Linux swap / Solaris
sda1 is what I have Ubuntu installed on. One of those NTFS partitions is an actual Windows 7 partition while the other one is for Windows 7 installed inside VirtualBox. The one with the star under boot is the VirtualBox one and I think this is whats causing the problem. Last thing I remember doing last night was installing a new program on the Windows 7 guest and when I started the computer up today it took abnormally long for everything to start up and ended up just loading BusyBox. 

I tried to mount /dev/sda1 from the live CD but it just gets stuck. It doesn't give me any error messages, it just returns to the next line like its processing the command but when I check the folder I'm mounting it to theres nothing in there.

---

### Post by Hedgehog1 on 2011-02-25
> **HorseBox said:**
> I'm having this problem right now and I tried holding shift down during startup but it didn't work.
 
HorseBox,
 
please start a new thread for this issue, otherwise most folks will not see it - and therefore cannot help.
 
:KS

---

### Post by HorseBox on 2011-02-26
> **Hedgehog1 said:**
> HorseBox,
 
please start a new thread for this issue, otherwise most folks will not see it - and therefore cannot help.
 
:KS
Done
[http://art.ubuntuforums.org/showthread.php?p=10497223](http://art.ubuntuforums.org/showthread.php?p=10497223)

---

