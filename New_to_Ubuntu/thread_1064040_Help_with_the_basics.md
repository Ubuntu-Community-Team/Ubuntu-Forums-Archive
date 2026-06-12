---
title: "Help with the basics"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by _georgios_ on 2009-02-08
Hello everyone, Im new to Linux & Ubuntu, my friends just installed, and they say that thy can help with everything I need, but I want to learn how to do things myself, so heres the thing, since its just installed, I cant connect to wireless internet, cant listen to my music, and probably other things, but these are the ones that are most important for me...can anyone help me? 

my pc is a Toshiba, 1 Gb Ram

---

### Post by issih on 2009-02-08
Music (assuming you mean mp3s) is solved by installing ubuntu restricted extras..

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Wireless is a bit more complex, we need to know what your hardware is in order to find out what driver is needed.

please open a terminal (Applications->Accessories->Terminal)
then type:
```
sudo lshw -C network
```
hit return and enter your login password when prompted for it.

copy the output of that command (use your mouse and its right click menu) here so we can identify what your wireless chipset is.

Hope that helps

---

### Post by _georgios_ on 2009-02-08
wow thanks, the music did work, now for the internet i&#314;l have to try it later...got homework :S but thanks for the tips n.n

---

### Post by issih on 2009-02-08
Good oh, enjoy the music :)

---

### Post by _georgios_ on 2009-02-08
T.T cant install the music programas, the codes there didnt work.... need the codes for

toshiba satellite L305-SP5806R, speaker problem, ubuntu u.u 

help

---

### Post by issih on 2009-02-08
Um I didn't understand a word of that...

What is the problem?

---

