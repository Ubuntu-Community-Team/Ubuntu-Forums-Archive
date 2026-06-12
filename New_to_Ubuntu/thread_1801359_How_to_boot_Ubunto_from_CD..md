---
title: "How to boot Ubunto from CD."
date: 2011-07-10
forum: New to Ubuntu
---

### Post by sstextile on 2011-07-10
Please tell me how to boot Ubuntu from CD. I have old verson of Ubuntu 9.10 and needs to be replaced by new version of Ubuntu 10.10. The new version is in CD. Also my computer has XP and Windows 7 and Ubuntu 9.10 is side by side. Both the windows verson (XP and Windows 7 ) is in C and D drive respectively. Without disturbing XP and Windows 7 how can i replace Ubuntu 9.10 with Ubuntu 10.10 from CD.

---

### Post by mttrmk on 2011-07-10
just pop the cd in the drive and reboot.When you see you see your motherboards logo go into bios settings.(usually all you have to do is press delete) from there navigate to boot priority options and select cd as primary drive. Save changes and exit.
On some motherboards you can press F11 during boot(When you see you see your motherboards logo) and some options will show up. Choose cd/dvd drive and press enter.

Besides you can upgrade ubuntu much easier from the windows installer.

---

### Post by critin on 2011-07-10
With cd in slot restart comp and press the fkey that applies to your boot.  for eample, f10, f12,.

The easiest way is to upgrade to the 10.04 version from the update manager in synaptic.  There will be no messing with partitions and everything is done for you.  If you still want the 10.10, you can do that later the same way.

critin

---

### Post by mttrmk on 2011-07-10
Sorry double post.

---

### Post by fabricator4 on 2011-07-10
> **sstextile said:**
> Please tell me how to boot Ubuntu from CD. I have old verson of Ubuntu 9.10 and needs to be replaced by new version of Ubuntu 10.10. The new version is in CD. Also my computer has XP and Windows 7 and Ubuntu 9.10 is side by side. Both the windows verson (XP and Windows 7 ) is in C and D drive respectively. Without disturbing XP and Windows 7 how can i replace Ubuntu 9.10 with Ubuntu 10.10 from CD.

You might want to consider 10.04 since it's the LTS (long term support) release - supported until April 2013.

To install, first back up _all_ your important data.  Make sure you backup up all the .hidden files and directories if you want to retain all your program and Gnome settings.

Next, boot off the CD and select install.  When it asks, select manually select partitions.  You need to select your current Ubuntu partition as / (root) directory and it will install all of the operating system there.  The default will probably be to format the partition, which is advisable.  If you have a separate /home partition you will need to set that up as well, but tell it not to format the /home partition.

If you don't currently have a separate /home partition you will have to restore all of your data once the install has finished. - from the backup you just made.

By default the install will install and update grub.
After installation and restoration of your data (if necessary) your system should be as it is now, but will be booting the later OS.

If in doubt, get more help before proceeding, but definitely do back up all your important data anyway.  Bad things can and do happen (but not very often).

It's scary if you've never done an install before, but quite easy and safe as long as you are careful.  As soon as the install is finished run Update Manager to get all the current updates for the release.

Chris

---

