---
title: "Ubuntu default theme bug"
date: 2010-10-21
forum: New to Ubuntu
---

### Post by Andy06 on 2010-10-21
With the default theme cousins (Ambiance and Radiance), the moment you increase the height of the panels (to say....30), it gets these ugly bars because apparently the background doesn't scale.

What can I do about this? I can't believe they shipped it like this

---

### Post by leclerc65 on 2010-10-21
* deleted *

Posted in the wrong thread, I am awfully sorry.

---

### Post by 101011010010 on 2010-10-21
Hello. I don't know if this is what you are looking for, but I edited the png  image to remove the gradient. I didn't like the line either, it looks ok  for my uses, but it might not for others.
  
 (Right click the image below and choose save image as, no need to rename).
   
 _N.B_: The image is very small, to save it the cursor has to be over the brown  section of the image. The easiest way to magnify it is "Control+ mouse wheel", once saved press "Control+0" to reset the zoom level.
  
 Navigate to (as root)
 > /usr/share/themes/Ambiance/gtk-2.0/apps/img/Make a copy of the original "panel.png" as a backup. Replace "panel.png" with the new image. Check the permissions (should be: root= read & write. root=read only. group=read only)

 Now log out and back in and hopefully the panel will look better.
  
 _N.B:_ Any update to Ambiance will reset this workaround.

---

### Post by Andy06 on 2010-10-23
Did the forum screw the formatting there?

---

### Post by Verbeck on 2010-10-23
> **Andy06 said:**
> Did the forum screw the formatting there?

> 
[IMG]file:///usr/share/themes/Ambiance/gtk-2.0/apps/img/panel.png[/IMG]

no. he pasted the local file link

---

