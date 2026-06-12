---
title: "Installing ubuntu server edition over older ubuntu."
date: 2011-05-27
forum: New to Ubuntu
---

### Post by ornothaloapq on 2011-05-27
I have an old desktop computer running the desktop version of ubuntu 8.04. The bios is locked down on this machine. It is inaccsessable for some reason. I have the iso of the new ubuntu server OS. How do I wipe the existing system and install new software ?
Thank you for any help.

---

### Post by Smart Viking on 2011-05-27
You can mount the hard drive in another machine and install it from that machine, then plug it back.

---

### Post by ornothaloapq on 2011-05-27
Do you mean connect the old ubuntu system via USB or some other cable to the computer with the ubuntu server iso file and make it install?

---

### Post by Smart Viking on 2011-05-27
More like taking the hard drive out of the computer, putting it into another computer, boot up and install from that computer, and than put it back.

---

### Post by lightstream on 2011-05-27
If you can't change the boot sequence in BIOS to make your machine boot from CD or USB, then I think Smart Viking has mentioned the only practical way to do it.

---

### Post by lightstream on 2011-05-27
although... you can apparently make Grub2 boot from an ISO image. Even if you can do this on your system, it's going to take a bit of messing about to install Ubuntu this way though - you might be able to do it by creating a partition that does little other than hold the ISO which you then boot from, and install onto the other partition. Afterwards you should then be able to use Gparted to delete that partition, that is if Gparted will let you modify the system partition. If not, you'd be stuck with the two partitions.

See [this thread]("http://ubuntuforums.org/showthread.php?t=1549847").

---

### Post by ornothaloapq on 2011-06-21
I put the hard drive into an enclosure and plugged it into a working ubuntu computer (11.04). I looked  at the link the person above posted but I couldnt make Amy sense of it. If anyone could help me out with simpler instructions I would appreciate it.

---

### Post by collisionystm on 2011-06-21
> **ornothaloapq said:**
> I put the hard drive into an enclosure and plugged it into a working ubuntu computer (11.04). I looked  at the link the person above posted but I couldnt make Amy sense of it. If anyone could help me out with simpler instructions I would appreciate it.

Here is simple... make the hard drive your only drive in your computer. Disconnect the one that is using your 11.04.

Now put the Server Ubuntu CD in the drive. Boot from the Server UBUNTU ISO. Install it " on your computer " now take out that drive and put it into the other box. Re-Connect your 11.04

---

### Post by spcwingo on 2011-06-21
> **ornothaloapq said:**
> The bios is locked down on this machine. It is inaccsessable for some reason.

If by the above you mean a BIOS password, just unplug the system, open the case, and pop out the CMOS battery for a few minutes.  After that reassemble, fire your rig up, and enjoy your password free BIOS.  :popcorn:

---

