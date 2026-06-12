---
title: "Screen Resolution Stuck at 800x600"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by Ntacman on 2009-01-03
My Screen Resolution is stuck at 800x600, but the actual size is 1024x768. 800x600 is my largest option, and I searched for drivers online in the Hardware Drivers option in System-->Admin, but didnt find any at all.

---

### Post by BDNiner on 2009-01-03
try running from a terminal:
```

sudo dpkg-recofigure xserver-xorg

```

and following the prompts.

---

### Post by amauk on 2009-01-03
```
sudo dpkg-reconfigure xserver-xorg
```

fixed typo ;)

---

### Post by alienexplorers on 2009-01-03
What video card are you using (make & model)?

---

### Post by Ntacman on 2009-01-03
That only dealed with keyboards, nothing about screen resolution o.O

---

### Post by BDNiner on 2009-01-03
Good catch, I am sitting at work on a saturday and the whole office has christmas lights still up. I is very taxing on the eyes and my complaints have lead me to be called a scrouge.

---

### Post by Ntacman on 2009-01-03
> **alienexplorers said:**
> What video card are you using (make & model)?

01:00.0 VGA compatible controller: Trident Microsystems CyberBlade/XP (rev 63)

---

### Post by mapes12 on 2009-01-03
Right click Applications>Edit Menu. From the GUI select Other in L/H column then Screen and Graphics in R/H column. You may have to reboot but then go Applications>Other>Screen and Graphics. When the GUI opens then select your hardware from the tabs then set your screen res.

This worked for me in 8.04 with a similar problem. If you're running 8.10 you may be out of luck cos 8.10 has a new X server version that does not allow manual configuration.

---

### Post by DWBC on 2009-01-03
I am having the same problem on a PC clone with an Xpert 98 AGP 2X adapter. You might check out the Thread "Display adapter and screen resolution" currently running in this Forum to see if any of the suggestions posted there help with your issue. We're still looking for the answer on my machine.

---

### Post by DWBC on 2009-01-03
I'm am not getting the options outlined in the following instructions:

> **mapes12 said:**
> Right click Applications>Edit Menu. From the GUI select Other in L/H column then Screen and Graphics in R/H column. You may have to reboot but then go Applications>Other>Screen and Graphics. When the GUI opens then select your hardware from the tabs then set your screen res.


When I go follow to the point of selecting Screen and Graphics in the R/H column (by double clicking) it opens the Launcher which does not give me any hardware selection options or screen res.

---

### Post by stoogiebuncho on 2009-01-03
Following those instructions just adds the launcher to your Applications Menu.  After you have checked it, click "Close", and then look in your Applications menu for Other > Screens and Graphics

---

### Post by mapes12 on 2009-01-04
This only works in 8.04, as I posted before. If your not getting the hardware options you may not have the packages installed. You will need these 2 packages:

[http://packages.ubuntu.com/hardy/admin/displayconfig-gtk](http://packages.ubuntu.com/hardy/admin/displayconfig-gtk)

[http://packages.ubuntu.com/hardy/guidance-backends](http://packages.ubuntu.com/hardy/guidance-backends)

You may have to restart to make them effective.

---

