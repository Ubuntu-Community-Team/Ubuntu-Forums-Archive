---
title: "ext4 is better than vfat"
date: 2010-09-04
forum: New to Ubuntu
---

### Post by Zacinfinite on 2010-09-04
I had two vfat partitions 13gb and 10gb. 
But i was facing problems downloading files from torrent. 
Usually i got error that file size exceeds disk space even if i tried to download 5gb file in 10gb vfat partition (partition being empty).
I dint enter nothing in fstab, changed permissions and ownership, looked for hidden files etc.
Then i formatted 10gb with ext4, everything works perfect for that partition now.
Any suggestions why this happened?

---

### Post by Ozymandias_117 on 2010-09-04
> **Zacinfinite said:**
> I had two vfat partitions 13gb and 10gb. 
But i was facing problems downloading files from torrent. 
Usually i got error that file size exceeds disk space even if i tried to download 5gb file in 10gb vfat partition (partition being empty).
I dint enter nothing in fstab, changed permissions and ownership, looked for hidden files etc.
Then i formatted 10gb with ext4, everything works perfect for that partition now.
Any suggestions why this happened?

FAT 32 doesn't support files larger than 4 gigs. (Although real life usage works out to about 3.9 gigs)

---

### Post by Zacinfinite on 2010-09-04
can u tell me about size limitations and features of all major partitions? vfat, ntfs, ext4

---

### Post by scorp123 on 2010-09-04
> **Zacinfinite said:**
> can u tell me about size limitations and features of all major partitions? vfat, ntfs, ext4 Feel free to use Wikipedia ):P

---

