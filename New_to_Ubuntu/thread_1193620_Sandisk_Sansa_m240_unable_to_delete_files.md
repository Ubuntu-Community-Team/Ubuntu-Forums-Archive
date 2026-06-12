---
title: "Sandisk Sansa m240 unable to delete files"
date: 2009-06-21
forum: New to Ubuntu
---

### Post by adventure man on 2009-06-21
Hi guys, I have the Sandisk Sansa m240 1 GB mp3 player.  In Ubuntu 8.04.2 I am able to add mp3's to the player, yet am completely unable to delete them from the player :confused:  The error I receive upon hitting the delete key is: "Error removing file: Read only file system".

Is there a known bug with Sansa mp3 players?  Am I doing something wrong?:confused:

---

### Post by gackt on 2009-06-21
Hi, try this, plug the sansa into windows operating system and right click the sansa, properties > tools > error checking > check now > and select all options.

---

### Post by adventure man on 2009-06-22
> **gackt said:**
> Hi, try this, plug the sansa into windows operating system and right click the sansa, properties > tools > error checking > check now > and select all options.


ok that worked to get me to be able to delete files.  One huge problem though,  I delete the files and ubuntu shows they are gone yet the amount of free space doesn't change (I had a 50MB audio book in there, deleted it, I still have only 850 MB free, it should be 900MB to account for the deleted files).  Also I plug my mp3 into my headphones have a listen and the songs are still there, yet ubuntu shows them as gone.  Here is a screenie, note on the bottom the amount of free space, this is after deleting all the files.  Am I deleting wrong?  Should I be deleting them with a music program like rhythm box? :confused:

[[IMG]http://i242.photobucket.com/albums/ff89/quasimodo69/th_Screenshot-AUDIBLE-FileBrowser.png[/IMG]](http://i242.photobucket.com/albums/ff89/quasimodo69/Screenshot-AUDIBLE-FileBrowser.png)

---

### Post by michy99 on 2009-06-22
It sounds like the files are being moved into a Trash folder instead of actually being deleted.

---

### Post by gackt on 2009-06-23
Yes its possible that the file is being sent to trash bin instead of deleted that instant. Try this: open your sansa in ubuntu (as portable media storage), and then ctrl + h (this will show you the hidden files), look for .trash001 or any folder that has .trashxxx and delete it. It should free more space (hopefully the one that you expect to gain). 
Next time you want to delete something try deleting with shift+del as it will by pass the trash folder. Actually, even if u are not shift+deleting, Ubuntu will prompt you with warning like "there is still item in the trash, would you like to remove it" when you try to eject the sansa, choose yes and the trash will be flushed. Let me know if this works for you. Cheers.

---

### Post by adventure man on 2009-06-23
thanks guys, appears to have worked. :D

---

