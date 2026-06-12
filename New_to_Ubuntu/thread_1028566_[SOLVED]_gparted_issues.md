---
title: "[SOLVED] gparted issues"
date: 2009-01-02
forum: New to Ubuntu
---

### Post by DMinard on 2009-01-02
I was hoping to resize an NTFS windows XP partition with gparted and it wont let me. if i open gparted and click show features in the gparted menu it tells me that resizing for NTFS is not available. i know that people have used gparted to resize NTFS but y cant i? i am running ubuntu 8.10

[IMG]http://i237.photobucket.com/albums/ff16/dterror/GParted-Features.jpg[/IMG]

---

### Post by wolfen69 on 2009-01-02
```
sudo apt-get install ntfsprogs
``` should allow you to work with windows drives. restart gparted if open.

---

### Post by ibizatunes on 2009-01-02
I had issue something like that, boot to XP run a check disk in xp, (selected to run at next bootup) reboot, do the check disk, then reboot again to your live cd, then increase your partition on your live ubuntu session

---

### Post by DMinard on 2009-01-02
> **wolfen69 said:**
> ```
sudo apt-get install ntfsprogs
``` should allow you to work with windows drives. restart gparted if open.

worked like a charm thanks man

---

### Post by wolfen69 on 2009-01-02
> **ibizatunes said:**
> I had issue something like that, boot to XP run a check disk in xp, (selected to run at next bootup) reboot, do the check disk, then reboot again to your live cd, then increase your partition on your live ubuntu session

gparted does not come with ntfs utilities by default. hence the need for ntfsprogs.

---

### Post by bumanie on 2009-01-02
The solutions above will probably work. Another thing you could do would be to download the dedicated [gparted live cd]("http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=125754") and use that - it's never failed me, whereas, on rare occasions the ubuntu version has not worked.

---

### Post by -kg- on 2009-01-02
> **bumanie said:**
> The solutions above will probably work. Another thing you could do would be to download the dedicated [gparted live cd]("http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=125754") and use that - it's never failed me, whereas, on rare occasions the ubuntu version has not worked.

If I have something to do quick and in a hurry, I usually will pop in the Ubuntu Live CD, and it pretty much has never failed me, but yes, the GPartEd Live CD is specifically set up to do nothing much more than to manipulate partitions on hard drives.

There are times I use it, as well, and as you said it has never failed me.

If you need further information on partitioning, please check out [https://help.ubuntu.com/community/HowtoPartition]("https://help.ubuntu.com/community/HowtoPartition").

---

