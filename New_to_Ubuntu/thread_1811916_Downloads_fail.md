---
title: "Downloads fail"
date: 2011-07-25
forum: New to Ubuntu
---

### Post by baliol on 2011-07-25
Downloaded Epiphany from software centre but not found under apps/internet.  Tried Reconq and also failed.  Running 10.10 and no previous problem. Anyone help?

---

### Post by frankbooth on 2011-07-25
See if you can start Epiphany by pressing *ALT+F2* and typing *Epiphany*.

If so, then all you need to do is create a menu entry:

[LIST]
[*]Right click your applications menu and hit &#8220;Edit Menus&#8221;.
[/LIST]
The menu editor will appear, browse to the desired category (Internet)
[LIST]
[*]Add a new entry by pressing "New item".
[/LIST]
A new dialog will appear, fill it in like following:
```

Type: Application
Name: Epiphany
Command: epiphany
Comment: <insert comment>

```

Unless you can find a suitable icon in */usr/share/pixmaps/* or */usr/share/icons/* you can probably find one over at [gnome-look.org]("http://gnome-look.org/").

---

### Post by baliol on 2011-07-25
Alt+F2+Epiphany failed to find Epiphany.  Same with Reconq.

---

### Post by westie457 on 2011-07-25
> **baliol said:**
> Alt+F2+Epiphany failed to find Epiphany.  Same with Reconq.

Try running these commands in a terminal ```
sudo apt-get update
sudo apt-get install rekonq
sudo apt-get install epiphany-browser
```

Any errors can you copy and paste them in a new reply between ```
 
``` tags, Click the # at the top of the message window.

---

### Post by baliol on 2011-07-25
Thanks Westie.  That did the trick.
How do I show it Solved?

---

### Post by westie457 on 2011-07-25
> **baliol said:**
> Thanks Westie.  That did the trick.
How do I show it Solved?

Click on [COLOR="Red"]Thread-Tools[/COLOR] Upper-Right hand side of the page.
Glad it worked for you.

---

