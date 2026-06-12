---
title: "Cant access Ubuntu Files from Windows 7"
date: 2009-10-13
forum: New to Ubuntu
---

### Post by Newbuntu85 on 2009-10-13
Hi,

I am new to Ubuntu and am using a dual boot along with Windows 7 RC edition along with Jaunty. 

As may the title suggest, I dont want to access the bin or source folder from windows 7. My problem is when I store a file in a Windows NTFS partition from Ubuntu, it doesnt show when I boot into Windows 7, yet from Ubuntu I can access them again. So is there any way by which I can access the files from Windows 7? 

I had also deleted a large chunk from a Windows 7 NTFS partition from Ubuntu. When I rebooted from Win, the files were not there but the space occupied by them still remains. (To give you more clarity, lets say I deleted 5 GB of files from a Windows Partition which was initially occupying 25 GB, when I boot from Win 7, while the disk used shows 25 GB but the files are not there). How can I solve this?

Thank You in Advance

---

### Post by crispy_420 on 2009-10-13
Sounds like a file permission issue. Anyone else want to chime in.

---

### Post by Jose Catre-Vandis on 2009-10-13
> **crispy_420 said:**
> Sounds like a file permission issue. Anyone else want to chime in.

Yeah, try allowing hidden files from explorer, should allow you to see them.

Also test this out with a non OS related file, such as an mp3 or text file, ensuring you have an extension on the file

Better still create a FAT32 partition for shared files

Better still, save your ubuntu files on your ubuntu partition, and install ext2fsd on Windows 7 which will provide you access to your ubuntu files

---

