---
title: "question about workspaces (virtual desktops)"
date: 2009-05-20
forum: New to Ubuntu
---

### Post by RobertL on 2009-05-20
I'm pretty new to Ubuntu. When I installed it I was really happy to see it supports multiple desktops and I envisioned using them right away. But once I learned how they work they seem pretty useless because all icons appear on all desktops. Am I missing something? I expected to be able to set up one desktop for office applications, with icons for my current writing projects, one for financial business, another for gaming with links to various game-related programs, documents, URLs, etc. and a third for programming with programming-related info. But I can't figure out how to put an icon on only one desktop.

If the only difference between desktops is where an open application window appears they are missing their potential usefulness.

---

### Post by Mornedhel on 2009-05-20
No, you're right. Workspaces are for windows only. What's visible on the desktop is only what's contained in the /home/yourusername/Desktop folder.

As for "one desktop for office applications, with icons for my current writing projects, one for financial business, another for gaming with links to various game-related programs, documents, URLs, etc. and a third for programming with programming-related info", why can't you just use simple folders ? If you want to separate by context, you can always use the workspace to organize your currently running applications.

You should store your personal files (really, everything that's not installed system-wide for every user) in your home directory, in /home/yourusername.

---

### Post by jbruced on 2009-05-20
I agree it would be neat, but it would be at a cost in system resources.

You would have resources tracking launchers and stuff on different virtual desktops for no reason other than when one switches to it.

There are programs available that will allow different wallpapers, but it ends up being more code running on your computer all the time, and eating some resources.

---

### Post by RobertL on 2009-05-20
Ok thanks for the replies. I'll stop hoping it works that way.  

In the "olden days' I had an SCO unix system that was set up with 8 totally independent desktops (control-F1 to control-F8). I loved the convenience of that arrangement and always remembered it and wanted to get back to it. The system resources would be about like having 8 users logged in simultaneously, each running a graphical interface. That doesn't sound excessive particularly since there's not likely to be much system load created by more than one desktop at the same time.

---

### Post by lovinglinux on 2009-05-20
I have a solution for you.

First you could use the "Wallpaper" plugin of Compiz. You can have different wallpapers for each workspace. This will draw the wallpaper above the regular desktop, which is drawn by Nautilus, so your Desktop folders and icons won't show.

Then you could use the "Place Windows" plugin to specify which programs would be opened on each virtual desktop.

Then you could use multiple instances of screenlets. Unless you tick "stick to desktop" option, the screenlets will start in the virtual desktop you place them. There are screenlets for launching programs, screenlets for accessing files and folders and much more. I'm sure this would let you create different virtual desktops for different objectives, each one with it's own set of tools, links, windows and wallpaper.

You can do that if you have enough juice on your machine.

---

### Post by RobertL on 2009-05-21
Thanks lovinglinux. I'll give that a try, although it's a little more contrived than I would like.

---

