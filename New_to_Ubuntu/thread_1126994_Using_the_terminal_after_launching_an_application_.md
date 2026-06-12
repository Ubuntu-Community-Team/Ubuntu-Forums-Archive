---
title: "Using the terminal after launching an application from it"
date: 2009-04-16
forum: New to Ubuntu
---

### Post by navaneethkn on 2009-04-16
Folks,

I have started an application through terminal and the terminal window is not usable until the application ends. Is there a way to use the terminal window after starting an application from it? Application should run without depending on terminal. 

Here is how to reproduce what I am saying,

1 - Open terminal
2 - Type "emacs foo.cpp" (or any command to open any application)
3 - After application opened, try to type in the terminal, I can't. Terminal is locked until this application closes.

Any help would be great.

---

### Post by Gramps on 2009-04-16
If you need to use the terminal while running a program in it just open another terminal window and do what ever you need to do.

---

### Post by navaneethkn on 2009-04-16
Thanks for reply. 

I am doing that now. But I am wondering is there anyway to do what I said?

---

### Post by M4rotku on 2009-04-16
Simply add an & after the command

> pidgin &

---

### Post by navaneethkn on 2009-04-16
That worked "M4rotku". Thanks very much.

---

