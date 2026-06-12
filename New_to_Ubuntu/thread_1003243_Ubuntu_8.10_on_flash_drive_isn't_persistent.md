---
title: "Ubuntu 8.10 on flash drive isn't persistent"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by PwnCakes193 on 2008-12-05
I downloaded and installed LIVE Ubuntu 8.10 from this website [http://www.pendrivelinux.com/2008/11/04/live-ubuntu-810-usb-persistent-install-windows/](http://www.pendrivelinux.com/2008/11/04/live-ubuntu-810-usb-persistent-install-windows/)    . they said it was persistent, so I guessed it would save all my changes once I shut down, apparently it doesn't, and I was wondering if there is a version like this that would save changes I make on the desktop, settings etc.

Thanks in advance

---

### Post by slyron on 2008-12-06
PwnCakes, I'm very interested in getting a persistent Ubuntu on a USB drive. I haven't been able to get this to work though, using the pendrivelinux guides or the USB Creator program in Ubuntu. Furthermore, no one seems to have any advice. Sorry I can't help, but I'm glad I'm not crazy here.

---

### Post by Cincinnatux on 2008-12-16
I, too, had this problem, and I tried several different "recommended" options.  Last night, I stumbled across a thread where two users were commenting back and forth about USB pendrives onto which they had installed full versions of Ubuntu.  I have an 8GB Kingston HyperX USB drive, so I figured I had the space needed to do a full install.  

This works.  FWIW, it looks like Ubuntu is a bit bloated - it's occupying around 3 GB of my USB drive, which is a bit surprising.  But it is definitely persistent and it survived a full round of updates without breaking (something LiveCD versions ported to the USB with a Casper partition did not want to do for me).

So if you have enough space on your USB device, you might try booting a LiveCD with your USB device inserted, then when it gets to the part about partitioning, make sure you select the USB device.  #-o

If you find a better way of achieving a consistently persistent USB install, please share it.  My understanding is that something is still broken in the effort to port the LiveCD version of Ubuntu to a persistent environment - it appears to be difficult to get it to be consistently persistent.

The next step for me will be to add a partition, format it for FAT32, and see if I can use that part of the USB as a platform-agnostic data repository.

Best of luck to you both.

- Cincinnatux

---

### Post by snowpine on 2008-12-16
I agree with Cincinnatux's suggestion and have one addition. I recommend, when you get to the final stage of the installer (step 7), click the Advanced Options button and install Grub to the USB stick, not your internal hard drive. This will allow you to boot from the device on other computers.

Good luck!

ps Windows will only see the first partition on the drive, so you should make the fat32 partition first.

---

### Post by Cincinnatux on 2008-12-16
> **snowpine said:**
> I agree with Cincinnatux's suggestion and have one addition. I recommend, when you get to the final stage of the installer (step 7), click the Advanced Options button and install Grub to the USB stick, not your internal hard drive. This will allow you to boot from the device on other computers.

Good luck!

ps Windows will only see the first partition on the drive, so you should make the fat32 partition first.

Thanks both for pointing out the bootloader issue (I had forgotten that the installer defaulted to the "first hard drive" for this; oddly, GRUB failed to install to my USB pendrive, so I opted to install LILO instead).

No big deal on having to put the FAT32 partition first, as I plan to wipe my USB drive soonish anyhow.  At present, I've got 64-bit Ubuntu installed to it, but I'd rather have the 32-bit version for my portable workspace, which means starting all over eventually.  Unfortunately, I don't have any CD-Rs handy (recently moved from China to Cincinnati and my stuff hasn't arrived yet) and the only LiveCD I had with me was for the 64-bit version I'm running on my laptop.  Although a temporary solution, really I did it as a proof-of-concept while I had the time.

- Cincinnatux

---

