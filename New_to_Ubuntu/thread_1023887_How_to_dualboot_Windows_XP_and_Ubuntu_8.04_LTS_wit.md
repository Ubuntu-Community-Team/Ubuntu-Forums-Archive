---
title: "How to dualboot Windows XP and Ubuntu 8.04 LTS with Ubuntu installed first"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by Bigbob22 on 2008-12-28
-Topic-

---

### Post by balaknair on 2008-12-28
> Normally when Windows is installed after Ubuntu the master boot record will be overwritten. This means that you would have to boot off a LiveCD and re-install grub. However, here is an alternative method:

   1. Create an NTFS partition for windows (using fdisk or whatever tool you are familiar with)
   2.

      Backup the boot sector e.g. dd if=/dev/hda of=/mbr.bin bs=512 count=1
   3. Install windows
   4. Boot into a LiveCD
   5. Mount your root partition in the LiveCD
   6.

      Restore the boot sector e.g. dd if=/media/hda/mbr.bin of=/dev/hda bs=512 count=1
   7. Restart and Ubuntu will boot
   8. Setup grub to boot windows

From
[https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu](https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu)


See also
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by StevenHarper on 2008-12-28
I prefer to 

[LIST]
[*]boot from a LIVE CD
[*]Resize the current Ubuntu partition
[*]Make a Blank Partition (no format) for windows
[*]Boot from windows CD and install to empty partition (NTFS)
[*]Reboot off Live CD
[*]Re-install Grub
[/LIST]

---

### Post by Bigbob22 on 2008-12-28
Is it possible to install Windows into an external hard drive? If it is how?

---

### Post by Bigbob22 on 2008-12-28
bump

---

### Post by Bigbob22 on 2008-12-28
How do you reinstall grub?

---

### Post by balaknair on 2008-12-29
**Reinstall GRUB:**

1 Boot your computer up with Ubuntu CD

2 Open a terminal window or switch to a tty.

3 Type "sudo grub"

4 Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". Use whatever your computer spits out for the following lines.

5 Type "root (hd0,1)", or whatever your hard disk + boot partition numbers are for Ubuntu.

6 Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or whatever your hard disk + partition nr is, to install GRUB to a partition.

7 Quit grub by typing "quit".

8 Reboot and remove the bootable CD. 

From [https://help.ubuntu.com/community/GrubHowto#Backup,%20Repairing%20and%20Reinstalling%20GRUB](https://help.ubuntu.com/community/GrubHowto#Backup,%20Repairing%20and%20Reinstalling%20GRUB)

---

### Post by balaknair on 2008-12-29
**Installing Windows onto an external hard drive**

Microsoft says it's not possible, but I've heard it can be done.
Your motherboard has to support booting off a USB device though. Most laptops support booting off USB.

I've never tried it myself, but you might want to take a look at
[http://www.ngine.de/article/id/8](http://www.ngine.de/article/id/8)

I wouldn't advise it though.

---

### Post by Bigbob22 on 2008-12-29
So if my motherboard supports it what are the downsides?
Can't you just run the Windows XP install cd and when it asks where to install, install it on the portable hard drive?

---

### Post by Dark Aspect on 2008-12-29
> **Bigbob22 said:**
> Is it possible to install Windows into an external hard drive? If it is how?

Its illegal to boot windows of an external hard drive, I've have done it before though its not hard. What do you want windows for? If you want it for extreme gaming than USB probably is not the way to go. Also you could look in to virtual box

[http://www.virtualbox.org/]("http://www.virtualbox.org/")

Send me a PM if you need help booting XP off USB, I have some tips for SP2/SP3 to avoid the blue screen of death.

Edit:

> **Bigbob22 said:**
> Can't you just run the Windows XP install cd and when it asks where to install, install it on the portable hard drive?

No, the installer by default denies installing on any thing other than an IDE/ATA hard drive. Plus upon boot up XP will re-enable all hardware drivers and in doing so give the BSOD in less you have specially modified USB system files....Which I have.

---

