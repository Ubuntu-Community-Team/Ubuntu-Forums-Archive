---
title: "compiz ati issue"
date: 2010-05-03
forum: New to Ubuntu
---

### Post by ~sHyLoCk~ on 2010-05-03
Hi,
 Using Ubuntu 10.04 in Dell Inspiron 1564 with HD4330 card. I am using the radeon driver as I experience video-tearing with the fglrx driver. Compiz and the effects like burn,magic lamp,etc. all work fine. However I can't use the cube since I can't increase the virtual desktop size from 1! I can change the horizontal and vertical desktops though. Any clue?

---

### Post by warfacegod on 2010-05-03
If you have a Workspace Switcher on your panel, right click it and select Preferences.

Set the number of columns to something higher than 1.

If your don't have it on your panel, you can add one by right clicking a panel and selecting Add to Panel.

---

### Post by ~sHyLoCk~ on 2010-05-03
> **warfacegod said:**
> If you have a Workspace Switcher on your panel, right click it and select Preferences.

Set the number of columns to something higher than 1.

If your don't have it on your panel, you can add one by right clicking a panel and selecting Add to Panel.

yeah I have set that to colums=4 and rows=1 but still can't change virtual desktops in ccsm. :(

---

### Post by warfacegod on 2010-05-03
I assume you have Advanced or Custom graphics turned on.

Is it just that the Ctrl+Alt+Arrow Left/Right isn't working?

Which plug-in is "Virtual Desktops" under?

---

### Post by ~sHyLoCk~ on 2010-05-03
> **warfacegod said:**
> I assume you have Advanced or Custom graphics turned on.

Is it just that the Ctrl+Alt+Arrow Left/Right isn't working?

Which plug-in is "Virtual Desktops" under?

General Options -> Desktop size

Ctrl+Alt+Left just flips the desktop to the next, the cube doesn't show up since desktop size is fixed at 1 !:confused:

---

### Post by warfacegod on 2010-05-03
Rotate Cube under Desktop enabled?

---

### Post by ~sHyLoCk~ on 2010-05-03
> **warfacegod said:**
> Rotate Cube under Desktop enabled?

yep...u dont understand I can't increase the  no. of virtual desktops more than 1.:o

---

### Post by ~sHyLoCk~ on 2010-05-04
somw help? :(

---

### Post by warfacegod on 2010-05-04
No, I do get it. I'm just trying to come up with a fix that doesn't involve purging and reinstalling CCSM.

At this point, I'm baffled. Workspace Switcher and Desktop Size in CCSM are the same thing. When I change Horizontal Virtual Size, Columns in Workspace Switcher changes automatically and vice versa.

Try simple-ccsm from Synaptic. It also has a way to change the number of Desktops.

---

