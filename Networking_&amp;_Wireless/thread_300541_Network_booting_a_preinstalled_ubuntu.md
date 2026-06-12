---
title: "Network booting a preinstalled ubuntu"
date: 2006-11-15
forum: Networking &amp; Wireless
---

### Post by patrickweber on 2006-11-15
I am trying to setup a renderfarm (actually, I had it setup on windows, but windows memory management caused me to rethink that).

What I would like to do, is use one main machine that has Ubuntu server installed along with Blender, Yafray, and my renderfarm client software.  Then, each machine will network boot and grab the operating system files from that server and prepare itself for accepting the files for processing.

Unfortunately, some of the machines on my network don't have built in gigabit ethernet or don't support network booting.  Therefore, i have installed gigabit pci cards in each machine.  Also, each machine has a floppy drive in it (I have an abundant supply of those) simply for installing some sort of network loader on a floppy which will perform the same function as a network boot supporting bios.

I can't seem to locate any tutorials or information about how to go about booting a PRE-installed system.  Each tutorial that I have stumbled upon talks about how to boot the ubuntu installation over a network, not a preinstalled system.

If anyone has any tips or links to tutorials that would be great.

---

