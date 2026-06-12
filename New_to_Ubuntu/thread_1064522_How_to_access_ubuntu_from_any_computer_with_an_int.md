---
title: "How to access ubuntu from any computer with an internet connection?"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by taylor102387 on 2009-02-08
I was wondering? Is it possible to access Ubuntu from any computer with an internet connection through a static ip? And if it is, is it easy?
I would like to access my pc from school by just typing in the ip into the adress bar. Sort of like vnc through the net!:p

---

### Post by racie on 2009-02-08
Haha that sounds like a great idea.  Although, I don't know the answer so...

BUMP!

---

### Post by dmizer on 2009-02-08
Just put a copy of [Putty](http://www.chiark.greenend.org.uk/~sgtatham/putty/) on a USB key, and use it to SSH into your home computer. This will give you command line access. VNC over the internet is unusably slow. With SSH, you can forward X11, and open individual graphical interfaces (like Open Office) without having to forward the entire desktop.

You can also give your home computer a URL by using a free dynamic host like [dyndns](http://www.dyndns.com).

Be sure to check with your school administration to make sure it's okay to do this, most schools I know of would be against this kind of activity, but if you showed them why you wanted to do it they might be open to the idea.

---

### Post by cybergalvez on 2009-02-08
read this thread, it think this is what you are looking for
[http://ubuntuforums.org/showthread.php?t=107503](http://ubuntuforums.org/showthread.php?t=107503)

---

