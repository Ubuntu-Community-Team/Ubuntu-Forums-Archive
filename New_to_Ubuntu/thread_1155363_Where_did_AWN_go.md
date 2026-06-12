---
title: "Where did AWN go???"
date: 2009-05-10
forum: New to Ubuntu
---

### Post by taminrob on 2009-05-10
Can someone possibly help me out here...I had AWN installed and running, I had just finished doing the whole mac4lin thing and it was working great UNTIL...I restarted my computer.  I cant see the dock.  From System/Preferences/AWN Manager, I can open the manager and see all of the settings that I enabled, and all applets and launchers are where they are supposed to be...but no dock on my desktop.  When I try to run it from Application/Accessories nothing happens.  When I run from terminal it returns

---     rob@rob-laptop:~$ avant-window-navigator

          (awn-applets-migration:21502): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `AwnConfigClient'
           Warning: Screen isn't composited. Please run compiz (-fusion) or another compositing manager.   ----

and opens a pop-up that says its starting AWN but lists the warning about screen not being composited, but still no dock.

Compiz is set to custom and ultimate.

I have searched the forums and have not seen this issue or a solution for other issues that I can get to work.  I have restarted multiple times with no luck.  Have had AWN up and running on this computer before with 8.10 and 9.04, but after running 9.04 and being fed up with freezing and no graphic card support I did a fresh install of 8.10 again...

Thats all the information that I have that I think may be of use...need anything else, just ask and I will supply.

---

### Post by spiderbatdad on 2009-05-10
After installing 8.10 did you apt-get compizconfig-settings-manager?

---

### Post by shadow120 on 2009-05-10
applications -> accessories -> avant window navigator
then add it system -> prefrences -> sessions -> startup programs
this should fix it

---

### Post by Bölvaður on 2009-05-10
There is no use restarting your computer over and over again..... it's not going to change by turning it on and off.... similar to my tv, which never works, no matter how often I turn it on or off.


SOLUTION:

The problem is that compiz isnt running, so make sure that it is. In the standard setting dragging any window off the screen to the right will make it appear on the next workspace on the right. But if compiz is not on, you will not be able to drag it onto the next workspace and be stuck with it on the screen there.

Under System &#8594; Preferences &#8594; Appearance, you should pick normal desktop effects to begin with and then later [click this link]("apt:compizconfig-settings-manager") to install a configuration tool for compiz to make all kinds of fancy stuff, but lets stay with the defaults at the moment.

Make sure compiz is running.
Open the terminal (or press Alt+F2) and type:
```
avant-window-navigator
```

Is it up?
Good.
Then make it run at startup by following the instructions of the guy above me.

Now you probably want to install the compiz config settings manager and set up things like scale to top the mac feeling of your desktop.

---

### Post by raymondh on 2009-05-10
> **shadow120 said:**
> add it system -> prefrences -> sessions -> startup programs


+1

---

### Post by taminrob on 2009-05-10
Well, thanks for the responses...already had compizconfig setting manager installed, but I started compiz in terminal and it seemed to fix it...never thought I had to do that as my cube and other effects worked properly...but that fixed it, thanks!

---

