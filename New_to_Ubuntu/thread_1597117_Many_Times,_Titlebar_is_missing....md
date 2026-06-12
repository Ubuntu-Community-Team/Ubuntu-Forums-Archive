---
title: "Many Times, Titlebar is missing..."
date: 2010-10-14
forum: New to Ubuntu
---

### Post by Rushyang on 2010-10-14
Hey guys,

I am on ubuntu 10.10 (aka Maverick Meerkat) . My problem is many times when I log in into ubuntu.. My window's Titlebar is missing.. it won't come even if I change themes or anything else. If I'm going for restart, it will come back... It happens too often and I hate this.. Please advice.

---

### Post by Ctrl-Alt-F1 on 2010-10-14
Have you toyed around with Emerald for windows decoration?  It sounds like a problem with that.

What happens if you hit Alt-F2 and when the dialog pops up you type --metacity replace (enter)?

---

### Post by BlazeFire247 on 2010-10-14
Try pressing Alt+F2 then put in *gtk-window-decorator --replace*

---

### Post by Rushyang on 2010-10-14
> **Ctrl-Alt-F1 said:**
> Have you toyed around with Emerald for windows decoration?  It sounds like a problem with that.

What happens if you hit Alt-F2 and when the dialog pops up you type --metacity replace (enter)?

Yes sir, I have installed "Compiz". & I would like to keep it if it's possible...
In another settings of compiz, "Select Window Decorator" is set to "GTK Window Decorator" (by default)..

---

### Post by Rushyang on 2010-10-14
> **BlazeFire247 said:**
> Try pressing Alt+F2 then put in *gtk-window-decorator --replace*

BlazeFire,
Thank you for that tip.. By typing that, My titlebar came back instantly.. But does that mean that i will have to type that whenever this happens?

---

### Post by Ctrl-Alt-F1 on 2010-10-15
> **Rushyang said:**
> Yes sir, I have installed "Compiz". & I would like to keep it if it's possible...
In another settings of compiz, "Select Window Decorator" is set to "GTK Window Decorator" (by default)..

For emerald:
> To install them, go to: System > Preferences > Emerald Theme Manager and click the "Import" button and select the themes you want. To make your windows use Emerald, go to System > Preferences > CompizConfig Settings Manager and enable "Window Decoration", then click it and under "Command", enter:
emerald --replace
Then to run it for the first time, press Alt + F2 and type:
emerald --replace

For GTK:
CompizConfig Settings Manager and enable "Window Decoration", then click it and under "Command", enter:
/usr/bin/compiz-decorator

[http://www.webupd8.org/2009/03/ubuntu-install-themes-emerald-compiz.html](http://www.webupd8.org/2009/03/ubuntu-install-themes-emerald-compiz.html)

---

### Post by BlazeFire247 on 2010-10-15
> **Rushyang said:**
> BlazeFire,
Thank you for that tip.. By typing that, My titlebar came back instantly.. But does that mean that i will have to type that whenever this happens?

Try going to System -> Preferences -> Startup Applications then click on "Add". Type it in the command and name it whatever you want.

---

### Post by Ronok on 2010-10-24
**Thanks**, 
This also fixed my situation instantly 

> 
**BlazeFire247:** 	
" Try pressing Alt+F2 then put in gtk-window-decorator --replace "

[Ronok]("http://www.gongkuo.com/linuxcli.htm")

---

### Post by fermulator on 2011-01-08
any other suggestions?

I've tried all of the above and nothing restores the window decorations while running compiz.

Also a post exits: [http://www.uluga.ubuntuforums.org/showthread.php?p=9971593](http://www.uluga.ubuntuforums.org/showthread.php?p=9971593)

---

