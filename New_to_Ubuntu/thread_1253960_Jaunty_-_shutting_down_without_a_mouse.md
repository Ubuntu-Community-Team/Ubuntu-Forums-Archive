---
title: "Jaunty - shutting down without a mouse"
date: 2009-08-30
forum: New to Ubuntu
---

### Post by Orographic on 2009-08-30
Hi all,

Can't seem to find an easy way to graphically shutdown Jaunty if a mouse isn't working. I know you can go into terminal via ALT F1 and then do 'sudo shutdown -h now' but the option to shutdown in the menus is now gone.

Is there a way to find a graphical shutdown menu via ALT F1? Or is there a way to add a shutdown icon to a menu?

---

### Post by magicmax0 on 2009-08-30
CRT+ATL+Delete then Enter (or wait 60 secs for auto shut down). Its the GUI way to shutdown, but even if ur GUI is messed usually it still works you just dont see it properly. You can also do a Down Arrow before you press enter to select restart.

Edit: You can also restart at the command line using "sudo reboot"

---

### Post by earthpigg on 2009-08-30
alt+f2
> 
sudo shutdown now

is the only thing that pops into my head.

---

### Post by belgianmadcow on 2009-08-30
Just to add a bit to earthpigg's reply - **CTRL**-ALT-F2 gives you a console in any case.
Then sudo reboot or -shutdown.
regards
bmc

---

### Post by CatKiller on 2009-08-30
> **Orographic said:**
> the option to shutdown in the menus is now gone.

Only if you've got the User Switcher applet on your panel. Otherwise, the same options as before are neatly in the menu.

To earthpigg: sudo won't work in the Run dialogue; there's nowhere to put your password in. ```
gksudo shutdown now
```should work from there, though.```
gnome-session-save --shutdown-dialog
``` would be my preferred method though. You can select between Shut Down, Restart and Hibernate with Tab and Space that way.

---

### Post by colau on 2009-08-30
+1

---

### Post by Orographic on 2009-08-31
Thanks guys, great stuff! Appreciate your help. Have tried a number of the methods mentioned above and all good.

---

### Post by The Cog on 2009-08-31
I often just poke the power button (which gives a popup of shutdown options, then press enter - shutdown is the default.

---

### Post by Orographic on 2009-09-01
Brilliant, tried that too and it works great. Thanks for the tip.

---

### Post by earthpigg on 2009-09-01
> **The Cog said:**
> I often just poke the power button (which gives a popup of shutdown options, then press enter - shutdown is the default.

nice! lol... the simplest solutions are often the best, well done sir.

---

