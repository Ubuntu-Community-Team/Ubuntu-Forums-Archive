---
title: "newbie q about make&amp;&amp;config"
date: 2009-11-18
forum: New to Ubuntu
---

### Post by steve_steve on 2009-11-18
Simple question:  when I make/config source code, do I need the original file anymore?  Or is it just like a Windoze installer that I can throw away?

thanks for your patient understanding.

---

### Post by whoop on 2009-11-18
if you compile a program, the compiled program itself will not require it's source code any more. a general rule.

---

### Post by Excedio on 2009-11-18
Is this what you're asking?
---------------------------------------
After I finish compiling the program (make & install) do I still need the original file that I downloaded?
---------------------------------------

In ALL of my experience thus far, the answer is no. I hope that I interpreted the question you asked correctly.

---

### Post by unamanic on 2009-11-18
I usually keep it around so that when I find or make a package for the application, I can do a make uninstall to remove the one I 'make install'ed.

---

### Post by MonoDeem on 2009-11-18
You don't need to keep it, tough, I prefer to do so. [COLOR=Blue]make install[/COLOR] can only be reversed by [COLOR=Blue]make uninstall[/COLOR], which obviously depends on whether it was implemented or not. If the compilation process went successfully and application works as expected, I always save it somewhere.

---

### Post by steve_steve on 2009-11-18
Thanks.  Yes, I was asking if I needed the source code for the program to run after I compiled it.  But I guess I should keep the source around in case I ever needed to reinstall or make uninstall.

Thanks again.

---

