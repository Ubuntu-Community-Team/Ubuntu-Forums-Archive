---
title: "What format should USB drive be?"
date: 2009-04-29
forum: New to Ubuntu
---

### Post by Jekshadow on 2009-04-29
I'm trying to create a usb startup disk (100GB)

FAT16, FAT32, NTFS, EXT2, EXT3, ETX4, what?

Running 9.04 btw

---

### Post by talsemgeest on 2009-04-29
> **Jekshadow said:**
> I'm trying to create a usb startup disk (100GB)

FAT16, FAT32, NTFS, EXT2, EXT3, ETX4, what?

Running 9.04 btw
I'm not sure if it is the best, but I stick all my startup disks as fat32.

---

### Post by binbash on 2009-04-29
If you are going to use it at linux only, ext3.If you are going to use it windows, linux etc : fat32.If you are gonna put files like 4-5gb mkv files : ntfs

---

### Post by barbedsaber on 2009-04-29
all i have to say is
avoid ntfs at all costs. if it is not a windows startup disk, keep away from ntfs. it is slow, easily fragmented, slow, and inefficient with space.
also, it is slow.

---

### Post by leonardo_neo on 2009-04-29
Well flash drive is basically used for transferring small data from one computer to another. We are living in a world, where most of the computers are running on Windows. So I would like to have a file system, which is compatible with Windows.

Now, when it comes to Windows compatible file system, we usually find NTFS, and FAT32. If I have have choose between the two for a flash drive, I will go for FAT32.

Here is a link which gives some light on file systems...

[http://www.testfreaks.com/blog/information/usb-flash-drive-comparison-part-2-fat32-vs-ntfs-vs-exfat/]("http://www.testfreaks.com/blog/information/usb-flash-drive-comparison-part-2-fat32-vs-ntfs-vs-exfat/")

---

### Post by talsemgeest on 2009-04-29
> **leonardo_neo said:**
> Well flash drive is basically used for transferring small data from one computer to another. We are living in a world, where most of the computers are running on Windows. So I would like to have a file system, which is compatible with Windows.

Now, when it comes to Windows compatible file system, we usually find NTFS, and FAT32. If I have have choose between the two for a flash drive, I will go for FAT32.

Here is a link which gives some light on file systems...

[http://www.testfreaks.com/blog/information/usb-flash-drive-comparison-part-2-fat32-vs-ntfs-vs-exfat/]("http://www.testfreaks.com/blog/information/usb-flash-drive-comparison-part-2-fat32-vs-ntfs-vs-exfat/")
However, the original poster specified that it was a boot disk, and as such should run the file system of the OS installed to it.

---

### Post by Paqman on 2009-04-29
> **barbedsaber said:**
> all i have to say is
avoid ntfs at all costs. if it is not a windows startup disk, keep away from ntfs. it is slow, easily fragmented, slow, and inefficient with space.
also, it is slow.

Fragmentation isn't an issue on flash storage. NTFS is technically a much better filesystem than the FAT32 one that all USB sticks come pre-formatted as. FAT32 has the advantage of being universal though, which is a good thing for portable storage.

---

