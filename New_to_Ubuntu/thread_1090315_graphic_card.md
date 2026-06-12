---
title: "graphic card"
date: 2009-03-08
forum: New to Ubuntu
---

### Post by mitja80 on 2009-03-08
Does anybody know if there is any suitablle drivers for my VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter?

And if 3d support is even posible? 
Im tottal beginer in ubuntu, i have ubuntu 8.1 installed.
It works fine, but when i trie to run google earth does not work some message appears abaout openGL.

Thank you for reply.

---

### Post by jerrrys on 2009-03-26
PCI/AGP/PCIE?? thats 3 different buss configurations....and not compatible as far as i know....

---

### Post by kansasnoob on 2009-03-26
Things you probably already know but:

```
glxinfo
``` 

lists details about OpenGL, the Xserver, and your graphics card


```
glxinfo | grep direct
``` 

tells you if you have direct 3d rendering


glxinfo | grep vendor 

just your graphics card vendor

lspci | grep VGA

will show specific graphics card model

---

### Post by kansasnoob on 2009-03-26
> **kansasnoob said:**
> Things you probably already know but:

```
glxinfo
``` 

lists details about OpenGL, the Xserver, and your graphics card


```
glxinfo | grep direct
``` 

tells you if you have direct 3d rendering


glxinfo | grep vendor 

just your graphics card vendor

lspci | grep VGA

will show specific graphics card model

Sorry made a mess of those last two commaands:

```
glxinfo | grep vendor 
```

just your graphics card vendor

```
lspci | grep VGA
```

will show specific graphics card model

---

### Post by jerrrys on 2009-03-26
thanks for the info, BUT...last time time i took an iq test, i was right up there with a rock...so i got to ask:

Does anybody know if there is any suitablle drivers for my VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter?

---

### Post by jerrrys on 2009-03-26
NO...NO....NO...
THATS WRONG....
i sent a to paragraph reply....going off line

---

### Post by jerrrys on 2009-03-27
good morning kansasnoob:

or at least it is morning here..first let me say something that i should of said in the beginning, im not running SAS ( have ATI), but usually pretty good at finding answers. back to your OP...drivers..

spent some time on google this morning and found this (my apoliges if you been here, done that) and there seems to be quite a bit of info on the subject. so here goes...

[http://www.google.com/search?q=](http://www.google.com/search?q=)[SiS]+661%2F741%2F760+drivers&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a

so if nothing else comes of this; a the least, your post is getting a bump during the busy time of day...cheers

[http://www.google.com/search?q=](http://www.google.com/search?q=)[SiS]+661%2F741%2F760+drivers+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a

[http://www.google.com/search?q=](http://www.google.com/search?q=)[SiS]+661%2F741%2F760&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a

---

### Post by jerrrys on 2009-03-27
ok, dont know whats going on, my links dont work....please to copy and paste. in the meantime i will see if i can relearn how to use a computer...

---

### Post by miegiel on 2009-03-29
Do the _[Debian GNU/Linux device driver check]("http://kmuto.jp/debian/hcl/")_ or look in their _[list of SiS]("http://kmuto.jp/debian/hcl/SiS")_

---

