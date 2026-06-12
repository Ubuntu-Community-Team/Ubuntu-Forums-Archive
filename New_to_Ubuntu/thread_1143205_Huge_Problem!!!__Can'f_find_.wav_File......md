---
title: "Huge Problem!!!  Can'f find .wav File....."
date: 2009-04-29
forum: New to Ubuntu
---

### Post by mysticaltopher on 2009-04-29
I right clicked on a .wav file on my desktop and choose the restore option, it then did some thinking and said it was putting the new data into a folder called folder001 (not sure if it was capitalized or not) now I've searched for the folder and for the wav file on my file system and it is nowhere to be found.  Please Help I need this file for work.....Thanks!

Where the heck did it send it?

---

### Post by andrew.46 on 2009-04-29
Hi mysticaltopher,

> **mysticaltopher said:**
> I right clicked on a .wav file on my desktop and choose the restore option, it then did some thinking and said it was putting the new data into a folder called folder001 (not sure if it was capitalized or not) now I've searched for the folder and for the wav file on my file system and it is nowhere to be found.  Please Help I need this file for work.....Thanks!

You could try to search your home directory first:

```
find $HOME -iname '*.wav'
```

which is the most like location for the file. If it is not picked up there you could try your entire computer:

```
sudo find / -iname '*.wav'
```

This search will look for *all* files that have the last 4 characters .wav so it could produce a large result. There are a few ways to cut this result down further but perhaps this will be enough.

I hope this helps you to locate your file?

Andrew

---

### Post by mysticaltopher on 2009-05-01
found it!

---

