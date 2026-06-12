---
title: "FAT32 format for USB external disk - what do I lose?"
date: 2010-08-22
forum: New to Ubuntu
---

### Post by paker on 2010-08-22
1) I know ntfs is recommended for an external hd that needs to be accessed by both Windows and ubuntu. What do I lose if I format it FAT32? I tried ntfs format but it was not a Disk Utility option. I had to choose between FAT and Linux format.

2) What is the advantage of partitioning external hd? I didn't partition mine. It's for audio and video file storage.

---

### Post by techunit on 2010-08-22
There isn't a real advantage unless you need to wipe it of files or the current format is incompatible or damaged.

---

### Post by HeadHunter00 on 2010-08-22
No specific advantages really. The only reason for using ntfs is so that your hd can handle permissions.

---

### Post by GlazedDonut on 2010-08-22
FAT32 has a file size limit of 4 GB, so you wont be able to store large files on it.

---

### Post by HeadHunter00 on 2010-08-22
> **GlazedDonut said:**
> FAT32 has a file size limit of 4 GB, so you wont be able to store large files on it.
No, thats fat, not fat32. fat32 has a much larger size limit. I forgot how much though. I know cuz my eight gig memory card is fat32.

---

### Post by linux18 on 2010-08-22
ntfs and fat 32 fragment, if its an external HD, then you will need to defrag, if its a flash drive your fine.

---

### Post by coffeecat on 2010-08-22
> **paker said:**
> I tried ntfs format but it was not a Disk Utility option.

Try installing the package ntfsprogs. You need this to be able to create an NTFS filesystem. With ntfsprogs you should find that Disk Utility will be able to format a drive NTFS.

> **HeadHunter00 said:**
> No, thats fat, not fat32. fat32 has a much  larger size limit. I forgot how much though. I know cuz my eight gig  memory card is fat32.

What GlazedDonut was saying is correct. The limit for an individual  **file** in FAT32 is 4GB. I think you're thinking of the filesystem  itself. The limit for the size of a FAT32 filesystem is much higher.

---

### Post by ST3ALTHPSYCH0 on 2010-08-22
> **coffeecat said:**
> 
What GlazedDonut was saying is correct. The limit for an individual  **file** in FAT32 is 4GB. I think you're thinking of the filesystem  itself. The limit for the size of a FAT32 filesystem is much higher.

I hate to split hairs... but it's in my nature. The file size limit of FAT32 is technically 4 Gb- 1 byte.

---

### Post by linux18 on 2010-08-22
> **ST3ALTHPSYCH0 said:**
> I hate to split hairs... but it's in my nature. The file size limit of FAT32 is technically 4 Gb- 1 byte.
if its starts counting at 0 then 11111111111111111111111111111111 is 4GB

---

### Post by paker on 2010-08-23
Thanks. I installed ntfsprog and was able to format the hd in ntfs.

---

### Post by linux18 on 2010-08-23
> **paker said:**
> Thanks. I installed ntfsprog and was able to format the hd in ntfs.
mark the thread as solved :)

---

### Post by pterosky on 2011-06-11
I formatted my 4GB USB flash drive with FAT32, to swap files between Ubuntu and Windows XP, but Ubuntu had problems handling it: the writing of bigger files seemed to go on forever and sometimes froze, the write speed was extremely slow, etc. But after I switched to NTFS format all problems seem to be solved, and it just works

---

