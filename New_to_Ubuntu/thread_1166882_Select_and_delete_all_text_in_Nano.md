---
title: "Select and delete all text in Nano"
date: 2009-05-22
forum: New to Ubuntu
---

### Post by bennychidge on 2009-05-22
Hi how can I select and delete all text in Nano?

Thanks

---

### Post by NevNiv on 2009-05-22
A quick look here and I couldn't find much [http://www.nano-editor.org/dist/v1.3/nano.html](http://www.nano-editor.org/dist/v1.3/nano.html)

I'm not sure that you can, but I believe ^K (Ctrl K) erases an entire line.  Or you could just erase the file and start over.

---

### Post by bennychidge on 2009-05-22
Yeah same I had been there, I think ctrl - K is actually cut. Just wondering if there was a simple way of selecting all and deleting. File recreation it is

thanks

---

### Post by oxoxbyx on 2011-01-14
maybe not direct using nano but we can use "echo"

for example
```
echo " " > filelocation.txt
```


sorry about my english

---

### Post by mrzero on 2011-05-29
> **oxoxbyx said:**
> maybe not direct using nano but we can use "echo"

for example
```
echo " " > filelocation.txt
```
sorry about my english

Nice trick it write out nothing in a file and deletes all its previous contents.;)

---

### Post by ApOgEEs on 2011-05-29
To select text in nano, move the cursor to the start of the text you want to select, press the Alt-A key combination to mark the start, then move the cursor to the end of the section you want to select. 

press Ctrl+K to cut your selection and Ctrl+U to paste it.

More info can be found here: [https://help.ubuntu.com/community/Nano](https://help.ubuntu.com/community/Nano)

---

