---
title: "cvs"
date: 2010-07-13
forum: New to Ubuntu
---

### Post by cvsuser on 2010-07-13
i am working on a project in concurrent versions system. I am working for
 the first time in it and i've been facing a problem.
if anyone is familiar with it then please tell  this:
i am working on the shell konsole of mandrivalinux. 
when we import a project in cvs then a window shows up at the terminal.
how do we proceed after this?how do we make the modifications in the imported file?
please help

---

### Post by DaithiF on 2010-07-13
Hi, what window -- is it a text editor?  cvs may be launching an editor for you to supply a comment.  

how are you performing the import, if from command line, then use -m to supply a message and avoid the need for the editor to be opened.
e.g.:
```
cvs import -m"first import of project X" directory VENDOR_TAG RELEASE_TAG
```

---

