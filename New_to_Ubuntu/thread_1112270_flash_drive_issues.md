---
title: "flash drive issues"
date: 2009-03-31
forum: New to Ubuntu
---

### Post by kdreimiller on 2009-03-31
I have a pny attache 4g flash drive for my CIS class.  I use it primarily on winXP in school to save data files. 

last night i put it in my ubuntu box (8.10) and it worked just fine.  when i went to use it at school today, winxp no longer recognizes it.

the data is still there and ubuntu can see it fine, but xp doesnt wanna play.

any way to get around this or do i just have to bite the bullet and reformat it in winxp and put the data back again and remember to NEVER use it on my ubuntu box?

---

### Post by Anthon on 2009-03-31
What is the format on the stick right now? I never had these kind of problems with FAT32 formatted sticks. But if this is a NTFS formatted one, you might run a higher risk of incompatibilities.
So if you reformat use if that was not on it before (unless you will have a file > 2G on the stick, IIRC that is the FAT32 limit)

---

### Post by kdreimiller on 2009-03-31
meh, now it wont even mount on ubuntu.  this is annoying.

so when/if i reformat on winxp i should format it fat32?

---

### Post by Anthon on 2009-03-31
I would use FAT32, unless you need the NTFS  features (single filesize > 2G etc).
If this is just for moving documents and some images FAT32 is fine.

---

### Post by kdreimiller on 2009-03-31
yeah, its all small excel, pp, and word files.

---

### Post by LowSky on 2009-03-31
just remember you cant just pull them out of the USB port, you need to unmount them, in Windows and Ubuntu

---

