---
title: "[SOLVED] Main menu Shortcut Problem"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by eumetaxas on 2008-12-04
Hi again!
i have installed Stata for the needs of my Msc in Statistics. It is under /opt/Stata/10 , the executable is xstata. if i do

cd /opt/Stata/10
xstata 

it works ok, but 
/opt/Stata/10/xstata crashes.
How can i add the two lines command in main menu?

Thank you

---

### Post by DieB on 2008-12-04
try && inbetween

________________


make a little skript Like:

> #!/bin/sh
cd /opt/Stata/10
xstata 

save it somewhere and the entry in menu simply lets this skript start

---

### Post by zvacet on 2008-12-04
In main menu choose where do you want that program to be (accessories,office,other...),then on the right side click on **new item** and you will see launcher.Under** command** browse to the right path to the executable file.Of course you will give name to the launcher.

---

### Post by eumetaxas on 2008-12-04
> 
DieB
try && inbetween

make a little skript Like:

save it somewhere and the entry in menu simply lets this skript start

&& did not work but the script did!
thanks!

> zvacet  	
In main menu choose where do you want that program to be (accessories,office,other...),then on the right side click on new item and you will see launcher.Under command browse to the right path to the executable file.Of course you will give name to the launcher. 

this is what i had done and did not work

Thank you both for your immediate answers!!

---

