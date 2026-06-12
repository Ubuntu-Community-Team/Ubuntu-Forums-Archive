---
title: "How To Install This Screenlet"
date: 2010-11-04
forum: New to Ubuntu
---

### Post by onaridge on 2010-11-04
I've installed screenlets that are already in the screenlet program but I found a clock I like better and so I downloaded it. It's a tar archive that I extracted and directed the screenlet manager to install it. Nothing happens. Not sure what I am doing wrong

---

### Post by Enigmapond on 2010-11-04
In your home directory there will be a hidden folder called .screenlets. Just extract the folder from the archive and put the whole folder in the .screenlets folder.

---

### Post by onaridge on 2010-11-04
OK it says it is installed but I can't find it in the screenlet manager

---

### Post by Enigmapond on 2010-11-04
You should see it right away...you may have to restart the manager. Where did you get the clock? Can you post the link?

---

### Post by onaridge on 2010-11-04
I did restart it thinking that would do it. Link: [http://gnome-look.org/content/show.php/Azenis+Clock?content=108545](http://gnome-look.org/content/show.php/Azenis+Clock?content=108545)

---

### Post by Enigmapond on 2010-11-04
Ok...I figured it out, This is not in itself a screenlet but a theme for the existing clock. You need to put the folder in your file system under /user/share/screenlets/clock/themes. You will need to do this with root privileges. Then just launch the clock and change the theme..:) Whew..LOL

---

### Post by onaridge on 2010-11-04
I don't have a clock folder in user/share! ?

---

### Post by Enigmapond on 2010-11-04
Sorry that was my late edit of my last...user/share/screenlets/clock/themes....:)

---

### Post by Enigmapond on 2010-11-05
in other words... copy the folder then do:

```
gksu nautilus
```

navigate to that folder and paste it. Launch the clock and then right click on it and go to "themes" and you will see Azenis....:)

---

### Post by onaridge on 2010-11-05
Ah, ok now how do i get root privileges to drop that folder in there.

---

### Post by onaridge on 2010-11-05
Ha! I wrote my question when you typed yours!

---

### Post by onaridge on 2010-11-05
ok it's done! Thank you and I learned a few things along the way.

---

### Post by Enigmapond on 2010-11-05
No problem. You need to mark this thread as solved in the thread tools just in case others have the same problem.

Cheers!

---

