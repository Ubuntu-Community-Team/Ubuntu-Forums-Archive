---
title: "GRUB loading error?"
date: 2009-12-21
forum: New to Ubuntu
---

### Post by coolcam on 2009-12-21
Hi,

The other day my computer broke so I had to send it off to PC world to get it fixed. I decided to use my mum's computer, however the screen was smashed and XP wasn't running properly. I soon tried to install Linux onto the external hard drive with another monitor. It seemed to be running fine but when I rebooted it after the installation neither XP or Linux booted. It said:

```
GRUB Loading
Error No Such Disk
GRUB Rescue>

```

I have no idea what to do!

I hope you can help

---

### Post by SecretCode on 2009-12-21
What version of Ubuntu did you install (or what other version of Linux)? - Need to know what version of Grub it has.

Do you have the ubuntu desktop installation CD - for use as a Live CD? Even better, are you able to download and burn a rescue CD like PartedMagic or SystemRescueCD or Super Grub Disk?

Also ... do you have the windows XP installation CD?

---

### Post by coolcam on 2009-12-21
I think grub is 1.97 (not too sure how to find out but I remember seeing that somewhere)

I installed Ubuntu 9.10 and I still have the disc but nothing happens when I put it in and restart it.

I haven't got the windows installation disc just a backup.

I probably can't burn another disc because the computer I am using has a dvd burner but it doesn't work!

---

### Post by ajgreeny on 2009-12-21
I suspect that you have put the grub bootloader on to the internal hard drive, and so if the external drive is not attached to the computer there are no grub configuration files available.  If the external disk is still attached it could be that the mount point for it has changed for some reason.

With the external disk still attached and using the live CD if necessary, run ```
sudo fdisk -l
sudo blkid
``` and with the hard disk mounted, let's see the **/boot/grub/****grub.cfg**.  That may give some clues about what is going on.

---

### Post by coolcam on 2009-12-21
> **ajgreeny said:**
> With the hard disk mounted, let's see the **/boot/grub/****grub.cfg**.  That may give some clues about what is going on.

I am not sure how to do that and when I enter the sudo command it says: Unknown command 'sudo'

---

### Post by SecretCode on 2009-12-21
> **coolcam said:**
> I am not sure how to do that and when I enter the sudo command it says: Unknown command 'sudo'

:confused:

Are you booting the Ubuntu 9.10 live CD and opening a terminal window (Applications > Accessories > Terminal)?

---

### Post by coolcam on 2009-12-21
no I can't. Even with the CD in it still says NO SUCH DISC

---

### Post by SecretCode on 2009-12-21
Oh - were you entering the sudo fdisk, etc at the grub prompt? That won't work as you found.

I'm worried that you can't boot from the CD. Is it the one you used for installation, ie one that works? It could be that your CD drive is not reading it properly.

Do you know how to change your BIOS settings to make sure booting from CD is enabled? And also to see if it can boot from USB? - Because that would be next choice

---

### Post by CaptainMark on 2009-12-21
sounds like your pc is still trying to boot from the internal hdd first, when you boot up look for a message saying push xx to select boot options usually f12 or delete or something, make sure your booting from cd, an easy option would be to reinstall again but at the last stage go to advanced and install grub on your external drive

---

### Post by coolcam on 2009-12-21
I don't really know how to do that. It is the same CD. I will have a go though

---

### Post by coolcam on 2009-12-21
hello again,

I tried to change the BIOS settings but it didn't seem to work. However, I noticed the external hard drives lights where flickering so I turned it on and off. I then rebooted the PC and it seemed to be stuck on Grub loading. I was about to leave the room to post back here when it went onto the options. I selected Ubuntu and it works amazingly!!

Thank you very much for all your help. I'm sorry I didn't notice this earlier.

Thanks again
Coolcam:P

---

### Post by XxDARKXx on 2009-12-22
> I suspect that you have put the grub bootloader on to the internal hard drive, and so if the external drive is not attached to the computer there are no grub configuration files available. If the external disk is still attached it could be that the mount point for it has changed for some reason.

With the external disk still attached and using the live CD if necessary, run  	Code:
 	sudo fdisk -l
sudo blkid 
 and with the hard disk mounted, let's see the **/boot/grub/****grub.cfg**.  That may give some clues about what is going on. 	


ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3a2f3a2f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19451   156240126    7  HPFS/NTFS

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3aea3aea

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    5  Extended
/dev/sdb5               1         476     3823407   82  Linux swap / Solaris
/dev/sdb6             477       30401   240372531   83  Linux
ubuntu@ubuntu:~$ sudo blkid
/dev/sda1: UUID="0050D73D50D737DC" TYPE="ntfs" 
/dev/sdb5: UUID="08ac96c8-b57e-4501-b176-27924c9e188e" TYPE="swap" 
/dev/sdb6: UUID="6afe7ef4-382a-4603-890c-ff6e72e469b6" SEC_TYPE="ext2" TYPE="ext3"

---

### Post by oldfred on 2009-12-22
XxDARKXx This thread is solved, even if your problem is similar your need to start a new thread with some more explanation of your problem and system setup. Only people looking for answers will look here now, those of us offering to help will look in your new thread.

Go to Absolute Beginner Talk and click on new thread button on left side middle.

---

### Post by XxDARKXx on 2009-12-22
i have 2 hdd one for vista and the other is for  ubuntu be for 

Installation  ubuntu  i cant see the other hdd i see one the other hdd is not from my computer i buy it and installation 
sorry if i have some mistake in what i writ it because i am Arabic  
and i didn't found any thing in Arabic forums :)

---

### Post by oldfred on 2009-12-22
XxDARKXx you still will do better starting a new thread as most people looking to help will not look as the solved threads. I just happened to look to see if I could learn more about the solution.

Your windows will not "see" the ubuntu install. But you Ubuntu install should see the windows install. Are you booting windows or ubuntu? Or is sda booting into windows or if you set sdb to boot first in BIOS will it boot first and see windows.

---

### Post by XxDARKXx on 2009-12-22
250 for  Ubuntu 9.10
and 160 for vista 
please help me

---

### Post by XxDARKXx on 2009-12-22
> **oldfred said:**
> XxDARKXx you still will do better starting a new thread as most people looking to help will not look as the solved threads. I just happened to look to see if I could learn more about the solution.

Your windows will not "see" the ubuntu install. But you Ubuntu install should see the windows install. Are you booting windows or ubuntu? Or is sda booting into windows or if you set sdb to boot first in BIOS will it boot first and see windows.

when computer start i don't see windows or ubuntu i see the 

GRUB Loading
Error No Such Disk
GRUB Rescue>
i am right now use the live cd

---

### Post by |{urse on 2009-12-22
This thread is marked solved. I'm assuming it isn't. what make and model is the computer you are currently using?

---

### Post by XxDARKXx on 2009-12-22
> **|{urse said:**
> This thread is marked solved. I'm assuming it isn't. what make and model is the computer you are currently using?
*Dell* DimensionTM *E520*

---

### Post by oldfred on 2009-12-22
can you boot following these instructions (scroll about half way down to 
**[SIZE=2][B][FONT=Arial]Using CLI to Boot[/FONT]**[/SIZE][/B]

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

