---
title: "Trouble with emerald.."
date: 2009-07-10
forum: New to Ubuntu
---

### Post by FoxFireX on 2009-07-10
Well, I downloaded a theme.. Imported it into emerald. Clicked on the imported theme.

Nothing happened.

Went to terminal and typed in "emerald --replace" and it worked.

closed terminal, and then the theme dissapeared.

I have compiz settings manger, and fusion if it matters.

---

### Post by boblemur on 2009-07-10
if you want to keep emerald open when you close it. run:

```

emerald --replace&

```

that should hold it open. also i think you need to goto compiz settings

```

sudo aptitude install compizconfig-settings-manager

```

and have a look under:

system > preferences > compiz settings manager

it should have an option to select emerald (sorry if this is a little too vague)

---

### Post by FoxFireX on 2009-07-10
What about when I reboot my PC will it boot emerald at start up? I was just testing out themes and the different types.. som1 said that emerald themes usually look better.. then metacity themes.. seems like they don't to me :S, I like the fact that the metacity themes change everything, the window style and the gnome panels and menus..


The only thing I found in compiz is the window decorator menu, which contains something that looks like that might be related to what we are talking about? It shows a command as "gtk-window-decorator --replace" I'm guessing I put emerald --replace there? and it'll launch emerald at startup instead?

---

### Post by boblemur on 2009-07-10
you could try, but before you try anything like that make sure your comfortable repairing it from terminal :P in case you break your GUI trying... cause you dont want to have to clean format because you accidentally broke X or something related to it.

i havnt used emerald much but i dono if i really like it, its so much work to make the gui look consistant and nice etc.. that its not really worth it

---

### Post by earthpigg on 2009-07-11
> **FoxFireX said:**
> 
The only thing I found in compiz is the window decorator menu, which contains something that looks like that might be related to what we are talking about? It shows a command as "gtk-window-decorator --replace" I'm guessing I put emerald --replace there? and it'll launch emerald at startup instead?

exactly correct :D

edit: i generally go theme-hunting here: [http://www.compiz-themes.org/index.php?xsortmode=high&page=0&xcontentmode=103](http://www.compiz-themes.org/index.php?xsortmode=high&page=0&xcontentmode=103)

download a dozen or two, import them all using system -> preferences -> emerald theme manager

and see which you like. i am a fan of 'adonis', myself.

---

### Post by Andy06 on 2009-07-11
Metacity sort of = Compiz
They are both window managers, that why everything changes.

Emerald is merely a window decorator, part of compiz. It only draws borders. Useful for aero glass and vista effects.

You need to have compiz enabled for it to work so make sure compiz starts on start up. Then you can goto CCSM (compiz settings manager), then the window decorator option and there you will see gtk window -replace, you can switch that to emerald through a GUI if you install the package "compiz fusion icon" from add/remove and synaptic.

In fact you can switch between gtk and emerald from a menu on the panel with it.

BTW, afaik, emerald is defunct. Not active anymore, then again it does not provide anything complicated so there is no real need for regular updates.

---

### Post by Clorow on 2009-07-11
Yeah - there is a small program that sits in the notification tray called fusion-icon. You can set it to load at startup, and when you right-click it, it gives you all sorts of options, such as replacing window decorator or window manager.

```
sudo apt-get install fusion-icon
```

---

### Post by amadeus266 on 2009-07-11
> **FoxFireX said:**
> Well, I downloaded a theme.. Imported it into emerald. Clicked on the imported theme.

Nothing happened.

Went to terminal and typed in "emerald --replace" and it worked.

closed terminal, and then the theme dissapeared.

I have compiz settings manger, and fusion if it matters.

Go back to the previous discussion and you will see where I posted a solution for you. And sorry, I didn't realize the installed fusion-icon would reset your settings.

---

### Post by FoxFireX on 2009-07-11
Yeah, its cool bro. I already had fusion icon installed. Now I know what emerald themes do. So I can keep that in mind. The kind I want must be metacity, cause i want it to change everything. Not just decorate windows, but it could come in handy.. Say I like the way the gnome panel and stuff looks but not the way the windows do, I could just use emerald for that :D

---

### Post by amadeus266 on 2009-07-11
If you look around on gnome-look.org and other sites you can find complete themes that will change everything. Some even include emerald themes. Emerald only affect the window borders. Preferences>Appearance will change everything else.

---

