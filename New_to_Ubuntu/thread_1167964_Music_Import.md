---
title: "Music Import"
date: 2009-05-23
forum: New to Ubuntu
---

### Post by rlj399 on 2009-05-23
I imported my music from XP using rythmbox. I got all my music, but then the next day i opened the music player to listen to my music and the files wouldn't play anymore and would have a red circle with a white bar in the middle on the side of the file, any suggestions?

---

### Post by ALIENDUDE5300 on 2009-05-23
> **rlj399 said:**
> I imported my music from XP using rythmbox. I got all my music, but then the next day i opened the music player to listen to my music and the files wouldn't play anymore and would have a red circle with a white bar in the middle on the side of the file, any suggestions?

Could you put the file type and name of the file that won't play? It will help us solve your issue.

---

### Post by ajgreeny on 2009-05-23
Is the xp partition you imported from still mounted?  If not you will not actually have the files to play at the moment.  If you want to play them you will need to mount xp again to the same directory as last time and then try again.  To play them when xp is not mounted you wil have to copy the files to your ubuntu partition, not just import in rhythmbox.

---

### Post by rlj399 on 2009-05-23
they seem to be .m4a files

hmm, how do i know if it's mounted? i can access my XP partition from the places window so i think that means it's mounted. I'll try copying the files.

---

### Post by SuperSonic4 on 2009-05-23
Copying will take a while. I'd use cp from a terminal to save resources. I assume you've got all the codecs installed to play them? If you can navigate around XP using nautilus it will be mounted. Mounted drives also appear if you run ```
df -h
``` in a terminal.

It might be easier to copy a few files as a test first though or make a data partition if space allows it

---

