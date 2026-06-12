---
title: "quick way to watch rars"
date: 2011-05-17
forum: New to Ubuntu
---

### Post by mick_86 on 2011-05-17
i have a few files that are rars and want to know a quick way to convert my files so i can watch them. a way that works on linux.

---

### Post by wojox on 2011-05-17
Have you looked at unrar or p7zip?

---

### Post by josephmills on 2011-05-17
vlc my friend

---

### Post by prshah on 2011-05-18
> **mick_86 said:**
> i have a few files that are rars and want to know a quick way to convert my files so i can watch them. a way that works on linux.

rars are an archive (compressed) file format. You need to decompress them to get at the contents of the rar. You can decompress in linux by right-clicking the file name (if a multi part archive, you can right click any file of the multi-part archive) and choose "Extract Here". Then look for a directory with (usually) the same name as the rar file.

You may need to install rar utilities first, you can do this through the software center or from the terminal (Applications-Accessories-Terminal) with the command ```
sudo apt-get install unrar
```

---

### Post by andrew.46 on 2011-05-18
One cool way is to use unrar and MPlayer in the following manner:

```
unrar p -inul myarchive.rar | mplayer -cache 2048 -
```

where of course you would need to change *myarchive.rar* to match the actual name of *your* rar file...

---

