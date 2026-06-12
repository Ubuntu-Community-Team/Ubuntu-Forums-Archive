---
title: "How to change the order of tasks in a right click in Desktop?"
date: 2009-06-20
forum: New to Ubuntu
---

### Post by kapmsd on 2009-06-20
Hi guys.
I really find difficult with a frequent right-click in Desktop (habit got from using XP ;)) always leading to creation of new folder.
I would like to know how to change the order so that i can place "clean up by name" at the top.
Which file is responsible for the specified event of right -click?
Thanks in advance for your inputs.

---

### Post by elianthony on 2009-06-23
Hi,

I haven't done exactly what you're wanting to do, but I have modified the context menu for the desktop. I've edited a file that allowed me to change *some* of the context menu, it might help you. You'll need to open a terminal from the Accessories menu, and enter this:

```
sudo gedit /usr/share/nautilus/ui/nautilus-desktop-icon-view-ui.xml
```

What I have done is to remove the *Change Background* & *Create New Launcher* options from the public machines here at the library where I work. You do this by changing the line...

<menuitem name="Change Background" action="Change Background"/>

to...

<menuitem name="Change Background" action="Change Background" hidden="true"/>

I have added ***hidden="true"*** to the end of that line. This removes the Change Background option from the menu. You could do the same with the Create New Launcher option, by editing it's line in the same file. Hope this helps, or at least gets you going in the right direction.

This is better than deleting that line, since all you have to do to undo your changes is remove the ***hidden="true"***, instead of retyping that whole line.

---

### Post by kapmsd on 2009-06-23
Hi!
Happy that you provided a good input.
But it doesnot seem to have that "clean up by name option" (in particular).
Also i wld like to know how you got info reg the file name responsible for the event i asked?( Am a beginner :D)

---

