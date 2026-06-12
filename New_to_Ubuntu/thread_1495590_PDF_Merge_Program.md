---
title: "PDF Merge Program"
date: 2010-05-28
forum: New to Ubuntu
---

### Post by mal_conductor on 2010-05-28
Is there a program to marge PDF files into one large file?

---

### Post by ron999 on 2010-05-28
**pdftk** is in Ubuntu's repository.

---

### Post by Ozymandias_117 on 2010-05-28
You can try ```
cat name1.pdf name2.pdf > newname.pdf
```

---

### Post by mal_conductor on 2010-05-28
> **ron999 said:**
> **pdftk** is in Ubuntu's repository.

thanx... I am going to close this thread

---

### Post by mal_conductor on 2010-05-28
I am trying to merge PDF files with PDFTK...

I found this code to do it:
Examples
Merge Two or More PDFs into a New Document
pdftk 1.pdf 2.pdf 3.pdf cat output 123.pdf

But where do the PDF files need to reside (what directory)?

---

### Post by mal_conductor on 2010-05-28
> **Ozymandias_117 said:**
> You can try ```
cat name1.pdf name2.pdf > newname.pdf
```

Ozy... to do this... Where do PDF need to reside.. or how do I specify where files are and where output to be written?

---

### Post by ron999 on 2010-05-28
> **mal_conductor said:**
> I am trying to merge PDF files with PDFTK...

I found this code to do it:
Examples
Merge Two or More PDFs into a New Document
pdftk 1.pdf 2.pdf 3.pdf cat output 123.pdf

But where do the PDF files need to reside (what directory)?

If the PDF files are in your home directory then your command should work as it is.
If they are in a different directory then change directory using cd command like this:-
```
cd /home/username/directory

```
Then use your original command.

---

### Post by mal_conductor on 2010-05-28
> **ron999 said:**
> If the PDF files are in your home directory then your command should work as it is.
If they are in a different directory then change directory using cd command like this:-
```
cd /home/username/directory

```
Then use your original command.

Thank you... it works fine

---

### Post by gandaran on 2010-05-28
why don't you use something simple with a gui like PDF-Shuffler, you can install it from synaptic package manager, or PDF-Mod from GetDed.

---

### Post by ron999 on 2010-05-28
Yes, PDF-Shuffler looks easy to use.:)
I didn't know about that program.

---

