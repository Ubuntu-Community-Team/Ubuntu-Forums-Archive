---
title: "How to do batch convert ps2pdf"
date: 2009-05-12
forum: New to Ubuntu
---

### Post by captain_rob on 2009-05-12
Hello Ubuntufriends,

I've a simple question. 

I need a batch command for **ps2pdf** to convert numerous .ps files to .pdf files. 

Filenames and directory don't have to be changed.

Thanks in advance :)

---

### Post by Dill on 2009-05-12
Are the files all in the same directory? If so, you can do this:

```
for FILE in *.ps
do
    ps2pdf $FILE
done
```

Otherwise, if they're in multiple directories, you may be able to combine 'find' with 'xargs' to accomplish the same thing 

Cheers,
Dill

---

