---
title: "Network Manager Icon Disappeared From Panel"
date: 2010-06-27
forum: New to Ubuntu
---

### Post by mapes12 on 2010-06-27
I've just logged on and got a message saying that their was a problem loading something to my panel. So I restarted my laptop and now my Network Manager icon is no longer present on my panel. Any ideas how to get it back again please?

Mark

---

### Post by Chame_Wizard on 2010-06-27
Application Launcher(the distro logo)>Applications>System>Network Manager>right click on icon to 'add to panel".

You should see it now.

---

### Post by nhasian on 2010-06-27
is your indicator applet loading?  it will have the sound icon, the messaging icon, network icon, etc.  if you need to add it you can do so by right clicking on the panel and selecting "add to panel" then choosing the indicator applet.

---

### Post by mapes12 on 2010-06-29
Thanks Guys, I got my Network Manager icon back but now my sound icon has disappeared. Can't find it anywhere in the menu's?

---

### Post by Rubi1200 on 2010-06-29
If you don't mind having any custom settings reset you could try the following from the terminal:

```
gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel
```This resets the panels to their original defaults.

---

### Post by saty on 2010-07-02
> **Rubi1200 said:**
> If you don't mind having any custom settings reset you could try the following from the terminal:

```
gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel
```This resets the panels to their original defaults.
Thank you very much! It worked like a charm. :)
the only thing is that my custom panel items are gone.

---

### Post by Rubi1200 on 2010-07-02
> **saty said:**
> Thank you very much! It worked like a charm. :)
the only thing is that my custom panel items are gone.

Glad it worked, but I did say:

> If you don't mind having any custom settings reset

;)

---

### Post by Egi_Power on 2010-12-18
> **rubi1200 said:**
> if you don't mind having any custom settings reset you could try the following from the terminal:

```
gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel
```this resets the panels to their original defaults.

I just converted one of my friends to Ubuntu user recently.
His icons from the panel disappeared.
Using the above commands now everything is back to normal, as it was before.
Thanks rubi1200!

Egi_Power

---

### Post by Rubi1200 on 2010-12-18
> **Egi_Power said:**
> I just converted one of my friends to Ubuntu user recently.
His icons from the panel disappeared.
Using the above commands now everything is back to normal, as it was before.
Thanks rubi1200!

Egi_Power
No problem, you are more than welcome :)

---

### Post by battlemage04 on 2010-12-23
ive been having networking issues over the passed few weeks and this looks promising thanks for all everyone's hard work.

> **Rubi1200 said:**
> If you don't mind having any custom settings reset you could try the following from the terminal:

```
gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel
```This resets the panels to their original defaults.


ok, so that worked... however, my network managment icon is non-existant, as well as not having the Application Launcher>Applications>System>**Network Manager **is not allowing me to add the "custom" icon to my panel

any way i can get this running? also yes. i do have the default network manager installed. its just not showing up.

---

