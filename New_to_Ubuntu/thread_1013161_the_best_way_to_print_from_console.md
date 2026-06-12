---
title: "the best way to print from console"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by AFCB on 2008-12-16
hello my friends
i'm from portugal, by the way sorry for my english):P

there is my question.

i have an office that have many network printers, and everyday i have many files to print.

i'm trying to print from console, the .pdf files go ok but the .doc files seems to print with errors, blank pages, special characters...:(:(:(

i'm using the next comand    ***cat nameoffile | lpr***

i drag files in to the console, to get the right directorie.

what im doing wrong??what is the best way to print from console??

regards

---

### Post by jpeddicord on 2008-12-16
I think the reason it isn't printing right is because you are using .doc: it's a proprietary format probably not understood by lpr. OpenOffice might be able to print them:

```
openoffice -p filename.doc
```

The disadvantage here is that it might require a graphical display to print; I haven't tried it myself.

---

### Post by AFCB on 2008-12-16
> **jacobmp92 said:**
> I think the reason it isn't printing right is because you are using .doc: it's a proprietary format probably not understood by lpr. OpenOffice might be able to print them:

```
openoffice -p filename.doc
```

The disadvantage here is that it might require a graphical display to print; I haven't tried it myself.


thanks friend

i will try.

there is any comand to put to especify a determinated print?before send the files??

one more time thanks

---

### Post by niteshifter on 2008-12-16
I take it you mean to print to a specific printer?

```
openoffice -pt <printername> <filename>
```

FYI, the -p and -pt do not invoke the GUI.

---

