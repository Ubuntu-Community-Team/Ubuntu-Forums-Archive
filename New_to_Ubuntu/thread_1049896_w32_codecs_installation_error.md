---
title: "w32 codecs installation error"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by tushar88 on 2009-01-25
i downloaded 2 files  w32codecs_20071007-0.1_i386.deb  &  w32codecs_20071007-0.1.diff.gz  now when i type command 

sudo install w32codecs_20071007-0.1_i386.deb

it gives error below :

install: missing destination file operand after `w32codecs_20071007-0.1_i386.deb'
Try `install --help' for more information.

now what to do with i have my both files in desktop please reply me describing where to keep these files andwhat command to give to install .

---

### Post by Guille Damke on 2009-01-25
If you have them in your desktop, why just don't click on them to install?

---

### Post by jrusso2 on 2009-01-25
Those codecs are in the mediabuntu repository.  You can add that repository and just download them with apt or synaptic.

---

### Post by binbash on 2009-01-25
> **tushar88 said:**
> i downloaded 2 files  w32codecs_20071007-0.1_i386.deb  &  w32codecs_20071007-0.1.diff.gz  now when i type command 

sudo install w32codecs_20071007-0.1_i386.deb

it gives error below :

install: missing destination file operand after `w32codecs_20071007-0.1_i386.deb'
Try `install --help' for more information.

now what to do with i have my both files in desktop please reply me describing where to keep these files andwhat command to give to install .

go to the directory which you downloaded the deb then give : 

sudo dpkg -i w32codecs_20071007-0.1_i386.deb command

but i suggest adding medibuntu repo and install w32codecs from there.

---

### Post by Michael.Godawski on 2009-01-25
hi,

and here it is described in detail how to add the mdibuntu repo and how to install w32 codecs:


[LIST]
[*][https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
[/LIST]

---

