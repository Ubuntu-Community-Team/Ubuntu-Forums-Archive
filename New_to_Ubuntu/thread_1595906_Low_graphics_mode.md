---
title: "Low graphics mode"
date: 2010-10-13
forum: New to Ubuntu
---

### Post by hyperhopper on 2010-10-13
Occasionally when starting my moms computer (10.04.1 LTS), it gives a SYSTEM IS RUNNING IN LOW GRAPHICS MODE error. there are a few options, such as view logs, restore driver data, and a few other things.

When i try to view logs, the prompt just flickers and acts like i never did anything. 

Same with restore driver data, and everything else except for

Run in low graphics mode just this one time (what she does to get it running)


and restart X, but when i do this, the screen freezes at something something cupsd

How can i fix this?

---

### Post by AndyM3 on 2010-10-13
Isn't Intrepid Ibex unsupported? You should probably do a backup and then a clean install of Lucid or Maverick.

---

### Post by Sealbhach on 2010-10-13
If you don't want to upgrade, I would suggest you reinstall the graphics driver. Find it in Synaptic, right-click and mark for Complete Removal, then reinstall it.

.

---

### Post by hyperhopper on 2010-10-13
> **AndyM3 said:**
> Isn't Intrepid Ibex unsupported? You should probably do a backup and then a clean install of Lucid or Maverick.

whoops, got my boxes mixed up, this one is the current LTS, 10.04.1



[SIZE="1"]one day ill get my dad to upgrade from II[/SIZE]

---

### Post by AndyM3 on 2010-10-13
As Sealbhach suggested, reinstall the driver, but using the command line (Ctrl+Alt+F2).

---

### Post by hyperhopper on 2010-10-13
there are about a million X dot org X server drivers, alot are for displays.....

---

### Post by hyperhopper on 2010-10-13
sudo apt-get remove xorg says that it cant get a lock becase another process is using it

---

### Post by AndyM3 on 2010-10-13
"sudo rm /var/lib/apt/lists/lock" should fix that.

---

### Post by hyperhopper on 2010-10-14
after sudo apt-get remove xorg and sudo apt-get install xorg nothing. still low graphics mode

---

### Post by Sealbhach on 2010-10-14
> **hyperhopper said:**
> after sudo apt-get remove xorg and sudo apt-get install xorg nothing. still low graphics mode

What driver is it? Maybe your graphics card is busted, try loading up a Live CD or USB session of Ubuntu 10.10, see how it looks.

.

---

### Post by hyperhopper on 2010-10-17
its an integrated. Ill try this, but its a recent install, and when i first loaded it up and installed via live CD, it looked fine and was normal.

ALSO, its not the graphics thats the problem, they look normal. its that darned message

---

