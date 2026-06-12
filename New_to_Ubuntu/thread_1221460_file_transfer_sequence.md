---
title: "file transfer sequence?"
date: 2009-07-23
forum: New to Ubuntu
---

### Post by paker on 2009-07-23
Is there a way to transfer files in the sequential way?

Say I have 10 folders and 100 files.
Folder_1 has File_1, File_2, File_3, etc
Folder_2 has File_1, File_2, etc


If I highlight all 10 folders and drag-drop them in a USB drive, apparently, the folders and files are not written in the alphanumeric sequence.  

Is there a way to fix it?
Thanks.

---

### Post by llamabr on 2009-07-23
What happens if you just drag one folder at a time?

I'm not sure why it doesn't just work, but can't you tar them, mv the .tar, and then untar?

---

### Post by paker on 2009-07-23
It is unpredictable at best. Some folders look okay. Some don't. Apparently, Linux doesn't move files sequentially, according to an internet article I found. Windows are better. 

Regarding rar and unrar, I don't know how this is related to the problem.
Thanks.

---

### Post by llamabr on 2009-07-23
Not rar.  tar.

If you want the exact same thing to be somewhere else, tar up the folders.  Move the tar, and then untar.

Though again, I'm not sure why moving would disrupt the file structure.

---

### Post by wojox on 2009-07-23
He said .tar not rar
Mount the drive and sort them.

---

