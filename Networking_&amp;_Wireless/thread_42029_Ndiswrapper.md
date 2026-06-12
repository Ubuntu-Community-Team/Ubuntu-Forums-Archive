---
title: "Ndiswrapper"
date: 2005-06-15
forum: Networking &amp; Wireless
---

### Post by Freestyle Skater on 2005-06-15
I know problems with ndiswrapper make up a large part of traffic on this forum, but I have looked and can't seem to find the answer to my problem.  I have normally been able to fix the problems, but this time I'm stuck.

I had ndiswrapper working perfectly under Ubuntu 4.x.  I upgraded, and I lost wireless support so I uninstalled ndiswrapper and reinstalled from the install disk using the same driver files that worked under 4.x.  After a bit of fighting, I got my drivers installed, and I go the modprobe to work perfectly (I had the operation error that many others experienced).  After doing a "sudo modprobe ndiswrapper" I try "sudo ifup wlan0", which has always worked before.  I get the same output, but when I get to the DHCP 255.255.255.255 Interval 3 or whatever, it just keeps looking for the network over and over until finally it gives up on me.  This is rather frustrating when people 5 feet from you are surfing away.  Sorry I don't have the actual output, but I don't have net on my laptop while it's down.  If someone really thinks it would be helpful, I'll burn it to a cd and upload it.

At this point I'm almost ready just to reinstall the 4.x kernel to fix the problem and wait for 6.0 to come out.  Thanks in advance for any help.

---

### Post by rachii on 2005-06-15
dumb question but....you say you installed it from the install disk?  did you upgrade the packages from apt afterwords or just keep the old packages?

for me, when i updated, it just worked

---

### Post by Freestyle Skater on 2005-06-16
I kept the package from the disk because my primary source of internet is wireless, and using ethernet is a bit of a pain.  I will try to get ethernet access though and update the package to see what effect it has.

---

