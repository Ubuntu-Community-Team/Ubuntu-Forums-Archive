---
title: "List Command Help"
date: 2009-09-22
forum: New to Ubuntu
---

### Post by gobrien on 2009-09-22
Hi, I used to have a command for listing the contents of a directory recursively and outputting the result to a text file. I can't remember the damn thing and didn't save it.

I want to list my music collection which is sorted like so

A
 Artist
  Album
   Tracks
B
 Artist

and output it to a text file.

Any help would be great thanks.

---

### Post by stumbleUpon on 2009-09-22
```
 ls -R folderName > fileName.txt 
```

All contents will be recursively available in fileName.txt

---

### Post by astrakhan on 2009-09-22
try: ls -R > ~/tmp.txt

will write lists to tmp.txt in your home directory

---

### Post by gobrien on 2009-09-22
> **stumbleUpon said:**
> ```
 ls -R folderName > fileName.txt 
```

All contents will be recursively available in fileName.txt

Beautiful, that's it. I was close with my attempt, forgot the >  :(

Thanks for the replies.

---

