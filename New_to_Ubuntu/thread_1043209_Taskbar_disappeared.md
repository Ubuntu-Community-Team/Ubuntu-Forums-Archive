---
title: "Taskbar disappeared?"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by gatorman1122 on 2009-01-18
Hi everyone,

Newbie here...I tried to extend my desktop onto my tv via S-video. I tried it and the resolution was absolutely horrible. I then tried to switch back to my single display. 

Afterwards, I can't seem to locate my taskbar. When I hit Ctrl+Alt+ left/right arrow to switch between workspaces, I can see the taskbar flash for a split second. 

So how do I get my taskbar back?

Thanks in advance.

---

### Post by reahjw6 on 2009-01-18
If you have complletly lost the taskbar.
 Try ALT + F2 and typing 'gnome-panel'
 If not right-click the panel and select New Panel. Put your new panel in position,then right-click and select Add to Panel. You want the Window List applet for the taskbar.

---

### Post by babloo75 on 2009-01-18
[http://ubuntuforums.org/showthread.php?t=1041893&highlight=panel](http://ubuntuforums.org/showthread.php?t=1041893&highlight=panel)

this should help

---

### Post by Michael.Godawski on 2009-01-18
hi,

or try this:

If you login into your Ubuntu desktop and your panels are gone try this to bring them back:
 
[LIST]
[*]Press Alt+F2, you will get "Run" dialog box.
[*]Type "gnome-terminal"
[*]In terminal window, run "killall gnome-panel"
[*]Wait for a moment, you should get gnome panels.
[/LIST]
 If alt+f2 does not work change with ctrl+alt+f1 into the command line gui. You will have to type in your login name and the login password. The password will not be displayd as you type it.
 Now you can run ```
killall gnome-panel
```.
 To leave the command line interface type exit and hit enter.

---

### Post by gatorman1122 on 2009-01-18
Hi,

Thanks for the replies, everyone. Unfortunately, neither of the solutions have solved my issue. 

Is it possible that the screen resolution is causing the taskbar to be hidden?

I'm starting to understand why a small percentage of people use Linux lol...getting frustrated but trying to be patient. 

Also, is there a shortcut for launching a terminal window in Ubuntu (instead of the virtual terminal)? I remember that CentOS allows you to launch a terminal simply by right-clicking and selecting that option.

---

### Post by gatorman1122 on 2009-01-18
anyone?

---

