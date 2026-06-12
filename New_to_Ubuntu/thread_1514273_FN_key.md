---
title: "FN key"
date: 2010-06-20
forum: New to Ubuntu
---

### Post by dawner on 2010-06-20
Hi, I am quite new to Ubuntu, so I would appreciate help with one problem. I am running Lucid on Fujitsu Siemens Amilo and I have problem with Fn+F3,Fn+F4,Fn+F5 - these are combinations for muting and increasing and lowering sound. Each time they are invoked, they crash the whole Xserver. So my plan is to create sh scripts and ind them to these keys. I successfully made scripts, but the binding part is problem, because i do not know what is key code of Fn key(for binding using gconf-editor).

---

### Post by achase79 on 2010-06-20
there is an article I just read about this today on [linuxjournal.com]("http://www.linuxjournal.com")

---

### Post by J V on 2010-06-20
Fn + key sends a byte signal to the system (along the lines of 0xAA or something)

Unfortunately, if it's crashing Xserver it will always crash, you need to fix that bug first (But then it will work by default)

I can't seem to find an xserver bug that looks to be the same problem as you are having...

---

