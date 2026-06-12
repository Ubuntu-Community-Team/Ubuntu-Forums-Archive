---
title: "Networking corrupted - possible that I got hacked"
date: 2014-08-12
forum: Networking &amp; Wireless
---

### Post by xigen on 2014-08-12
My browser went to an unsafe site.  It's ubuntu ... safety was presumed.

I ran ClamAV and 109 files were tagged as problematic.  I deleted the files without carefully reading them.  Most were .msi files.

My cat shut down my Ubuntu 14.04 system

When I brought the system back ... it booted as 13.10, and the keyboard and mouse did not work after initial boot (ie. choose ubuntu, memtest, etc).

I tried to get back on the network - I got the message "network unreachable".  
I tried to ping the router (192.168.2.1) .. and 'network unreachable'.
I tried to get a new network connection - no luck

$ ifconfig
eth0  is seen and
lo  

Also USB devices are not working after initial boot.  The Keyboard and mouse light up for a brief moment at boot and then the lights on the keyboard/mouse are no longer lit and there is no response.

And my saved passwords do not work on Firefox (*chrome not tested)

...

How do I re install my networking files?
How do I re install USB connectivity?

---

### Post by tgalati4 on 2014-08-12
I don't have a cat, but if I did, I would not let it use the computer.

If your computer has a CD drive, burn an Ubuntu disk on another system and boot from it.  Recover important files first.  You might need to wipe and reinstall.

It's not uncommon for networking to break.  It's unclear how you would have 13.10 still on your system.  Is this system dual boot?

Keep the cat in another room.

---

### Post by xigen on 2014-08-13
Headaches are abounding.   In good news I backed up all of my /home so.. my files are OK.

I tried to boot from a 14.04 disk -- networking did not work
I tried to boot from a 13.10 disk -- networking did not work

I used a Mint 14 disk -- it worked just fine
I used a Mint 17 disk -- networking did not work.

The theory:  wipe / reinstall is running into a bunch of problems.

How do I mount my 14.04 iso disk and use it as a repository in Synaptic to let me repair my system?

thoughts ... ?... I find the behavior of my system to be very strange.  It has worked really fine for the last 5 months since I built it.

---

### Post by xigen on 2014-08-19
Lessons learned:

1)  I think my bios got horked.  When I started to see strange behavior I wish I had looked into the Motherboard/Bios sooner.   Resetting the bios to a back-up version of the original version helped to get my system working again.

2) ClamAV is cool.  In the future I will quarantine files rather than  delete.  

3)  I will not let the cat reboot the system when I am in the middle of something.   There is now a cover over the power button.

4) I will back up my FF/Chrome book marks on a regular basis.   They were not part of my /home directory and got deleted.

5) I will make a list of:  Motherboard/Processor/Memory/SSD/GPU/Network Driver/  Network config ... and save it on paper.  

6) I will output a list of all installed software.  And save it in a cloud based drive.

7: When frustrated - I will exercise.  It helps me think more clearly.

---

