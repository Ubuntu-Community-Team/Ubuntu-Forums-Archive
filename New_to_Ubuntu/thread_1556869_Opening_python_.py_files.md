---
title: "Opening python .py files"
date: 2010-08-20
forum: New to Ubuntu
---

### Post by mrphud on 2010-08-20
Hello,

So....

I have python 2.6 IDLE installed.

What I would like to do is if I save a .py file, close it, and then try to
open it again by double clicking the icon, I would like it to open up in the IDLE GUI window so that I can F5 (quickrun) it.

Right now I have the .py filetype associated with the IDLE start script so that when I open the .py file, IDLE interpreter opens up as well. This is a problem because I can only have one window open at a time!!!

So what do I associate .py files with in order to open only the .py editor and not the interpreter?

Is this clear or do I need to restate anything?

Thanks in advance

---

### Post by gdonwallace on 2010-08-20
Sounds like it may be IDLE that is causing the headaches.  Not knowing exactly what it is, it sounds as if IDLE can only open in one way with the interpreter in one window and the editor in another.

You might try Dr Python, its in the repos and its one that I use.  Once you have created a python script, the next time you start it, that script will be auto loaded.  The other thing is that Dr Python runs in one window, but shows 3 different "frames".  The editor as most prominent, below that the actual interpreter where you can type commands or when you run scripts will show what happens and a third that shows useful information about the script itself.

---

