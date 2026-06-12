---
title: "urxvt and screen - problem"
date: 2010-03-27
forum: New to Ubuntu
---

### Post by tektonik on 2010-03-27
Hello!

Today I installed the gnu screen application. Everything is OK, but there is a small problem: there is grey bar (marked with red) under the "tabs". 

[http://noob.hu/2010/03/27/problem.png]("http://noob.hu/2010/03/27/problem.png")


I want to remove these bar. it is possible?

---

### Post by vedek on 2010-03-27
could be part of the program?

---

### Post by tektonik on 2010-03-27
not really.

here is a screenshot without bar (same terminal emulator and screen)

[http://bl1nk.core.ws/s/2010-03-24-101437_1366x768_scrot.png]("http://bl1nk.core.ws/s/2010-03-24-101437_1366x768_scrot.png")

---

### Post by tektonik on 2010-03-27
any ideas?

---

### Post by falconindy on 2010-03-27
You'll need to post your .Xdefaults.

---

### Post by nothingspecial on 2010-03-27
You are running byobu which is a pimped up version of screen.

Remove byobu and you will have plain old screen without the grey bar.

Alternitively you could use the grey bar, it`s kind of like a panel for your terminal.

Press F9 and choose "Toggle status notifications" and use the grey bar to display your fan speed, temp, network info etc

There`s a few other features they`ve added. My personal favourite is F2 to create a new session and F3 and F4 to toggle between them instead of all this Ctrl A business. (You still need to Ctrl A then K to kill a session)

---

