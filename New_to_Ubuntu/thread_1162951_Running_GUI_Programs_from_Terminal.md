---
title: "Running GUI Programs from Terminal?"
date: 2009-05-18
forum: New to Ubuntu
---

### Post by raziiq on 2009-05-18
Alright i have this confusion in my mind, whenever i try to run lets say firefox from terminal like this

**firefox **

In this case Terminal hangs or i should say, Terminal wont take any more commands. why??

However if i run this command in Terminal i can enter commands

**firefox &**

Which one is efficient?? And is it ok running Programs from Terminal??

---

### Post by skymera on 2009-05-18
It's fine running programs from the terminal.

It can help with debugging and solving problems :)

---

### Post by alexander.i on 2009-05-18
If you add & after command process backgrounded and your command line free for you. But if backgrounded process write something to stdout then you will see it in terminal. For example, try `ping ya.ru &` and then run mc

Another nice future that you can use it's command line in gnome - Alt+F2

---

### Post by pawnrocket on 2009-05-18
It is okay... I don't know the ins and outs of it. However I did once setup a server version with no gui that ran graphica programs from the command line. xorg is what the gui runs off of, so I used it to run programs. The info for that stuff is available on the web.

---

### Post by raziiq on 2009-05-18
> **alexander.i said:**
> If you add & after command process backgrounded and your command line free for you. But if backgrounded process write something to stdout then you will see it in terminal. For example, try `ping ya.ru &` and then run mc

Another nice future that you can use it's command line in gnome - Alt+F2

Means it will not slow down my pc, whatever method i use right??

Also what does that ALT+F2 means??

---

### Post by superprash2003 on 2009-05-18
its the run dialog box where you can type commands which runs certain services. for example : gnome-system-monitor gives CPU usage , processes etc

---

### Post by mrtomservo on 2009-05-18
> **raziiq said:**
> Means it will not slow down my pc, whatever method i use right??


Whether you use the & (run in background) or not, (run in foreground) it will have NO effect on the speed of your computer.  It's just whether you want it in the background or the foreground.

---

