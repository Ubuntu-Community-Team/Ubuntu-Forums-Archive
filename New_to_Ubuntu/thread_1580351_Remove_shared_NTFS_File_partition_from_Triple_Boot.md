---
title: "Remove shared NTFS File partition from Triple Boot rEFit"
date: 2010-09-23
forum: New to Ubuntu
---

### Post by sctracey on 2010-09-23
I am triple booting a new i7 MacBook Pro with Snow Leopard, Windows 7, and Kubuntu 10.04 with a shared NTFS file storage partition with Read/Write access by all three OSes. After much trial and tribulation, I got everything to work right. Only annoyance is that the shared NTFS file storage partition shows up in rEFIt menu as a 4th bootable partition. Any way to remove this? Maybe modify the MBR to show that this partition is not bootable? I tried to remove boot flag on this partition using Gparted, but it was already removed. How can I make rEFIt ignore this partition?

Any help would be greatly appreciated. Thank you.

---

### Post by Underst8 on 2010-12-14
bump?

---

### Post by MrNago on 2010-12-28
So far rEFIt does not allow to custom hide partitions.
NTFS are always seen by rEFIt, and shown in the menu whether they are bootable or not.

I guess your option is wait for an update, or choose a different format for the shared partition.

---

