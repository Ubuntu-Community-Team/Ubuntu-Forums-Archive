---
title: "Scrolling to side of the screen options."
date: 2009-09-23
forum: New to Ubuntu
---

### Post by ikitson on 2009-09-23
I just reinstalled jaunty jackalope 9.04 and after 30 minutes of looking around, I was unable to find the place where i can assign specific actions to happen when i slide my cursor to the side of the screen. Can anyone help me out on this please? ty

Also, I have 2 desktop panels, where can i add 2 more to complete my cube?

---

### Post by oboedad55 on 2009-09-23
> **ikitson said:**
> I just reinstalled jaunty jackalope 9.04 and after 30 minutes of looking around, I was unable to find the place where i can assign specific actions to happen when i slide my cursor to the side of the screen. Can anyone help me out on this please? ty

Also, I have 2 desktop panels, where can i add 2 more to complete my cube?

Install compiz setting manager if not already there. Then look in "scale" and "expo" to get those effects.

---

### Post by ikitson on 2009-09-23
I remember a seperate window allowing me to do this, it might have come from the compiz manager, but as far as i can see i can't assign the side scroll hotkeys nor can i add more desktop panels.

---

### Post by oboedad55 on 2009-09-23
> **ikitson said:**
> I remember a seperate window allowing me to do this, it might have come from the compiz manager, but as far as i can see/media/ubuntu-9/home/dlouhy/Downloads/picasa_3.0-current_i386.deb i can't assign the side scroll hotkeys nor can i add more desktop panels.

Can't you right-click on a panel and choose "new panel"?

---

### Post by ikitson on 2009-09-23
> **oboedad55 said:**
> Can't you right-click on a panel and choose "new panel"?

Are we both speaking of a panel as in (ctrl + alt + down) shows more desktops(panels)? Or am i completely getting this term wrong? xD

---

### Post by ikitson on 2009-09-24
Bumping for further help, i've looked elsewhere before posting again, last post was a few hours ago.

---

### Post by tom.swartz07 on 2009-09-24
Hiya

Try installing compiz config settings manager. there will be 2 entries, one for ccsm, and one for 'simple compiz config settings manager'. Theyll be listed under system/preferences/

when you open the simple manager, you could add extra panels, extra screens and add commands for the edges of your screen.

Hope this helps!

---

### Post by ikitson on 2009-09-24
> **tom.swartz07 said:**
> Hiya

Try installing compiz config settings manager. there will be 2 entries, one for ccsm, and one for 'simple compiz config settings manager'. Theyll be listed under system/preferences/

when you open the simple manager, you could add extra panels, extra screens and add commands for the edges of your screen.

Hope this helps!

which option do i go to to do this?

---

### Post by tom.swartz07 on 2009-09-24
I think you had some of the previous posts confused; a 'panel' is the bar on the top or bottom of your screen. I believe you were trying to say that you would like to add more virtual desktops. (the screens that change with ctrl + alt + *direction*)

sccsm will take care of that. You could specify if you want a wall of 4 side-by-side, or if you prefer a 2x2 config. Its beefy enough to handle most desires. If you want to fine tune your special effects, then use the full compizconfig settings manager there.

---

### Post by tom.swartz07 on 2009-09-24
> **ikitson said:**
> which option do i go to to do this?


Open up add/remove programs from your applications panel. in the search box, type in compiz config or ccsm

install that, and you should have the programs listed in your preferences menu

hope this helps!

---

### Post by ikitson on 2009-09-24
> **tom.swartz07 said:**
> Open up add/remove programs from your applications panel. in the search box, type in compiz config or ccsm

install that, and you should have the programs listed in your preferences menu

hope this helps!

Once in the settings window, which icon do I open/edit ?

---

### Post by tom.swartz07 on 2009-09-24
> **ikitson said:**
> Once in the settings window, which icon do I open/edit ?

Im confused. Could you please be as descriptive as possible? Do you have the program installed?
Once its installed, it should look like this when you open it

[IMG]http://lh5.ggpht.com/_tORug_uHNu4/Srr5pse4FkI/AAAAAAAAAHQ/O9t4Ml72yTc/s800/Screenshot-1.png[/IMG]

From there, "edges" will allow you to edit your screen edge commands, 'desktop' will allow you to change the number of virtual desktops.
There are also some other settings there, feel free to play around. BUT BE WARY! make sure you note what you change, so that you could change it back if something goes wrong.

---

### Post by ikitson on 2009-09-24
TY, this will help e once i figure out what's wrong, the problem is now, there is no "simple" compiz manager installed, nor does it show in the list of all available applications, what would the next step be?

---

### Post by tom.swartz07 on 2009-09-24
> **ikitson said:**
> TY, this will help e once i figure out what's wrong, the problem is now, there is no "simple" compiz manager installed, nor does it show in the list of all available applications, what would the next step be?

open a terminal, from applications/accessories
and type

sudo apt-get install simple-ccsm

it will prompt you for your password, then ask if you want to install it. say yes with 'enter', then it should be all set!

---

### Post by ikitson on 2009-09-24
Problem solved :D thanks for all your help.

---

### Post by tom.swartz07 on 2009-09-24
Sure thing! 

Glad to help!
Please make sure you mark this thread as 'solved' (under thread tools at the top of the page) so that others could use this as a guide!

---

