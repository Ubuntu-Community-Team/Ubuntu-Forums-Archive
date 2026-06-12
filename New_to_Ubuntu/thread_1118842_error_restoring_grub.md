---
title: "error restoring grub"
date: 2009-04-07
forum: New to Ubuntu
---

### Post by faraz_k86 on 2009-04-07
k so my windows got infected...AGAIN.. and i had to reinstall.

i lost my grub, but i fix that all the time, this time i keep getting "unrecognized command"

here is what i do

boot from live cd

go to terminal

type sudo grub

***Im sure i forgot something here***

then root hd(0,0)

***thi is where i get the error***

then setup hd(0)

then quit

---

### Post by faraz_k86 on 2009-04-07
never mind.. got it fixed.

the string i was missing was

find boot/grub/stage1

and mine was hd0,2  not hd0,0

---

