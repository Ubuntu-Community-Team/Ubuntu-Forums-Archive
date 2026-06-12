---
title: "Help! I'm a newbie in need! Problem with GRUB"
date: 2010-02-09
forum: New to Ubuntu
---

### Post by Silas_Parrish on 2010-02-09
I installed Ubuntu a year or so ago...and I love it. I've got twin HDDs, one with Windows XP Home and one with Jaunty. I'm still figuring out this Linux business, so bear with me if I sound like I don't know what I'm talking about. Cause I really don't know. Well, anyway, here's the problem. Every once in a while when I install updates to 9.04 (I'm still trying to decide if I want to make the change to 9.10. Also, I don't know how the upgrade will affect my Windows partition) the bootloader will display what appears to be multiple Linux partitions, and only one Windows. If that's not clear, let me explain it this way: when I first installed Ubuntu, the bootloader listed one Linux partition, and one Windows partition. Now, after several updates and errors, it displays five Linux partitions. When I select any one of them, it loads the same settings, files, and whatnot that it always has. I just can't figure out why there are five of the same menu option...there used to only be one (not including recovery mode, etc.) Does anybody know how I might fix this? Thanks in advance!

---

### Post by Miljet on 2010-02-09
First off, no updates to Ubuntu will have any effect on your Windows partition. So you can quit worrying about that one.

The multiple Ubuntu entries that you are seeing are just new versions of the kernel. They are not new partitions, or different installations. When a new kernel update is installed, the old ones are left in place. That is just in case the new kernel has problems with your hardware, you can boot with the old kernel. They aren't hurting anything by being there. But if they bother you, you can remove the old versions through synaptic. It is a good idea to leave at least two of the latest. And be sure that you know which ones that you want to remove.

---

### Post by Silas_Parrish on 2010-02-09
> **Miljet said:**
> First off, no updates to Ubuntu will have any effect on your Windows partition. So you can quit worrying about that one.
 
The multiple Ubuntu entries that you are seeing are just new versions of the kernel. They are not new partitions, or different installations. When a new kernel update is installed, the old ones are left in place. That is just in case the new kernel has problems with your hardware, you can boot with the old kernel. They aren't hurting anything by being there. But if they bother you, you can remove the old versions through synaptic. It is a good idea to leave at least two of the latest. And be sure that you know which ones that you want to remove.
 Thanks very much! Maybe I should get one of those Linux for Dummies books...

---

