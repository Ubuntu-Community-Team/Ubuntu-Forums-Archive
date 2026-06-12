---
title: "Can't remove Xubuntu boot"
date: 2009-04-12
forum: New to Ubuntu
---

### Post by IgotsDibs on 2009-04-12
Hey, I could really use your help. I tried running Xubuntu 8.1 off of a live CD, then I tried to remove Xubuntu from my computer. I deleted the partitions and I removed it in windows program manager, but I think those files might've been from a failed attempt to set up Xubuntu inside Windows. So now every time my computer boots up, it asks if I want to run Xubuntu or Windows Vista. How do I get rid of it asking which one? I just want Vista on here, but I can't wipe the hard drive. I need all the files on here intact.

Thanks.

---

### Post by halitech on 2009-04-12
can you still boot into Xubuntu? If you can, you can edit GRUB so it boots vista after a wait time of 0 seconds. if not, you can boot from your vista install cd (if you have one) and restore the MBR. Failing that, look into Super Grub boot disk to repair the mbr.

---

### Post by zvacet on 2009-04-12
If you deleted Xubuntu partitions but you still see Xubuntu in grub then try [this.]("http://www.users.bigpond.net.au/hermanzone/p18.htm#MbrFix.exe")

---

