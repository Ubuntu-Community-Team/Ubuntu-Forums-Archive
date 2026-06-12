---
title: "changing owners,group of a external drive"
date: 2009-10-21
forum: New to Ubuntu
---

### Post by 45acp on 2009-10-21
I partitioned an external drive into an ext3 partition and a fat32 partition. After it was finished I changed the owner:group of the ext3 partition from root to james:james with no problem. But I wasn't able to change the fat32 partition group from root to james. I get a permission denied error. I can access and write to the fat32 so it is not a big deal but I was wondering why I can't do this.

---

### Post by mcduck on 2009-10-21
> **45acp said:**
> I partitioned an external drive into an ext3 partition and a fat32 partition. After it was finished I changed the owner:group of the ext3 partition from root to james:james with no problem. But I wasn't able to change the fat32 partition group from root to james. I get a permission denied error. I can access and write to the fat32 so it is not a big deal but I was wondering why I can't do this.

You can't change ownership or permissions on a FAT filesystem because FAT isn't able to handle Unix/Linux-style ownerships and permissions. It simply doesn't have such feature.

The permissions for FAT and NTFS filesystems are set for the whole filesystem, at mount time.

---

### Post by 45acp on 2009-10-21
Thanks for the reply. I thought that might be the reason but I wasn't sure. Thanks again.

---

