---
title: "Repartition NTFS WinXP after Uninstalling Ubuntu"
date: 2009-02-16
forum: New to Ubuntu
---

### Post by quimming on 2009-02-16
So, I'm new to using Linux.  I had different distros booting from my flash drive and eventually liked it so much that I am dual-booting with WinXP.  I used to have 2 partitions, 1 for Winxp, other for data.  I repartitioned the one with WinXP to put on Ubuntu 8.04 using the installer.

I'm buying a new harddrive to have only ubuntu 8.04 and would like to restore my original harddrive to what I had before.  There are some licensed programs I occasionally need to use in WinXP that I would like to be able to use.  It's working fine now with dual-boot using GRUB.

Can I remove ubuntu and grub, restore MBR, and repartition the original drive to restore the space originally allocated to WinXP?  Will it be a messy repartition or does NTFS with WinXP take it pretty well?

I was planning on popping that harddrive back into my laptop on the rare occasion that I need to use it or boot from an external enclosure (if possible, but I don't see why not if a flash drive can be booted).  Or just trying to use Wine with my programs and keeping original hdd as a backup.

Any suggestions?

---

### Post by zvacet on 2009-02-16
I think [this]("http://ubuntuforums.org/showthread.php?t=508927&highlight=uninstall+ubuntu") is what are you looking for.

---

### Post by SlalomMan on 2009-02-16
GParted should be able to do that with no problems. Just delete the Ubuntu and swap partions and extend/grow the NTFS partition to fill the free space. It may take a while, but it should work.

You should be able to boot from the external hard drive, but if you can't Wine should be able to take care of most windows programs that aren't graphic intensive. I have trouble running some games in wine, but other things work perfectly.

Another thing you could do is install XP in a Virtual Machine inside Ubuntu; this would let you run the occasional app that you need without having to use a separate partition on your hard drive or swap out hard drives. The VM will be slower than a native XP install, but it runs pretty quick.

---

### Post by quimming on 2009-02-16
Ah great!  Thanks a lot for the suggestions and link.  I figured it was a pretty typical thing to do, but I was just searching the forum with the wrong terms.

---

