---
title: "console text editing help?"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by djbushido on 2009-01-09
Ok, i have two tasks i need to do, preferably via console.

I need to read in a collection of text files and copy the contents (appending) to another text file. I would like to use a command like```
someprogram *.txt > new.txt
```

Also, i need a quick way to convert CRLF (Windows) to CR (Linux-pretty sure it is CR right?)

Thanks, i know this is pretty stupid, but i appreciate the help.

EDIT: on the line endings, i would also like a way to convert back to CRLF as well, if possible.

---

### Post by lloyd_b on 2009-01-10
1.  Use two >'s to append to a file:
```
someprogram *.txt >> new.txt
```
will take the output from "someprogram", and append it onto the file "new.txt" (creating "new.txt" if it doesn't already exist.

2.  "sudo apt-get install tofrodos" (or use a GUI package manager such as Synaptic).  This will add the "dos2unix" and "unix2dos" commands (dos2unix converts CR/LF to CR (AKA "newline" in the *nix world), while unix2dos converts CR to CR/LF).

Lloyd B.

---

### Post by Sealbhach on 2009-01-10
Hi, if this helps...

```
cat txt1 txt2 > txt3
```

Will append the content of txt2 to txt1 in a new file called txt3.


.

---

### Post by snova on 2009-01-10
> **djbushido said:**
> OAlso, i need a quick way to convert CRLF (Windows) to CR (Linux-pretty sure it is CR right?)

I think Mac used CR once upon a time, but now, along with Linux, uses LF.

---

