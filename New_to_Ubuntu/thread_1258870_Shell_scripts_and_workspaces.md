---
title: "Shell scripts and workspaces"
date: 2009-09-05
forum: New to Ubuntu
---

### Post by bzm3r on 2009-09-05
Hi,

I'm wondering if there is a way I can make my shell script execute in a particular workspace, regardless of which workspace it is executed in?

For example, if I execute the shell script in workspace 1, it still does whatever it has to in workspace 4.

Thanks

---

### Post by lovinglinux on 2009-09-05
I guess you are talking about the terminal graphical interface or the interface of applications launched by the script, because shell script actions do not relate to workspaces.

You can use the "Place Windows" plugin of Compiz. Open "CompizConfig Settings Manager", then click the "Place Windows" plugin, select the "Fixed Window Placement" tab and add your script window to the "Windows with fixed viewport" list.

---

### Post by schwascore on 2009-09-06
Looks like this is what you're looking for:

[http://ubuntuforums.org/showthread.php?t=312803](http://ubuntuforums.org/showthread.php?t=312803)

---

