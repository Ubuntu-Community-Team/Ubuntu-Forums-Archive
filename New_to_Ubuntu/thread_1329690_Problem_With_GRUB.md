---
title: "Problem With GRUB"
date: 2009-11-17
forum: New to Ubuntu
---

### Post by Cooter2543 on 2009-11-17
Here's my setup:

500GB SATA - Ubuntu 9.10
82GB SATA  - Windows XP
20GB IDE   - Ubuntu 9.10

My friend is was having problems with Windows, so I offered to install Ubuntu on his HDD from my computer (because his CD-ROM drive is not working.)
After the install when I remove his HDD, I cannot boot from my primary HDD (500GB SATA.) I get the message:

Loading Grub
Cannot find Hard Disk
Grub Rescue>

I can still boot from my Windows HDD if I set it to primary in my BIOS. If I reconnect my friend's HDD (20GB IDE) then then Grub screen does show up, and I can boot from any disk I want.

How can I set it back to load grub from my 500GB SATA?
If I were to connect my friend's HDD back into his computer, will that work with no further configuring?

I appreciate any help.

---

### Post by kansasnoob on 2009-11-17
Assuming your 9.10 was running grub2 this should help:

[http://www.openpeta.com/index.php/how-to-recover-ubuntu-grub-after-windows-installation/](http://www.openpeta.com/index.php/how-to-recover-ubuntu-grub-after-windows-installation/)

If you're not sure I'd probably need to see the output of the Boot Info Script run from a Live CD with that extra drive NOT plugged in:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

---

### Post by snkiz on 2009-11-17
A lot of diagnostics for a simple problem (Good to learn what you did.) You installed grub to the drive you removed (to the mbr as well I'm guessing)In the process you must have rewritten your mbr to point to the drive you removed. Reinstall grub without your friends drive installed you should be good.

---

### Post by Cooter2543 on 2009-11-17
I appreciate the help guys. 

How do I boot from the live CD? When I select Boot from first Hard disk, I get the same error.

Grub loading
error: no such disk
grub rescue>

---

### Post by JBAlaska on 2009-11-17
First off, unless you and your friend have the exact same computers(MB/Chipset?Video card etc.), what you did will not work..

Hopefully you have a working CD drive, insert the LiveCD, reboot, enter your system BIOS and enable "Boot from CD", change the boot order to "Boot cd-rom first", save and exit.
Does the Live CD boot now? If so see this Wiki on Grub2
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)
Go to the "Recover Grub 2 via LiveCD" section.

---

### Post by kansasnoob on 2009-11-17
> **Cooter2543 said:**
> I appreciate the help guys. 

How do I boot from the live CD? When I select Boot from first Hard disk, I get the same error.

Grub loading
error: no such disk
grub rescue>

Select Try without changes to hard drive.

---

### Post by kansasnoob on 2009-11-17
> A lot of diagnostics for a simple problem 

I'll admit that's the lazy way out:)

In this case I simply could have said, "once you're chroot in the proper partition run "grub-install -v" then I could see what version grub is installed.

Then if the OP asked which partition to mount and chroot I could ask for fdisk -l, etc, etc.

OTOH if someone needs help beyond a non-specific web-link I'd just as soon see it all at once. Then I can type system specific commands.

---

### Post by snkiz on 2009-11-17
No no don't get me wrong, I tried that script its great. its just I'd rather tell the newbs whats going on in general terms and let them research the method themselves. They'll ask less questions latter that way and become self sufficient... Then again some need more help then others ;)

---

### Post by snkiz on 2009-11-17
> **JBAlaska said:**
> First off, unless you and your friend have the exact same computers(MB/Chipset?Video card etc.), what you did will not work..

Hopefully you have a working CD drive, insert the LiveCD, reboot, enter your system BIOS and enable "Boot from CD", change the boot order to "Boot cd-rom first", save and exit.
Does the Live CD boot now? If so see this Wiki on Grub2
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)
Go to the "Recover Grub 2 via LiveCD" section.
I don't see why it wouldn't work, I am assuming that is his friends sole drive and there are no proprity drivers involved. My kernel has all kinds of crap I don't need in it. I've changed hardware in my system before without having to do anything to get up and running again.

---

### Post by JBAlaska on 2009-11-17
> **snkiz said:**
> I don't see why it wouldn't work, I am assuming that is his friends sole drive and there are no proprity drivers involved. My kernel has all kinds of crap I don't need in it. I've changed hardware in my system before without having to do anything to get up and running again.

I guess I assumed that there were proprietary drivers involved LOL

The OP seems to have buggered off in any case. :-)

---

### Post by Cooter2543 on 2009-11-17
Thank you, I got it working now. I appreciate the help.:)

---

### Post by ranch hand on 2009-11-17
Mark the thread solved in thread tools (top of this page).

---

### Post by Cooter2543 on 2009-11-18
BTW, the 20 GB HDD did work in my friend's computer. Hooked it up and it booted fine the first time, no problems.

---

