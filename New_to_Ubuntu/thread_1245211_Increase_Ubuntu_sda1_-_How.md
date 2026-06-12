---
title: "Increase Ubuntu sda1 - How?"
date: 2009-08-20
forum: New to Ubuntu
---

### Post by Quarkrad on 2009-08-20
My main 'PC' is Ubuntu 9.04 sitting at sda1 as a ext4 partition - I need more space.  Using a windows (sorry but the GUI is somewhat good!) partition manager I have created a new partition (taken from other partitions on the HD) next to it physically but formatted as ext3.  The windows partition manager has a merge partitions function but does not like ext4.  So I guess I need to run gparted from a boot CD.  Questions are:
Can I format new part as ext4 with gpart/boot CD?
Is there a merge partitions or grow (sda1) in gpart?
If I can do above will my 'PC' on sda1 still be OK after merge/growth?

Thanks

---

### Post by philinux on 2009-08-20
gparted from live cd can do that. But with any operation like this always backup any critical stuff.

---

### Post by Penguin Guy on 2009-08-20
_GParted:_
Format ext4: [COLOR="Green"]Yes[/COLOR]
Merge Partitions: [COLOR="Red"]No[/COLOR]
Grow Partitions: [COLOR="Green"]Yes[/COLOR]

If a partition has 50GB of data on it and you shrink that partition to 40GB, you will loose 10GB. [COLOR="Red"]The partition manager will not warn you about this.[/COLOR] Also, **before shrinking a Windows partition, defragment it**. Generally try and give Windows more room than it needs, but apart from that you're pretty much safe.

---

### Post by mikechant on 2009-08-21
You just want to use gparted to delete the new empty partition and grow (resize) the existing partition into the unallocated space. No need for merging, no data should be lost normally but with all partition changes with any tool there is a danger of data loss (e.g. power goes out while operation is in progress) so backups are always recommended (and you should be backing up anyhow!).

---

