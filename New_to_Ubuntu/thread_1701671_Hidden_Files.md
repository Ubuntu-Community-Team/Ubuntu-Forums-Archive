---
title: "Hidden Files"
date: 2011-03-06
forum: New to Ubuntu
---

### Post by COMPUTIAC on 2011-03-06
Hello , last week I had experimented with WINE , trying to run different programs on it but gave up .

  I thought I removed everything  ( both WINE and all the programs ) . I now find after running disk analyzer , it still exist . I have finally  found my way to it , I opened the home folder , I used  ctrl+h  to find hidden files .

  I can get to the folder but , can  open it , but can't delete it as I do not have permission .

How do I obtain permission , is there some code to enter in a terminal ? If so what is the code ?



COMPUTIAC

---

### Post by kerry_s on 2011-03-06
press-> alt+f2
type-> gksudo nautilus /home

---

### Post by COMPUTIAC on 2011-03-06
Hello kerry_s ,  your advice did the trick , am I correct in thinking this gives temporary root permission to change things ?


Thank's alot , 

  COMPUTIAC

---

### Post by anand warik on 2011-03-07
> **COMPUTIAC said:**
> 
How do I obtain permission , is there some code to enter in a terminal ? If so what is the code ?

COMPUTIAC

Even I came across this problem many times. Finally found a PDF file for Unix/Linux command reference from FOSSwire.com which pointed to following commands. 

rm -f *file*     #force remove *file*
rm -rf *dir*     #force remove *dir*

Those commands should be preceded by sudo if not declared previously.

---

