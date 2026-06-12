---
title: "How would I install this theme?"
date: 2009-07-10
forum: New to Ubuntu
---

### Post by FoxFireX on 2009-07-10
[http://gnome-look.org/content/show.php/Carbon+Fibre?content=107504](http://gnome-look.org/content/show.php/Carbon+Fibre?content=107504)



I don't have emerald yet, so.. yeah.

I don't wanna try to get it and do something wrong.

So if somebody could write me a step by step tutorial it would be good.

---

### Post by amadeus266 on 2009-07-10
First you need to have emerald installed
```
sudo apt-get intall emerald
```

Download the file and save it. Open emerald-theme-manager and click import. Navigate to the file and click open. You will then see it in emerald-theme-manager, Click and your done.

If it doesn't change your theme you may need to start emerald..```
emerald --replace
```

---

### Post by FoxFireX on 2009-07-10
hm, wheres a good place to save it?

---

### Post by amadeus266 on 2009-07-10
> **FoxFireX said:**
> hm, wheres a good place to save it?

In your home directory is always a good choice. I actually created a folder just for themes and such.

---

### Post by FoxFireX on 2009-07-10
Okay emeralds open, themes imported, wheres the apply button :S?

---

### Post by amadeus266 on 2009-07-10
There isn't one. Your theme should change when you click on the theme preview. If it doesn't then try starting emerald with the command I gave earlier.

In Terminal type ```
emerald --replace
```

By the way, you also need to have compositing enabled. Do you have Compiz-fusion installed and working?

---

### Post by FoxFireX on 2009-07-10
Uh well it worked, but as soon as I closed terminal the theme went poof

---

### Post by amadeus266 on 2009-07-10
Do you have fusion-icon installed? If not, install it with ```
sudo apt-get install fusion-icon
``` then hit F2 and type in fusion-icon.

It will show up in the system tray. You can right-click the icon and get a menu, then click on Select Window Decorator and choose Emerald.

---

### Post by zerhacke on 2009-07-10
That's alt-F2.

---

### Post by amadeus266 on 2009-07-10
Sorry, that is hit <Alt F2>

---

### Post by FoxFireX on 2009-07-10
Uh, wheres my tray at? I dont see anything, and when I typed that in, it just like freshed everything, and un-did all of my compiz settings..so it seems, my workspaces went back to 2, instead of 4 and my desktop cube no longer works.. and when i hit ctrl alt (right arrow) its not the cube thing, or the fancy thing that pops up and slides over to the next desktop now its just some boring looking classic workspace switcher..and the theme still hasn't apply'd.

---

### Post by UbuntuNerd on 2009-07-10
right click on the work spaces and hit preferences where it says "number of work spaces" select 4 also make sure you still have the effects activated by going to System > Preferences > appearance under "visual Effects" make sure you have normal or extra selected

---

### Post by kandieyman on 2009-07-10
You need to install compizconfig-settings-manager. This will allow you to change your compiz settings (as if the name didn't make that painfully obvious). Then you can specify desktop cube with 4 desktops. Understand, though that there are many, many settings. It will take time for you to wrap your head around it.

---

### Post by FoxFireX on 2009-07-10
Yeah, compiz settings has been installed for a few days... I was saying that what he told me to do basically reset everything..and now nothings normal... no cube etc

---

### Post by FoxFireX on 2009-07-10
bump, got it back to normal it seems. But emerald still is not working, like i open the themer and click on the theme and it does nothing.

If I go to the terminal and put in emerald --replace, it works. But If I close the terminal the theme dissapears.

And yeah I already have fusion

---

### Post by Arquis on 2009-07-10
Go to Preferences, Sessions and add emerald --replace there then boot (or logout, I guess). It should work. I don't know if this is a better solution, but it does the job.

---

### Post by FoxFireX on 2009-07-10
There is no sessions in preferences..?

---

### Post by amadeus266 on 2009-07-11
If you have compiz settings manager installed start it and go to Window Decorations and on the "Command" line enter emerald --replace. That should make emerald your default window decorator when compiz-fusion starts. And sorry, I didn't realise that installing fusion-icon would reset your compiz settings. If for some reason you no longer want emerald to be the default you can enter gtk-window-decorator --replace to use the defaults or compiz-decorator --replace.

---

### Post by kandieyman on 2009-07-11
When right-clicking on your fusion icon, which you should have launch on session startup, you are select the window manager to use perpetually. Emerald should be one of those choices.

---

