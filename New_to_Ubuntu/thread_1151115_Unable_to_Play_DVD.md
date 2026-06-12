---
title: "Unable to Play DVD"
date: 2009-05-06
forum: New to Ubuntu
---

### Post by Herber on 2009-05-06
I have installed Jaunty and gone through the very helpful Audio and Video Guide to set up DVD playing.  Unfortunately whenever I try to play a DVD I get an error message suggesting I don't have permision to use the Drive.  I try to check the permisions on the drive but the tab for permisions is blank.  I have been able to play DVD'd on previous versions without problems.

---

### Post by khelben1979 on 2009-05-06
I think you will find the addgroup command useful.

```
man addgroup
```
for more information on how to use the command.

KDE User Manager allows you to add more groups to your user also. Gnome should also have a graphical application for this if you haven't KDE installed. Try adding these groups to your user in that system: **video** and **audio**.

If you feel uncertain about how this works, then go have a look at the [file systems permissions wiki document]("http://en.wikipedia.org/wiki/File_system_permissions").

---

### Post by Sealbhach on 2009-05-06
You could check System/Adminstration/Users and Groups

Make sure the box "Use CD ROM drives" is ticked.


.

---

### Post by Herber on 2009-05-07
Hey Thanks, I am watching a Video right now, Problem solved.

---

