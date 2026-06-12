---
title: "Deleted Top Panel HELP PLZ"
date: 2009-04-29
forum: New to Ubuntu
---

### Post by koldphlame on 2009-04-29
I was reading this while installing AWN dock and misunderstood what i was actually doing can someone please tell me how to get my top panel back:(

"First, delete the alternative (bottom) GNOME panel, if you have one. Now comes the tricky part, because the remaining panel can't be deleted. So, go to System -> Preferences -> Sessions and click the second tab, "Current Session". Click once on the gnome-panel entry in that list and then hit the 'Remove' button to delete the last remaining panel. Then, click on the "Session Options" tab and check the 'Automatically remember running applications when logging out' option and hit the 'Remember currently running applications' button. Close the Sessions window and reboot the computer."

---

### Post by Penguin Guy on 2009-04-29
Right-click on your remaining panel and select 'New Panel' - you will then have to add all the objects that you want to it manually.
Right-click -> Add to panel... Main Menu
Right-click -> Add to panel... Clock
etc.

---

### Post by CatKiller on 2009-04-29
If you don't have any panels, you can right-click on the desktop and create a launcher for **gnome-panel**. Then you'll be able to go back into Sessions to make it start up on log in again.

---

### Post by sundar_ima on 2009-04-29
you have not given info about other panel. anyway i consider you have the bottom panel. right click on it --> add panel. now you can see new panel. in the new panel again right click --> add to panel and search for packages which you had earlier.

---

### Post by nothingspecial on 2009-04-29
Interesting. I sometimes delete both my panels with a different method so I`m not sure what to do in your case.
I would try reversing what you did in the sessions window.

Ah but how do you get there without a menu?

Type ```
gnome-session-properties
```
That should bring the sessions box up.

---

### Post by koldphlame on 2009-04-29
i don't have any panels at all :(

---

### Post by Penguin Guy on 2009-04-30
> **koldphlame said:**
> i don't have any panels at all :(
Run either [COLOR="Green"]gnome-panel[/COLOR] - which should bring the panels up
or [COLOR="Green"]sudo debconf gnome-panel[/COLOR] - which should reset panel defaults.
You may then need to restart ([COLOR="Green"]shutdown -r now[/COLOR]).

To run commands press Alt + F2 (for a single command) or Ctrl + Alt + F1 (for a proper terminal).
* If you chose the proper terminal (Ctrl + Alt + F1) then use [COLOR="Green"]exit[/COLOR] to return to the GUI.

---

### Post by CatKiller on 2009-04-30
> **Penguin Guy said:**
> To run commands press Alt + F2 (for a single command)

You can't, you know. Unless it's been changed in the last couple of releases, Alt-F2 to run a command is provided by the panel. No panel, no Run dialogue. Which is why I suggested the OP create a launcher for the panel first.

---

### Post by sundar_ima on 2009-05-05
i have a different problem. i am not able to drag mail panel and keep it down. it was possible in 8.10. right click and move option is not there in ubuntu 9.04. anybody have any idea how to drag panel in ubuntu 9.04...

---

### Post by Penguin Guy on 2009-05-08
> **CatKiller said:**
> You can't, you know. Unless it's been changed in the last couple of releases, Alt-F2 to run a command is provided by the panel. No panel, no Run dialogue. Which is why I suggested the OP create a launcher for the panel first.
Thanks for the info - but I did also say: > or Ctrl + Alt + F1

---

### Post by Kareeser on 2009-05-08
> **sundar_ima said:**
> i have a different problem. i am not able to drag mail panel and keep it down. it was possible in 8.10. right click and move option is not there in ubuntu 9.04. anybody have any idea how to drag panel in ubuntu 9.04...

Like moving windows around, holding down alt while dragging will move panels in Jaunty.

---

### Post by sundar_ima on 2009-05-09
thank you man... it works...

---

### Post by bobheaps on 2009-07-24
I just used your suggestions for a problem I had - and it woked. Thanks very much Bob

---

