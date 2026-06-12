---
title: "Lost both taskbars"
date: 2009-05-02
forum: New to Ubuntu
---

### Post by lsemmens on 2009-05-02
I've lost both the taskbar and the menubar in Jaunty, They are not "minimised" and I can find no way to get them back. A re-start did not fix the problem so I am down to being able to use only the apps that I have pinned to my desktop. This means that I cannot access Terminal or any other Utilities via the menu bar. I do have access to firefox and nautilus via the desktop.

The problem occurred after removing several apps that I decided that I would not use. (Don't ask me what as I cannot remember - I'm still getting my head around Linux having been a Windoze user for years)

---

### Post by Elfy on 2009-05-02
Try this Alt+F2
 put gnome-panel in the command box and run

---

### Post by mikewhatever on 2009-05-02
Please boot into recovery mode (second boot option), login and run the following command: **sudo apt-get install gnome-panel**. It should install back the panels.

---

### Post by lsemmens on 2009-05-02
Alt F2 did not work forest pixie. Thanks for trying

I booted to the recovery console, mikewhatever, and was presented with another menu, I selected an option to repair broken packages (or similar - can't recall) and now all is well, so, thank you!

---

