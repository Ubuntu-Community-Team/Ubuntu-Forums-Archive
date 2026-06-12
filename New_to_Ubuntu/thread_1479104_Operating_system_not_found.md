---
title: "Operating system not found"
date: 2010-05-10
forum: New to Ubuntu
---

### Post by Mousetrapreplica on 2010-05-10
Hi
I'm a total newbie to Linux, but as the whole ethos behind it was so impressive I wanted to give it a try.
 
I have an old PC running a 750 P3 CPU, 256MB of RAM and 2 x 40GB hard drives.
It has run XP Pro successfully for years.
I did my research and Xubuntu seemed to be a suitable version of Linux for the spec of the machine.
 
I downloaded Xubuntu 9.04, ran the Live CD and liked what I found. I decided to install from the disk onto the primary hard drive and replace XP with Xubuntu.
This all seemed to go well until I came to boot at the end and I got the message 'Operating System not found'
 
I went back to the Xubuntu website and downloaded version 10.4, went through the same process and arrived at the same result.
 
It occurs to me that I have done/am doing something wrong that is so fundamental that it could be embarrassing, but I can't figure out what.
 
I have tried changing the boot order. I have checked the Forums and there seems to be a lot of discussion about the master boot record which I don't entirely understand as I would have expected the operating system to come with it's own mbr.
 
Any help would be hugely appreciated.

---

### Post by Irony on 2010-05-10
Make sure that one drive is the master and that you are installing to that master. You might try physically unplugging one of the drives so that the install can only be all on one drive including grub. After that you can then fiddle around with reconnecting the second drive and determining the correct pin positions for master and slave (assuming old style ide drives).

Alternatively assuming you've installed correctly and are already getting to a grub screen (press shift if you don't see the screen whilst booting up) or Press Ctrl+Alt+Del when you get the error message at boot to boot into grub then press e for edit than replace root=uuid with /dev/sda1 and delete the no-floppy line.

Where sda1 is whatever yours actually is (it might be hdaX). Note that the e for edit is only temporary for that boot.

---

### Post by Mousetrapreplica on 2010-05-10
Massive thanks Irony, doubley so for responding so quickly.
I disconnected the hard drives one at a time and when I did the second one I got a GRUB screen followed by a login, a fleeting glimpse of a Xubuntu splash screen, a very long blank screen, and then XUBUNTU.
 
I'm in business.
Thanks again

---

