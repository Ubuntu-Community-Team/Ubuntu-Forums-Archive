---
title: "Kill process"
date: 2009-11-04
forum: New to Ubuntu
---

### Post by kakashi_12 on 2009-11-04
Is there a keyboard shortcut to do it? Not through the terminal. Ctrl+PrintScreen+K or whatever it is, does not work. Someone suggested that to me earlier.

---

### Post by which ones pink on 2009-11-04
You can go into a terminal and type "killall (program)", or hit alt+F4 if it's an application.

Edit: just saw you said not through terminal lol.  Why not?

---

### Post by braete on 2009-11-04
there is a force quit button you can add to any of the panels.
then to kill a process you click it then click to window of the app you want to kill.

---

### Post by nhasian on 2009-11-04
a hotkey to close the application in the foreground is Alt-F4.  However if an application has crashed, you can press Alt-F2 then type xkill.  then click on the application thats crashed it will kill it.

you can also use from a terminal:

kill
xkill
killall
top (press k to kill a process)

---

### Post by NickJones on 2009-11-04
If you wish to kill a program that is not closing, right click on a blank section of the taskbar, click "Add To Pannel" then type "force quit" into the search box. Now when a program is misbehaving, click on the force quit icon then the window you want to close.

---

### Post by kakashi_12 on 2009-11-04
> **which ones pink said:**
> You can go into a terminal and type "killall (program)", or hit alt+F4 if it's an application.
 
Edit: just saw you said not through terminal lol. Why not?
 
because if the OS is hanging, you may not be able to open the terminal.

---

### Post by fela on 2009-11-04
Always remember the -9 option aswell. If an application is truly hanging it won't respond to a normal killall, pkill, or kill. The -9 option will try to force it to kill, well it should kill it as long as the program you use to kill (such as killall) gets enough CPU cycles to run. Exceptions to this are when things like

```
:(){ :|:& };: # fork bomb, DO NOT RUN
fork while fork # I think ruby, again DO NOT RUN
```

get run without protection in /etc/security/limits.conf. When this happens, and there is no protection, you will often have to resort to the reset button, or the dank corner where your server is, to reset it. This is why setting stuff in limits.conf and keeping an eye on runaway (zombie/defunct) processes is so important, and number 1 [SIZE="6"]REMEMBERING THE -9 OPTION![/SIZE].

---

### Post by fela on 2009-11-04
> **kakashi_12 said:**
> because if the OS is hanging, you may not be able to open the terminal.

If you can't access a tty then you want the reset button or the power plug at very worst, and hope you remembered to disable delayed write back or whatever it's called. Lost data == bad.

If you knew that if your computer was badly hanging that you couldn't open a tty, why did you think you'd be able to do anything else?

---

### Post by kakashi_12 on 2009-11-04
cause i should be able to kill all and start fresh.

---

### Post by Crunchy the Headcrab on 2009-11-04
> **nhasian said:**
> a hotkey to close the application in the foreground is Alt-F4.  However if an application has crashed, you can press Alt-F2 then type xkill.  then click on the application thats crashed it will kill it.

you can also use from a terminal:

kill
xkill
killall
top (press k to kill a process)
I think you can use all those from Alt-F2.  I know for sure you can use kill.

---

### Post by kakashi_12 on 2009-11-26
I FINALLY figured it out! While trying to fix another problem, I ended up fixing this one. Ctrl + Alt + Backspace. It logs you out!

---

