---
title: "hp 1020 - recognised but not working"
date: 2009-01-01
forum: New to Ubuntu
---

### Post by kimikrishna on 2009-01-01
my printer is hp laser jet 1020..

when i tried to print a page...

it stands still...

but ubuntu printer dialog box [COLOR="Red"][SIZE="6"]shows my printer name[/SIZE][/COLOR] in it.. ?????:confused::confused:

But it is not pritning/// 

how do i make it print in ubuntu ??

in windows , it prints perfect......

why not in ubuntu ???????

---

### Post by kimikrishna on 2009-01-01
from where do i download drivers ??

is this free ?? :D

please do not fell different.. I only know all types of windows os.. 


there i have to pay everything :( even to to get a text editor :(...

help me... I am now thinking of removing xp totally from my comp.

---

### Post by Delever on 2009-01-01
No need to download drivers, you should have them.

Does your printer appear under System->Administration->Printers ?

---

### Post by kimikrishna on 2009-01-01
$ sudo apt-get install build-essential
$ wget -O foo2zjs.tar.gz [http://foo2zjs.rkkda.com/foo2zjs.tar.gz](http://foo2zjs.rkkda.com/foo2zjs.tar.gz)
$ tar -zxvf foo2zjs.tar.gz
$ cd foo2zjs
$ sudo make uninstall
$ make
$ ./getweb 1020
$ sudo make install install-hotplug

I used this in command prompt.. and solved the problem !!! 

thanks !!

---

### Post by kimikrishna on 2009-01-01
SOLVED !!!!!!!!


sorry.. Its not command prompt :O it is terminal :D

what i speak is only about windows os..

@ mods.. you can mark this thread solved !! thanks

---

### Post by Delever on 2009-01-01
You seriously amazed me. Nice that you solved it.

---

### Post by kimikrishna on 2009-01-01
@ delever..

thanks for your immediate responses !

---

