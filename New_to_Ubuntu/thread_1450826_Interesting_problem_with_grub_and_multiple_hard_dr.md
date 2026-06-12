---
title: "Interesting problem with grub and multiple hard drives"
date: 2010-04-09
forum: New to Ubuntu
---

### Post by biggeekSF on 2010-04-09
I've searched for a similar situation but couldn't find one, so I mayjust  be the victim of a weird hardware configuration.

I had a successful dual boot setup with Windows 7 and Fedora 10 on a 300GB IDE HDD with additional installation of Windows 7 on a 1TB SATA HDD (essentially a backup drive).

When I wiped the Fedora partitions on the IDE HDD and installed Ubuntu 9.10, I encountered the dreaded "grub rescue>" prompt.

Here's the weird thing: When I unplug the SATA HDD and reboot, grub starts as usual and the dual boot works fine. 

I thought I would take this opportunity to learn more about grub, but this problem really baffles me.

Thanks in advance for any help!

---

### Post by jvc26 on 2010-04-11
Which version of Ubuntu are you currently running, and which version of Grub? (```
lsb-release -rd
``` and ```
apt-cache policy grub
```) Sounds to me like you have two installs of grub - one on each MBR of the 2 drives.

The SATA drive is being recognised ahead of your IDE one, and so it looks to the grub referenced on that one for where your OS's are. I can't say for definite, but I would think that is the issue.

If you're using GRUB2, then you can run ```
grub-install <drive>
``` for each of the two drives - that should mean that both MBR's have the same GRUB settings for boot and should fix stuff up. However for Grub 1 I can't say the same solution will necessarily work.

Il

---

### Post by oldfred on 2010-04-11
I have several drives an operating systems and run this script that we use on the forum for boot issues before and after I change anything so I know what is where.

I would run this script with and without your drive to see what it reports and then run easydiff so you can spot the differences.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

### Post by biggeekSF on 2010-04-11
> **Illuvator said:**
> 
The SATA drive is being recognised ahead of your IDE one, and so it looks to the grub referenced on that one for where your OS's are. I can't say for definite, but I would think that is the issue.

That was it...Exactly. Before doing the LiveCD upgrade, I switched boot priority to boot to CD first, but doing that round-robined boot priority so that the SATA drive was recognized before the IDE drive.

I got so focused on grub that I didn't realize is was a BIOS issue, and the other installation of grub on the SATA drive throwing the error confused me, as I presumed it was coming from the grub install on the IDE drive.

Grub doesn't look so weird and capricious anymore now that I know what was actually going on. Thanks a bunch!

---

### Post by biggeekSF on 2010-04-11
> **oldfred said:**
> I have several drives an operating systems and run this script that we use on the forum for boot issues before and after I change anything so I know what is where.

I would run this script with and without your drive to see what it reports and then run easydiff so you can spot the differences.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

That's a great reporting script...thanks for the link!

---

