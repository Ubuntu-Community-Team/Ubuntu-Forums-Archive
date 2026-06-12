---
title: "Stubborn internet problem..."
date: 2005-05-22
forum: Networking &amp; Wireless
---

### Post by VincentP on 2005-05-22
I'm very new to this, so I hope this isn't something simple.  Anyways.. my internet worked fine when I first installed Ubuntu, everything went well, I even installed World of Warcraft via Cedega, and it ran better than on Windows.

I restarted the system and booted into Windows.  It did a file system check (Expected, I did repartition the drive with XP already installed).  Everything was fine there.  Restarted into Ubuntu.  The startup process now takes ages.  It freezes on Configuring Network Interfaces.  It sits there for abut 2 minutes, does nothing, then continues to boot.  It loads a few more things that are all [OK], probably 3 or 4, then theres a "failure to do something" error, that I cannot read because it all scrolls and boots too fast.

I get into Ubuntu.. no internet.  sudo dhclient, no internet.  Switch my Ethernet cable from one onboard LAN jack to the other, sudo dhclient, internet.  Here's the thing, though.  The system wont boot regardless of which jack I use, and once I get into Ubuntu, the one that works is the one I did NOT have plugged in when I booted up the system.  So the problem is not with the motherboard, since both jacks work (They also both work fine in Windows).  I'm using an Nforce3 board, but have 32 bit Ubuntu installed, though I doubt that is the problem, because everything was working fine before.

Also, when I try to play World of Warcraft now, I get a NetConnection error that crashes (actually freezes) the game at startup, so I can't get on there anymore.  That, again, was working fine before.

Any ideas?

---

### Post by britbrian on 2005-05-23
VincentP

Your system as described seems more fundamentally broken to me.

Did you defrag XP before you let Ubuntu repartition your drive ?.  I don't expect repartitioning tools to be able to move files around because it would be trying to defrag and I don't believe thats its job. I could be wrong on that since I always manually partition my drives before OS installs. Did the Ubuntu repartitioner suggest first defragging XP ?

Win2K (& presumably XP) files and the spare space chains get very fragmented all over the Windows partition. Even after a defrag, free space isn't always entirely bunched at the partition end and a few files can be close to the partition end.
So I would have defragged once or twice and visually checked the defragmenters graph display showed only space on the right side where you could safely put the partition split.

You might want to get more info then repost in the Ubuntu Install area and give details about your drive size, the C:\ partitions new capacity, used space & free space reported by XP, size of hidden pagefile.sys. Is the spare space on C:\ atleast 15% of C:\ capacity to do future defrags ?.

In XP rt click MyComputer them Manage then DiskManagement. The partition capacities are only shown in GB. To see their byte sizes, rt click every partition then properties and note the capacities down. These partition sizes should match with what you set the repartitioner to do.

Your observations about network jacks, though odd, don't seem relevant to me.

You could boot Ubuntu in recovery mode just to see what it can report so that you can get more info to your post. Don't do corrective actions until others can help you better in case it borks XP. 

good luck

---

