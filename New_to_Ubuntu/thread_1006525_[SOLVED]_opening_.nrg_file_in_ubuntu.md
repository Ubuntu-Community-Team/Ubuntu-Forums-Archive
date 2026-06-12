---
title: "[SOLVED] opening .nrg file in ubuntu"
date: 2008-12-09
forum: New to Ubuntu
---

### Post by brijraj22 on 2008-12-09
is there any software in ubuntu repositories that i can use to open/edit .nrg files.(its a type of cd image file,opened in windows through magic iso program)?
if yes then how to download and install it.
(i am running ubuntu 8.10 nd am pety new to linux.dont know how to install a program so plz explain in detail)

---

### Post by binbash on 2008-12-09
you can convert them to iso with  : 

sudo apt-get install nrg2iso

then you can mount it (sudo mount -o loop asdasd.iso /mnt/iso) ,edit , rebuild etc.

---

### Post by brijraj22 on 2008-12-09
i installed nrg2iso but dont know how to proceed further. sorry for the seemingly very stupid question but how do i run the program nrg2iso,its not there in my applications menu anywhere.i tried to open the nrg file by right clickin it nd then trying to find the program,but couldn't do it either. in fact, i had also installed a program mount manager but i couldnt find it either.i'm very new to ubuntu,so plz. ignore my idiocy. is there a way to do it in GUI instead of using the terminal?

---

### Post by binbash on 2008-12-09
nrg2iso image.nrg image.iso

---

### Post by pramtung on 2009-11-03
Thank you.. what a great help..

---

