---
title: "Prinnting from Command line prints blank page, not the file."
date: 2009-06-10
forum: New to Ubuntu
---

### Post by Coder68 on 2009-06-10
I am only a few hours into using Linux.
I am running Ubuntu 6.06 LTS (It is the only Ubuntu the runs on my Shuttle box correctly.) 
 
I installed a HP JetDirect Samsung 1430 printer and tested it from the GUI. It works perfectly. I printed file1 in my home dir, via the GUI, and it prints that fine.
 
If I use the command line to print the same file, the page just comes out blank. My default printer is set correctly. 
 
```
lpinfo -v | grep socket  returns network socket
```
 
To print the file I use:
 
```
coder68@ubuntu:~/test$ lp file1
```
 
It sends the print job to the printer, but the page is blank. And yes, the file does have some text in it! ;)
 
All I could find about blank pages were issues with an extra page or blank lines.
 
Any ideas what I am doing wrong?

---

### Post by kai60 on 2009-06-10
try using 

```
lpr file
```

---

### Post by Coder68 on 2009-06-10
Sorry, I forgot to mention that I did try 

```
lpr file1
```That just prints a blank page as well.

Thanks for the help!

Any other thoughts?

C68

---

### Post by Coder68 on 2009-06-11
Bump.

This may be a dumb question, but is the default font color when printing from the command line white?  That would explain why it sends the job to the printer, but the page is blank.

C68

---

### Post by Coder68 on 2009-06-11
Double bump!!

lpr file
lp file 

both send a print job to the printer, and it prints a blank page!  Anyone know why?  File does have text in it!!

Thanks

C68

---

