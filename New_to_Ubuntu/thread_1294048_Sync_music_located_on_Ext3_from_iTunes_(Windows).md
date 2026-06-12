---
title: "Sync music located on Ext3 from iTunes (Windows) ?"
date: 2009-10-17
forum: New to Ubuntu
---

### Post by complete-linux-noob on 2009-10-17
Dual boot = Ubuntu & Win7. I use an EXT3 partition for storage, including all music, and enjoy multimedia in Ubuntu !

BUT -  I have an iPhone. (you can roll your eyes!! :))

I know theres work-arounds in Ubuntu, but for maximum functionality & features I wanna try using itunes in Windows if possible. Is there a way I can get full access to the files from Windows without having to make it a FAT32 etc?

I appreciate your answers!

---

### Post by houbysoft.xf.cz on 2009-10-17
It depends on your definition of simple : you could use LTOOLS or something similar, but it is usually slow, and mainly it doesn't recognize larger number of inodes so unless you reformat your ext3 partition to have a smaller number of inodes it's unlikely to work at all.

What I would do is create another Fat/ntfs "sharing" partition which you could then access from both linux and windows.

---

