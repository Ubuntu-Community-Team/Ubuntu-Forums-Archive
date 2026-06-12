---
title: "help with corrupted tar ball"
date: 2010-10-11
forum: New to Ubuntu
---

### Post by leeagt on 2010-10-11
Hopefully some can help me out. I backed up my netbook so i could do a clean install of 10.10 . When i try to extract my tar ball back up it gets about half the way through and then gives me the following error :-

gzip: stdin: unexpected end of file
tar: Unexpected EOF in archive
tar: Unexpected EOF in archive
tar: Error is not recoverable: exiting now


Now i have done some googling and realise that i shouldn't have backed up to a fat32 filesystem as it can't handle files over 4 gig in size. Is there anyway to get the rest of the files from my tar ball or have i lost the files ?

TIA Lee

---

### Post by The Cog on 2010-10-11
Ew! That's not nice. I'm surprised tar didn't error when you were writing it. But anyway, I have a feeling that it's bad news. End of file means there isn't any more. It it's because you hit the filesize limit on FAT then there probably never was any more on the disk. It's probably game over, sorry. 

Can I suggest that next time, you install with a separate /home partition. That should allow you to upgrade/reinstall the OS without wiping all your user data. Not that it helps with your current data loss.

---

### Post by leeagt on 2010-10-11
Thanks thought that might be the case. damn fat32 sucks !

---

### Post by leeagt on 2010-10-12
Sorry but just bumping the thread just incase anyone can help. I fear that I may have lost some of my back up hopefully someone more knowledgeable can help

---

### Post by ibizatunes on 2010-10-12
can you get into the .tar ball? and extract small sections at a time?

---

### Post by JackNocturne on 2010-10-12
Since you did a **clean install** of ubuntu 10.10 , you could recover the written-over partition using **testdisk. **Hope it helps.



[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by leeagt on 2010-10-14
Thanks mate , trying testdisk / photorec just now

---

### Post by SlugSlug on 2010-10-14
whats the size of the TAR?

if when maybe it's created the whole file but can't read it??

maybe dd could help move it from one File system to another..?

dd if=/path/to/tar of=/path/to/ext4/space/new.tar

---

### Post by leeagt on 2010-10-14
photorec worked :) i've got all my photos back. *PHEW*
 
Now to get the rest of my backup back

---

### Post by kaldor on 2010-10-14
> **leeagt said:**
> photorec worked :) i've got all my photos back. *PHEW*
 
Now to get the rest of my backup back

Wow, I'm surprised :)

Congrats.

---

