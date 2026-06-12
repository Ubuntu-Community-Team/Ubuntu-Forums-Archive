---
title: "Mass compress many folders"
date: 2011-04-29
forum: New to Ubuntu
---

### Post by mafi127 on 2011-04-29
Is there somekindow script witch will copress many folders to single files?
I mean copress like this metod. I want to copress folders what are in the /MyFolder and there are several other folders like

/myfolder/folder1
/myfolder/folder2
/myfolder/folder3
etc..

I want to copress thows folders to seperate archive files like folder1.rar, folder2.rar, folder3.rar is there somekindow script witch can to this ?

---

### Post by TeoBigusGeekus on 2011-04-29
Open a terminal inside /myfolder and give this
```
find ./ -maxdepth 1 -type d ! -wholename ./ -exec rar a '{}'.rar '{}' \;
```

---

### Post by mafi127 on 2011-04-29
Thank you for fast replay, works great :)

---

### Post by 3L33T on 2011-04-29
> **TeoBigusGeekus said:**
> Open a terminal inside /myfolder and give this
```
find ./ -maxdepth 1 -type d ! -wholename ./ -exec rar a '{}'.rar '{}' \;
```

I second this!

---

### Post by TeoBigusGeekus on 2011-04-29
Don't forget to mark the thread as solved.

---

