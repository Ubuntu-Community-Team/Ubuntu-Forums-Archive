---
title: "extract .tgz file to filesystem (/) with the terminal."
date: 2011-02-10
forum: New to Ubuntu
---

### Post by latestbeats on 2011-02-10
I want to copy the files in my .tgz file to / with the terminal. so i don't want to move them to a folder just the harddrive itself.
How can i do this?:confused:

---

### Post by Luinar on 2011-02-10
To extract from .tar.gz

```
tar -zxvf FILENAME

```However, is there any particular reason why you want to extract them to / rather than to your home directory? I'd advise against extracting into the file system as it should really be left alone unless you have a specific reason to put files there and know what you are doing.

---

### Post by latestbeats on 2011-02-10
It's a backup file. So i want to replace te folders without removing the originals.
for example:
In my .tgz file i have the folder /usr/share/
 
And i want to replace this folder. but without removing the original /usr/ folder + content.
is this possible?

---

### Post by Stephen Morgan on 2011-02-10
Yes, that should work. I just did the same thing myself. Any files that get in the way will be overwritten, of course, so be careful with the sudoing.

---

