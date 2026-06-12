---
title: "A little help with c++"
date: 2009-07-31
forum: New to Ubuntu
---

### Post by DiegoTc on 2009-07-31
Well I am having a little trouble.
I am using code blocks for programming in c++.
But at college I am working with a partner and she uses windows. But there is more. We have to work with the conio library which is only available for windows. i was planning to use the ncurses library which is almost the same but my partner can not used this library.

So I was thinking on using a virtual box for this little problem. Work with a virtual and use the conio library without any problems. But i am not sure if this is going to work. 

Can some one tell me if there is another solution, or if the virtual box isn't going to work¿?

---

### Post by Liolikas on 2009-07-31
Your colleague will have to use gcc on [http://www.cygwin.com/](http://www.cygwin.com/) - most simple way. or install Linux on virtualbox or on real box.

---

### Post by Durden on 2009-07-31
You cna use virtualbox just fine. You take a performance hit but nothing you're doing in class will tax the system too hard. Your partner can alternatively install Ubuntu via Wubi but if he/she isn't used to Linux then it would probably be easier for you to just do the Windows in Virtualbox thing.

---

### Post by Cypher on 2009-07-31
If the conio library is provided by your class/teacher, I imagine they want you to use it as opposed to ncurses or any other alternative. So you installing Windows in VirtualBox seems like the best course of action..

---

