---
title: "How to install GTSBoolean plugin"
date: 2009-08-01
forum: New to Ubuntu
---

### Post by Tapas Bose, India on 2009-08-01
I have installed K-3D. In the tutorial of K-3D when I am trying to see GTS Boolean (Advanced) tutorial then the following information is displayed :

"Unfortunately, it looks like you don't have the GTSBoolean plugin installed.  The tutorial can't continue without it."

Can anyone tell me how can I figure it out?

Thanks in advance.

---

### Post by wallgod on 2010-01-21
same here

---

### Post by noverb on 2010-04-19
**  I don't have a GTSBoolean plugin in my Create menu, what's the deal? **

 You will have to grab the optional gts library. In most cases once you have downloaded the library. You will install it without any extra ./configure options. In that case what you will be doing is this: 
 
[LIST=1]
[*] ./configure
[*] make
[*] make install or (checkinstall if you like to use it)
[/LIST]
 Please note, if you have installed K-3D already you will have to uninstall it first and recompile with: ./configure --with-gts. You may run ./configure --help and add or exclude more things.

---

### Post by alfu on 2010-09-16
Okaaaay.  Thanks for copying that from [[COLOR="Blue"]http://www.k-3d.org/wiki/Frequently_Asked_Questions[/COLOR]]("http://www.k-3d.org/wiki/Frequently_Asked_Questions")

So that leads to my next question.

On which planet orbiting Arcturus-3 do we find a terminal into which we can type this gibberish?

---

