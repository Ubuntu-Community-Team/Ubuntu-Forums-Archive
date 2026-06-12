---
title: "Application menu problem"
date: 2009-06-15
forum: New to Ubuntu
---

### Post by smokystone on 2009-06-15
Hi, I am using Ubuntu 9.04, and encounter a problem on Menu Bar. I tried to remove some shortcuts in the Applications of menu bar, but after they were removed and the edit window was closed, the Application menu was not able to be opened, I mean the application list didnt show up and the edit window neither can be opened. Now I can only use these applications from gnome-do, not from the routine application menu.

Anyone knows what s the problem and how to fix it?

Thanks a lot. :(:(

---

### Post by hayden92 on 2009-06-15
You could try opening the terminal and typing
```
killall gnome-panel
``` and see if that works.

Hayden

P.S. if this doesn't work, you might want to revert to the original menu by pressing ALT+F2 and then typing "alacarte"

---

### Post by smokystone on 2009-06-15
> **hayden92 said:**
> You could try opening the terminal and typing
```
killall gnome-panel
``` and see if that works.

Hayden

P.S. if this doesn't work, you might want to revert to the original menu by pressing ALT+F2 and then typing "alacarte"
I have tried that, actually, I have tried to fix by restarting the system, but didnt work. i think it has to be done from gconf-editor, but i dont know how to do that.
anyway, thx a lot.

---

### Post by smokystone on 2009-06-15
Another problem is if I add the "Main Menu" to the panel, there are only "Places" and "System" inside without "Applications".

No idea what s the problem.  :(:(

---

### Post by smokystone on 2009-06-15
Worse problem, when I clicked system> preferences> Main Menu, no response totally.

:(:(:( what have I done?

---

### Post by hayden92 on 2009-06-15
You haven't uninstalled evolution by any chance have you? I had a similar problem when I did this.

If you are still stumped you can try:

ALT+F2
"gksu"
"synaptic"
quick search for "gnome-panel"

find "gnome-panel" and gnome-panel-data" and mark them for reinstallation

I hope this helps!

---

### Post by smokystone on 2009-06-15
> **hayden92 said:**
> You haven't uninstalled evolution by any chance have you? I had a similar problem when I did this.

If you are still stumped you can try:

ALT+F2
"gksu"
"synaptic"
quick search for "gnome-panel"

find "gnome-panel" and gnome-panel-data" and mark them for reinstallation

I hope this helps!
No, I didnt try to install evolution, but just try to remove some application shortcuts from the list and then the edit menu was stuck, and then the application menu was gone.

Anyway I have resolved the problem by doing this way:

The application menu setting actually is stored in the system default file and the user defined file. The user defined file is located in "/home/<username>/.config/menus/applications.menu". And I found that the application.menu file was totally empty when I opened it. 

What I did was simply to remove the file:

$ rm /home/<username>/.config/menus/applications.menu

then restart system, login user which you removed the file from, and then system will generate a new user file from the system default file. Then it is done!

Anyway, thanks for your help, hayden92. I have to say it is really happy to use Ubuntu because you always have chance to communicate in a community and learn new things, and it never happened to me when I used Windows. :D

---

### Post by cmannnn on 2009-08-13
i dont know if this will help i have the same problem i loged into another account on my comp and the app menu drops down i know the problem for me is that i messed up the config file

---

### Post by bswilson on 2009-10-20
I just did the exact same thing.  I had right-clicked on the Gnome Menu and selected **Edit Menus**.  Then I attempted to click the check boxes to display additional menu components.  Once I did that, I can no longer get the **Applications** part of the menu to expand.  **Places** and **System** work, but I can't und what I did.

Did you ever get a satisfactory resolution to the problem?

---

### Post by bswilson on 2009-10-20
Augh!  I didn't read carefully enough about how you fixed the issue.  Thanks for documenting it here.

---

