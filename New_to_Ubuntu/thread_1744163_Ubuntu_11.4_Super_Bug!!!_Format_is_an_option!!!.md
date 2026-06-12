---
title: "Ubuntu 11.4 Super Bug!!! Format is an option!!!"
date: 2011-04-30
forum: New to Ubuntu
---

### Post by lordddelgado on 2011-04-30
Activating Desktop Cube in compiz while in Ubuntu Classic will make your minimize, maximize/restore, and close button dissappear, you may fix it by typing in terminal: metacity --replace temporarily, then go to compiz and reset it by default, next when you activate compiz in Ubuntu 11.0 you will loss all items in your desktop, the menu tab the panel, unity tab...ALL, all is lost!... all you can do is to go to classic settings and ask for help!!!....HELP I NEED HELP :(:(:(

or I'll just format my hard drive and go back to windows for the meantime.

---

### Post by sikander3786 on 2011-04-30
Press Ctrl + Alt + F1 at the Unity (messed up) desktop. You might see the tty1. Login using your credentials and try this command.

```
unity --reset
```

Or this might help.

[http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html](http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html)

---

### Post by abnordude on 2011-04-30
> **sikander3786 said:**
> Press Ctrl + Alt + F1 at the Unity (messed up) desktop. You might see the tty1. Login using your credentials and try this command.

```
unity --reset
```Or this might help.

[http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html](http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html)


Do as told.

Just one more advice.

Ubuntu unity and desktop cube desktop rotate don't go well together.
So tis better not to activate them.

---

### Post by lordddelgado on 2011-04-30
> **abnordude said:**
> Do as told.

Just one more advice.

Ubuntu unity and desktop cube desktop rotate don't go well together.
So tis better not to activate them.


It's too late I already activated it... now it's all messed up.
my desktop is empty, all you can see is just the wallpaper. :(

---

### Post by lordddelgado on 2011-04-30
> **sikander3786 said:**
> Press Ctrl + Alt + F1 at the Unity (messed up) desktop. You might see the tty1. Login using your credentials and try this command.

```
unity --reset
```Or this might help.

[http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html](http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html)


yes it show progress by typing the commands... but :( it did'nt work,
after rebooting my linux box it goes back to that only wallpaper state.

---

### Post by abnordude on 2011-04-30
Well.
Try this link.


[http://ubuntuforums.org/showthread.php?p=10733905](http://ubuntuforums.org/showthread.php?p=10733905)

---

### Post by lordddelgado on 2011-04-30
I noticed something i run ubuntu in a very low resolution, it worked the desktops item are back, I check the compiz setting, and in the prefernces > profile unity is missing > i reinstall unity by using the terminal and reset it again, and it says:
unity-panel-service: no process found
libcompizconfig: dlopen: /usr/lib/compizconfig/backends/libgconf.so: cannot open shared object file: No such file or directory

Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : ini
Integration : true
Profile     : default
Adding plugins
Initializing core options...done
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
Xlib:  extension "GLX" missing on display ":1.0".
Xlib:  extension "GLX" missing on display ":1.0".
Xlib:  extension "GLX" missing on display ":1.0".
Compiz (opengl) - Fatal: glXCreateContext failed
Compiz (bailer) - Info: Ensuring a shell for your session
lordddelgado@OSLINUX:~$ Cannot register the panel shell: there is already one running.

HELP...

---

### Post by lordddelgado on 2011-04-30
... after reinstalling my nvdia drivers the minimize, maximize/restore, and close button is back!!!, but my upper lower and unity panel is still missing, 

I'm getting near to success!!!

MOAR HELP PLS!

---

### Post by lordddelgado on 2011-04-30
OK I'm done, It's better to re-format and re-install ubuntu on my system, It's taking a lot of time troubleshooting... I'll go back to Windows for the meantime so I can go back with my work.

Ubuntu 11.4 Perfect? NOT, I like the earlier versions... :(

---

