---
title: "Partition problems"
date: 2010-01-23
forum: New to Ubuntu
---

### Post by JamesParnell on 2010-01-23
ok, so ive wiped my ubuntu partition, yay!. but now the 41gb partition won't delete, and i cant put a new filesystem on it...why is this?

Ive tried using Gparted and Palmisest (whatever its called)....whats wrong, and can i destroy the partition from windows CMD? (the partition was ext4...but i deleted the filesystem, but the partition remains)

---

### Post by tgeer43 on 2010-01-24
> **JamesParnell said:**
> ok, so ive wiped my ubuntu partition, yay!. but now the 41gb partition won't delete, and i cant put a new filesystem on it...why is this?

Ive tried using Gparted and Palmisest (whatever its called)....whats wrong, and can i destroy the partition from windows CMD? (the partition was ext4...but i deleted the filesystem, but the partition remains)
If you are running Gparted from a HD installation, try booting a Live CD and running it from there. Make sure the partition in question is not currently mounted.
If this still doesn't work then try providing us with some details (error messages, etc.) so we can help.

tgeer

---

### Post by Gone fishing on 2010-01-24
My guess if you've deleted the logical partition, but can't delete the extended partition (and probably don't want to). However, you don't need to, just create a new logical partition using gparted.

---

### Post by mbzn on 2010-01-24
Are you still using grub? is this the partition with /boot?

---

### Post by JamesParnell on 2010-01-24
> try booting a Live CD and running it from there
I had already removed ubuntu from my harddrive, so i was using the LCD. the problem is that it "scans /dev/sda" for about 15 minutes then i just give up and close it down.

> create a new logical partition using gparted.
I cant, because of the reason above...also, using the built-in partition manager, if i try to put a new NTFS/FAT/FAT32 filesystem on it, i get "modifying the partition" for about 15 minutes. and the same when i try to delete the partition itself.

> Are you still using grub?
No, i have wiped my ubuntu partition and used the XP Recovery console to "fixmbr"

---

### Post by Gone fishing on 2010-01-27
You've got Windows partitions on the drive which work? It seems odd, and might be hardware?

however, Parted magic is cool and has lots of tools like ntfsclone and partition cloning tools. I think I'd be tempted to clone my ntfs partition onto another drive (shockingly quick with ntfsclone) and the thoroughly check the problem drive using the manufactures utilities and possibly low level format and start again.

---

### Post by Jeneral22 on 2010-02-09
James,

I did this last night and lost patience twice before just letting Gparted run it's magic and took a shower. When I came back 30 min later it was done. I stopped it before it finished twice before because I thought it wasn't doing anything. Patience grasshopper... :):)

---

