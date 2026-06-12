---
title: "Starters Problems"
date: 2008-12-24
forum: New to Ubuntu
---

### Post by The Zune Guy on 2008-12-24
Hi,
After a many a year using windows, I've decided like so many others to give Linux a try. I've installed Ubuntu 8.10 on a partition about 70GB in size alongside an existing 350GB Windows Vista (64 bit) partition. There's an empty 50GB or so between the two from a deleted secondary Vista installation but I can't use it as I (a)don't know how to format it and (b)can't merge it with my existing installation anyway as the swap file is before the main Ubuntu Partition.

**My actual problems:**
Firstly, I can't add themes to firefox. I get the following message:      
*"Firefox could not install the file at" x "because: Download error -228"*


Secondly, I can't save download because I'm told:
[I]"There is not enough room on the disk to save /tmp/x

Remove unnecessary files from the disk and try again, or try saving in a different location"[/I]


THIRDLY, I can't run Synaptic Package Installer because:
[I]"Failed to run /usr/sbin/synaptic as user root.

Unable to copy the user's Xauthorization file"[/I]

There's more, but if I solve this much I'll be happy. I would reinstall but then I'd have to redownload updates and programs. I only have a few gigs of a cap on my connection and can't use them all :(

Thanks

---

### Post by st33med on 2008-12-24
You wouldn't be running as root user, would you?
```
whoami
```

---

### Post by The Zune Guy on 2008-12-24
> **st33med said:**
> You wouldn't be running as root user, would you?
```
whoami
```

Nope, I'm trying a few things as I've found on google but any suggestions still helpful

---

### Post by zvacet on 2008-12-24
That 50GB partition can be used as shared partition.That way you can put there files you want to be able to access from both OS.In that case partition will be format as NTFS.But that is just one option.Second option is to delete swap and then you will have more then 50GB of unallocated space.Add it to your Ubuntu partition.After thar shrink your Ubuntu partition to 10 GB and mark it as root.Rest of free space can be your home partition.There is more options and they are all easy to do ( if you don´t count your time).Yopu can do all of this if you download [Gparted live CD.]("http://gparted.sourceforge.net/")

---

### Post by The Zune Guy on 2008-12-24
> **zvacet said:**
> That 50GB partition can be used as shared partition.That way you can put there files you want to be able to access from both OS.In that case partition will be format as NTFS.But that is just one option.Second option is to delete swap and then you will have more then 50GB of unallocated space.Add it to your Ubuntu partition.After thar shrink your Ubuntu partition to 10 GB and mark it as root.Rest of free space can be your home partition.There is more options and they are all easy to do ( if you don´t count your time).Yopu can do all of this if you download [Gparted live CD.]("http://gparted.sourceforge.net/")

Thanks loads. Will try that now :)

---

### Post by The Zune Guy on 2008-12-24
Ok. Fixed the no space problems. Reboot solved them :). As for the partitions. Just downloaded iso and will try now

---

