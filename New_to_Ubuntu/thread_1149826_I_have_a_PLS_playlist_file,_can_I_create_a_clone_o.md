---
title: "I have a PLS playlist file, can I create a clone of track listed in it?"
date: 2009-05-05
forum: New to Ubuntu
---

### Post by legolas_w on 2009-05-05
Hi
Thank you for reading my post.
I want to copy some of my musics from my desktop computer to my laptop.
I have a playlist file which includes all tracks that I like, I am looking for a program to get the PLS file and copy all tracks listed in that file to a separate folder. is there such program available?

thanks

---

### Post by blazemore on 2009-05-05
PLS is a proprietery playlist format. It has been documented by reverse engineering, and is layed out in the following way:

```
[Playlist]
NumberOfEntries=1
File1=http://www.panix.com/web/faq/multimedia/sample.mp3
Title1=Bird Song
Length1=21
Version=2
```

Unfortunately, I don't know regular expressions, so can't grab the File field and save it.

But the process you'd take is this:
1. Find all lines that begin with "File*="
2. Save all text from those lines into a new file.
3. Use the cp command to copy the files to a new folder.

---

