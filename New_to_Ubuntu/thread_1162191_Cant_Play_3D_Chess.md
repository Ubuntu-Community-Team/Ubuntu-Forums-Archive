---
title: "Cant Play 3D Chess ?"
date: 2009-05-17
forum: New to Ubuntu
---

### Post by ravi_buz on 2009-05-17
I have installed all drives for my graphic card and able to use compiz in full,But when i try to play chess in 3D i get this error
"You are unable to play in 3D mode due to the following problems:
No Python OpenGL support
No Python GTKGLExt support

Please contact your system administrator to resolve these problems, until then you will be able to play chess in 2D mode"

What can i do to resolve this

---

### Post by jimmy the saint on 2009-05-17
Follow the directions in this thread:
[http://ubuntuforums.org/showthread.php?t=864509](http://ubuntuforums.org/showthread.php?t=864509)

---

### Post by ravi_buz on 2009-05-17
Tried tat and now i cant even start Chess game it just shuts down

---

### Post by zika on 2009-05-17
> **ravi_buz said:**
> Tried tat and now i cant even start Chess game it just shuts down
same here, I installed these two packages, and two more that were required, and changed it to display in 3d but now I get only a glimps of it before it go in oblivion.
I've tried deleting ~/.gconf/apps/glchess directory but it did not help ... :)
even reinstalling gnome-games did not help ...
...
solved: went into gconf-editor found chess and removed 3D ... :)

conclusion: my ATI HD 3650 can not play chess in 3D even though I have all other stuff installed ... ATI rules in ruining Ubuntu experience ... :)

---

### Post by jimmy the saint on 2009-05-17
Did you try a reboot after you installed it?  I have found that anything relating to video capabilities often works better after a post-install reboot.  Otherwise it sounds like a reportable bug.  If that is the case, go to launchpad and file a bug report against 3D-chess so that the developers can fix the issue.

---

### Post by ravi_buz on 2009-05-18
> **zika said:**
> same here, I installed these two packages, and two more that were required, and changed it to display in 3d but now I get only a glimps of it before it go in oblivion.
I've tried deleting ~/.gconf/apps/glchess directory but it did not help ... :)
even reinstalling gnome-games did not help ...
...
solved: went into gconf-editor found chess and removed 3D ... :)

conclusion: my ATI HD 3650 can not play chess in 3D even though I have all other stuff installed ... ATI rules in ruining Ubuntu experience ... :)

Thanks zika it worked for me too and i have a nvidia card , i thing its a bug

---

### Post by Martin Marshalek on 2009-07-14
Sorry for the bump, but has this been confirmed as a bug in Jaunty or is there a fix for the Chess app crashing in 3d view?

---

### Post by Martin Marshalek on 2009-07-14
Sorry now for the useless bump, turns out the solution is on page 2 of this thread: [http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=7310102#post7310102]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=7310102#post7310102")

---

