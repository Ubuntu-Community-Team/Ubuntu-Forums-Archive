---
title: "Windows Backup"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by Martin Marshalek on 2009-01-15
Okay, so I have installed my Ubuntu on a 16GB partition of my hdd (84GB for Vista and 8GB for recovery, I think this is enough) and have been wondering if I could make an iso or disk image of Vista. While I do have a recovery partition, if something went wrong all of my programs will be destroyed. I would have to start from the beginning if my hdd were accidentally formatted or ruined. I was wondering if I could make an iso of my Vista partition in case something went wrong. That way I could reinstall an exact copy of my current Vista. If it matters, 50GB of the Vista partition is already used.

Is there some kind of freeware for this and would it be legal?

---

### Post by handydan918 on 2009-01-15
Perfectly legal. 
I would suggest looking into rsync and dd. You can make a very good backup with rsync like this:

[CODE]rsync -av <source_directory> <target_directory>/CODE]

dd is very powerful, therefore very dangerous. If you reverse the source and the target, you end up with a disk full of zeros....

---

### Post by dark_harmonics on 2009-01-15
Clonzilla is another good option. The problem with dd is that the backup would be the same size as the entire partition or device. So if you backed up the whole hard drive and it was a 120gb drive, the image file would be 120gb. I think you can pass it though gzip to remove the empty space but i've never had much luck with that. I use dd to make iso images from my CDs and backup my bootable usb drives (it keeps all the partition information). 

Clonzilla confuses me a little bit i must confess, but i've gotten it to do local imaging pretty easily.

---

### Post by Paqman on 2009-01-15
Partimage can take an image of a whole partition or drive and compress it down to a sensible size for you. You can either install it in Ubuntu or use it on the excellent Clonezilla LiveCD.

---

### Post by crjackson on 2009-01-15
Some people love the *zilla but it's output looks messy to me. I'm used to working with Acronis TrueImage and spoiled I guess. I have to boot it from a CD or run the backup/restore from windows, but it works none the less. If we move to ext4 however it will slow it down to the point I'll have to switch to something else.

They do have a Linux version available but it's cost is very prohibitive, and I could never get the trial versions to work on my Ubuntu installs.

---

