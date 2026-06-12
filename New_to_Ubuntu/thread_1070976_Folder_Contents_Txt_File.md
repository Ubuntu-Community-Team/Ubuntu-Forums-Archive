---
title: "Folder Contents Txt File"
date: 2009-02-15
forum: New to Ubuntu
---

### Post by GaryLittlemore on 2009-02-15
Hi,

Is anyone aware if I'm able to make a txt file of a listing of a folder contents?

What can I use to create the list?

---

### Post by diablo75 on 2009-02-15
I'm thinking you could use the ls command in the terminal, combine it with a pipe and cat to send its output into a text file.  Like this:

```
ls */path/to/folder | cat textfile.txt
```

Take a look at the the manual for ls (type **man ls** in the terminal) to find out about other options you can add in.  If I read it correctly, the * at the beginning of that will make ls show subdirectories and their contents as well.  You could do something like this:

```
ls -s */path/to/folder | cat textfile.txt
```

to have it include filesize in the output.  I've not tried this, but I'm pretty sure I've got the commands right.

---

### Post by binbash on 2009-02-15
ls > asdasdaaaaaaaaaaaaaaaaaa.txt

---

