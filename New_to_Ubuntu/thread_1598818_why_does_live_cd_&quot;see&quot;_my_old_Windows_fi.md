---
title: "why does live cd &quot;see&quot; my old Windows files?"
date: 2010-10-17
forum: New to Ubuntu
---

### Post by RLCGRN on 2010-10-17
I'm currently trying 10.04 on the live cd.  Under _Places_ I can view my hard drive contents, and there I can see my folders and files as setup under MS Windows.  When I go for the full install of Ubuntu, will this still be the case?  Will this allow me to avoid from needing to separately save and transfer "39,245 items, totalling 33.5 GB" of items in my Documents and Settings folder, as explained in the "Ubuntu Pocket Guide"?

---

### Post by garvinrick4 on 2010-10-17
> **RLCGRN said:**
> I'm currently trying 10.04 on the live cd.  Under _Places_ I can view my hard drive contents, and there I can see my folders and files as setup under MS Windows.  When I go for the full install of Ubuntu, will this still be the case?  Will this allow me to avoid from needing to separately save and transfer "39,245 items, totalling 33.5 GB" of items in my Documents and Settings folder, as explained in the "Ubuntu Pocket Guide"?Ubuntu can read ext, Ntfs, fat and Windows will read ntfs and fat but not ext and
linux is formatted in ext4 nowadays. So I just make a partition and format it ntfs and will show up in Windows as a drive. F, G , H whatever is next and in Linux it is a sda# so it is rather nice. And yes under places will be all your partitions including Windows.

---

### Post by Ctrl-Alt-F1 on 2010-10-17
> **RLCGRN said:**
> I'm currently trying 10.04 on the live cd.  Under _Places_ I can view my hard drive contents, and there I can see my folders and files as setup under MS Windows.  When I go for the full install of Ubuntu, will this still be the case?  Will this allow me to avoid from needing to separately save and transfer "39,245 items, totalling 33.5 GB" of items in my Documents and Settings folder, as explained in the "Ubuntu Pocket Guide"?
You can see them because Ubuntu is capable of reading NTFS/FAT (Windows) partitions.  The livecd itself just runs in memory (RAM) and is therefore not written to the harddrive.  If you install Ubuntu on a separate partition you will still have access to your windows files, but if you have it use the whole disk, then it will overwrite your windows files rendering them inaccessible.

---

### Post by Vaphell on 2010-10-17
if you decide to keep XP, ubuntu will be able to use its partitions, because it can read and write NTFS filesystems. Many people use NTFS partition to share data between win and linux systems so they always have access to their important files.

---

