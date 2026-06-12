---
title: "Laptop mouse pad"
date: 2009-07-04
forum: New to Ubuntu
---

### Post by goldenfamily on 2009-07-04
Is there any way to disable the mouse pad when typing on the keyboard?  I sometimes hit the pad and off goes the cursor.  I looked it the mouse preferences and did not see anything that would help.  Not a major problem just a hiccup.  One thing that I did have a problem with in the hibernation with my Toshiba lap top.  It would go through the start up and then the screen would just show random pixels and freeze.  Shut the laptop off and started it back up and away it went.

forgot to add

HAPPY 4TH OF JULY

---

### Post by Celauran on 2009-07-04
First, you must edit your /etc/X11/xorg.conf file and add the following line in the touchpad section:

```
Option    "SHMConfig"    "on"
```

Then you can disable the touchpad while typing by running syndaemon

```
syndaemon -d
```

Your best bet would be to add syndaemon to sessions so it runs on boot.

---

### Post by shifty_powers on 2009-07-04
[https://help.ubuntu.com/community/SynapticsTouchpad#Disabling%20the%20Touchpad%20Temporarily%20While%20Typing](https://help.ubuntu.com/community/SynapticsTouchpad#Disabling%20the%20Touchpad%20Temporarily%20While%20Typing)

---

### Post by goldenfamily on 2009-07-04
that was quick and solved the problem..    Thanks every one!!!

---

### Post by Penguin Guy on 2009-07-04
> **goldenfamily said:**
> One thing that I did have a problem with in the hibernation with my Toshiba lap top.  It would go through the start up and then the screen would just show random pixels and freeze.  Shut the laptop off and started it back up and away it went.

This is a very common Linux issue; it happens with almost all computers running Linux and I don't think there is any way to fix it - certainly not easily.

---

