---
title: "Programs in Ubuntu written with Python"
date: 2009-10-25
forum: New to Ubuntu
---

### Post by davidstri on 2009-10-25
I'm sorry if someone's asked this question before, but I can't find it anywhere on google. Where can I find programs for Ubuntu written in Python? I'm learning Python by reading Learning Python by Mark Lutley, and I want to try reading some code, but I can't find out which programs are written in Python. I remember seeing a GUI in Ubuntu that said it was 100% Python(if that's possible), but I can't remember what it was called.
What are a couple programs in Ubuntu that have Python in them or are completely written in Python? Thanks.

---

### Post by twright on 2009-10-25
> **davidstri said:**
> I'm sorry if someone's asked this question before, but I can't find it anywhere on google. Where can I find programs for Ubuntu written in Python? I'm learning Python by reading Learning Python by Mark Lutley, and I want to try reading some code, but I can't find out which programs are written in Python. I remember seeing a GUI in Ubuntu that said it was 100% Python(if that's possible), but I can't remember what it was called.
What are a couple programs in Ubuntu that have Python in them or are completely written in Python? Thanks.
If you want to learn python, I recommend you either wait 4 days or Upgrade to Ubuntu Karmic now and check out Quickly which will walk you through the process including making your own GUI applications.

---

### Post by davidstri on 2009-10-25
Wait 4 days?

---

### Post by lswb on 2009-10-25
Try this in a terminal:

grep '#!/usr/bin/python' /usr/bin/*

You could try it on some of the other bin and sbin directories as well.

---

### Post by j7%&lt;RmUg on 2009-10-25
The application in my sig(which i wrote) is written entirely in python.

---

### Post by twright on 2009-10-26
> **davidstri said:**
> Wait 4 days?
Until the release of the next version of Ubuntu, 3 now

If you want you could try out the release candidate though - as I said it includes some great tools for learning python

---

### Post by delphiexile on 2009-10-26
There is many programs in the system written fully in python like Hardware Drivers (jockey-gtk) you find some code of this program here in  this folder 
/usr/share/jockey

you can also find code of other apps here /usr/share , but not always , there is places in the system that application use it to store py-scripts.

I advice you to download source code of an application written in python instead of seeking code inside your system.

For example you can download the Ubuntu Tweak [source code]("http://launchpad.net/ubuntu-tweak/0.4.x/0.4.9.1/+download/ubuntu-tweak-0.4.9.1.tar.gz") , its fully written in python.

---

### Post by Simian Man on 2009-10-26
Reading production source code is actually not a good way to learn a language at all.  It is without context and rarely, if ever, explains all of the assumptions made as to how the code will fit into a larger product.  It also offers no insights into why certain things are done the way they are.  Often times production code is admittedly bad in order to patch over bugs and so on.

That isn't to say that reading code is always bad because it's not.  It is an important way to hone your craft as a programmer, but should come after you are very comfortable with programming in general and can understand exactly what the code is doing and why.

---

### Post by oldfred on 2009-10-26
I also agree that most of the code in the major applications is not a good place to start. I tried looking at Gramps and there are so many modules that it is extremely difficult for a beginner to follow.

I tried to find a few smaller applications and reviewed them but tutorials and several books seem for me to work the best.

python
[http://www.python.org/dev/](http://www.python.org/dev/)

pyGTK applications:
[http://www.pygtk.org/applications.html](http://www.pygtk.org/applications.html)

---

