---
title: "[SOLVED] Nano Highlighting?"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by sanubie on 2008-12-28
I tried turning Nano syntax highlighting on for C code, but it doesn't ever work. I looked up Nano Highlighting in Google, and I tried what this page says to do, but still it doesn't work....


[http://tux.50webs.org/tip_nano_highlighting.html](http://tux.50webs.org/tip_nano_highlighting.html)

It doesn't really explain what to do to get Nano to highlight code. Can anybody help me out here?

---

### Post by Dr Small on 2008-12-28
Just try vim. :)

---

### Post by .Maleficus. on 2008-12-28
The guide worked fine for me.  First, what you should do is open up a terminal and type "nano .nanorc", to create the .nanorc file that they talk about.  After that, in that file, type "include "/usr/share/nano/c.nanorc"" (without the outside quotes) and save it in your home directory.  After that, either make a new C file or open one and you should have syntax highlighting.  Note that you have to save the file before it will highlight anything.

---

### Post by sanubie on 2008-12-28
> **.Maleficus. said:**
> The guide worked fine for me.  First, what you should do is open up a terminal and type "nano .nanorc", to create the .nanorc file that they talk about.  After that, in that file, type "include "/usr/share/nano/c.nanorc"" (without the outside quotes) and save it in your home directory.  After that, either make a new C file or open one and you should have syntax highlighting.  Note that you have to save the file before it will highlight anything.

Okay, I got it! I forgot to include the first part. Thanks! It's fixed.

---

