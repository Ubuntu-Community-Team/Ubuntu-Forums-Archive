---
title: "speeding up file operations"
date: 2009-10-21
forum: New to Ubuntu
---

### Post by ashu. on 2009-10-21
hi i have a intel core 2 duo procssor , 2 gb ram n i use ubuntu within in windows.
lately i hav noticed the rate of file operations(cut paste / copy paste ) into different NTFS partions very less, ie at a rete of 4mb ps which is generally higher with windows plz tell me how to speeden this up???

---

### Post by martrn on 2009-10-21
NTFS are not native to linux.  The linux native file system for ubuntu is ext3 and/or ext4.  The linux kernel can read NTFS file systems, but can not write directly to a NTFS file system.  In order for ubuntu or gnu/linux to write to a NTFS system it has to use the kernel module FUSE (File systems in Userspace).  FUSE will then call its own set of libries such as the NTFS file system drive.  This means there is extra overhead in read/write access to NTFS file systems, than there would be on a native file system.

I don't think you can speed it up, you are dependent on the ntfs written libraries bwhen copying.

---

### Post by NoaHall on 2009-10-21
Defrag the ntfs partition.

---

### Post by ashu. on 2009-10-22
thank you very much

---

