---
title: "Urgent - on a borrowed computer, dead in the water, not sure how long I have on this"
date: 2011-05-10
forum: New to Ubuntu
---

### Post by ClientAlive on 2011-05-10
I run ubuntu 10.04 LTS with gnome desktop and kairo dock.
 
New to Linux. Problem is probably (i hope) and easy fix.
 
Not long ago I was trying to clean up some of the things on cairo dock that I don't use often. In the middle section there is an applet to switch desktop views. I right clicked it and n that menu selected "detach from dock." I thought that this just meant to remove the icon from the dock.
 
Immediately the computer went down, restarted to the log in screen. Now, when I enter my password and press enter at the log in screen it begins to log in and gets to the point where it plays the log in sound then goes right back to the log in screen.
 
I can get to a virtual terminal window by pressing ctrl+alt+F1 but am not sure what to do to correct this.
 
I asssume, if what happened only involved that applet, that there is a way to just 'put it back' from the command line and be golden. If what happened resulted in something more severe (like the removal of gnome altogether) I'm not sure what it would take.
 
Is there anyone who can help me with this. I am typing this to you on a borrowed computer at a local business close to my home. I am not certain how long I will be able to use this machine.
 
Thanks you very much for your help.

---

### Post by JKyleOKC on 2011-05-10
When you do ctrl-alt-F1 do you get a "Login:" prompt? If you do, log in with your user name and password to get a terminal prompt. then type "startx" and hit Enter. That ought to get you to a normal GUI display, from which you can operate while trying to correct the problem.

---

### Post by ClientAlive on 2011-05-10
> **JKyleOKC said:**
> When you do ctrl-alt-F1 do you get a "Login:" prompt? If you do, log in with your user name and password to get a terminal prompt. then type "startx" and hit Enter. That ought to get you to a normal GUI display, from which you can operate while trying to correct the problem.
 
 
Thanks KyleOKC. I'm on it. Gotta boot up and then I'll try that.
 
Thanks man.

---

### Post by josephmills on 2011-05-10
press ctrl+alt+f1 then log in then do a ```
sudo apt-get remove cairo-dock-core && cairo-dock-plug-ins-data&&cairo-dock-data&&cairo-dock-plug-ins-integration&&cairo-dock-plug-ins  
``` then ```
sudo reboot 
```

---

### Post by ClientAlive on 2011-05-10
> **josephmills said:**
> press ctrl+alt+f1 then log in then do a ```
sudo apt-get remove cairo-dock-core && cairo-dock-plug-ins-data&&cairo-dock-data&&cairo-dock-plug-ins-integration&&cairo-dock-plug-ins  
``` then ```
sudo reboot 
```


Removes cairo dock from the system entirely. Worked like a charm. Thanks buddy. Now on to just reinstall cairo dock and I should be golden.

:popcorn:

---

