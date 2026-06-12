---
title: "Vim can not change mode"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by crsiny on 2009-01-06
My vim can not change mode from the insert to Normal mode , press the ESC but only the cursor on the screen flashing without changing.
What should I do.

Ubuntu 8.10 and VIM with gui 7.1.314.

---

### Post by bump_ on 2009-01-06
Even if you are out of Insert mode, the cursor still flashes. For example, try prssing h,j,k, or l. if you are in Insert mode, the letter will type. If you are out of insert mode, the letters will move the cursor.

---

### Post by crsiny on 2009-01-06
> **bump_ said:**
> Even if you are out of Insert mode, the cursor still flashes. For example, try prssing h,j,k, or l. if you are in Insert mode, the letter will type. If you are out of insert mode, the letters will move the cursor.

Yes, I know some about VIM. Well , may be it my mistake to describe.

When I press  down ESE without Up the cursor is black but when UP it is still do nothing like in the insert mode , but I want to go to Normal.

When press CTRL+C , it seems to go to the Normal.

---

### Post by llama320 on 2009-01-06
do you have the same problem happen when you are in non-gui Vim? open a terminal and just type
```
vim <filename>
```
has this problem just recently started happening?
this might be of help:
[http://www.ph.unimelb.edu.au/~ssk/vim/]("http://www.ph.unimelb.edu.au/~ssk/vim/")

---

### Post by crsiny on 2009-01-06
> **llama320 said:**
> do you have the same problem happen when you are in non-gui Vim? open a terminal and just type
```
vim <filename>
```
has this problem just recently started happening?
this might be of help:
[http://www.ph.unimelb.edu.au/~ssk/vim/]("http://www.ph.unimelb.edu.au/~ssk/vim/")

The same as gvim. In face I have the gvim but almost in terminal with NON-Gui.

---

### Post by mongmong on 2009-01-07
I have met the same problem with Ubuntu 8.10 and vim 7.1.314

When I want to go back to the normal mode from insertion mode, pressing ESC, the cursor flashes and vim stays at insertion mode.

I have another box running Ubuntu 8.04, no such problem found there.

I use Ctrl+C/Ctrl+ESC/Ctrl+[ instead now, but combined keys are not convenient.

---

