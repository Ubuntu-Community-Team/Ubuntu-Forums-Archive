---
title: "Firefox crashed"
date: 2009-10-09
forum: New to Ubuntu
---

### Post by AndyP79 on 2009-10-09
Hi All,
 I am using Karmic at the moment, and everything seems to be good except for one thing. After installing GlobalMenu, Firefox has decided to crash. When I try to open it, nothing happens. I uninstalled it in Synaptact, and then re-installed it, but still nothing. For the moment, I am using Chromeium, but would rather be using Firefox. I can open thunderbird, and everything else seems to open fine.
Thanks

***EDIT---- oKAY, THE EASIEST WAY TO DO THIS IS USE THAT FANCY NEW UBUNTU STORE, AND JUST INSTALL FIREFOX 3.0, NOT THEE COOL NEW VERSION, BUT YOU GET TO KEEP A NICE FIREFOX THAT WE ARE ALL USE TO***

---

### Post by kanikilu on 2009-10-09
Try running firefox from a terminal, and see if it displays any errors. Also, try running firefox in safe mode. ```
firefox -safe-mode
```

---

### Post by Bodsda on 2009-10-09
> **AndyP79 said:**
> Hi All,
 I am using Karmic at the moment, and everything seems to be good except for one thing. After installing GlobalMenu, Firefox has decided to crash. When I try to open it, nothing happens. I uninstalled it in Synaptact, and then re-installed it, but still nothing. For the moment, I am using Chromeium, but would rather be using Firefox. I can open thunderbird, and everything else seems to open fine.
Thanks

Can you open a terminal and the run the following command
```

firefox

```
And then paste the output it produces when it crashes. This will help us debug the problem for you.

Kind regards,
Bodsda

---

### Post by mharrison on 2009-10-09
> **AndyP79 said:**
> Hi All,
 I am using Karmic at the moment, and everything seems to be good except for one thing. After installing GlobalMenu, Firefox has decided to crash. When I try to open it, nothing happens. I uninstalled it in Synaptact, and then re-installed it, but still nothing. For the moment, I am using Chromeium, but would rather be using Firefox. I can open thunderbird, and everything else seems to open fine.
Thanks

Did you delete the .mozilla holder in your home directory?  If you installed an add-on and uninstall/reinstall Firefox, it will pick the add-on back up....at least from my experience.

---

### Post by AndyP79 on 2009-10-09
> **Bodsda said:**
> Can you open a terminal and the run the following command
```

firefox

```
And then paste the output it produces when it crashes. This will help us debug the problem for you.

Kind regards,
Bodsda

I got this
Segmentation fault (core dumped)

what's that mean?

---

### Post by AndyP79 on 2009-10-09
I got the same thing if I put the safe mode in the terminal

---

### Post by kanikilu on 2009-10-09
Try starting firefox in safe mode and disable all add-ons (first checkbox).

Alternatively, as previously suggested, if you delete (or move) your ~/.mozilla directory and restart firefox, it should reset everything. Just be aware that you'll lose all add-ons, customizations, toolbars, bookmarks, etc.

---

### Post by kanikilu on 2009-10-09
Err...nevermind, it looks like you are not alone in this:

[http://listento.jaketolbert.com/firefox/gnome-global-menu-causes-firefox-3-5-segmentation-fault/](http://listento.jaketolbert.com/firefox/gnome-global-menu-causes-firefox-3-5-segmentation-fault/)
[http://ubuntuforums.org/showthread.php?t=1201158](http://ubuntuforums.org/showthread.php?t=1201158)

---

### Post by lovinglinux on 2009-10-09
[Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567). It doesn't have an exact solution to your problem, but might help.

---

### Post by AndyP79 on 2009-10-09
Thanks ya'll, I guess this is something I will have to wait to get fixed with the final release of Karmic. Dang!
Thanks again

---

### Post by AndyP79 on 2009-10-09
just incase anyone wants to know, AWebBrowser does not work either, but Ephinay and Chromium both do work

---

