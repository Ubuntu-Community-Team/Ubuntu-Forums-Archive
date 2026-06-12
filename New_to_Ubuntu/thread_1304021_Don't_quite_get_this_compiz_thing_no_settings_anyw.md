---
title: "Don't quite get this compiz thing: no settings anywhere"
date: 2009-10-28
forum: New to Ubuntu
---

### Post by Pott on 2009-10-28
Well apparently compiz is already installed, so I ran it through the terminal, the desktop/screen reset but I had no setting screen or anything. I went back to the stock Appearance/Visual Effects/Extra and kept the settings.

What does compiz do? It seems to run in the background since Conky says it's running out there. Where can I access the settings, or do I need to install packages for a GUI way of getting there..?

Thanks!

---

### Post by bkratz on 2009-10-28
> **Pott said:**
> Well apparently compiz is already installed, so I ran it through the terminal, the desktop/screen reset but I had no setting screen or anything. I went back to the stock Appearance/Visual Effects/Extra and kept the settings.

What does compiz do? It seems to run in the background since Conky says it's running out there. Where can I access the settings, or do I need to install packages for a GUI way of getting there..?

Thanks!


just realized you said you were in terminal --so ignore this!!!


In the menus
if installed


system---preferences---compiz config manager

---

### Post by Bölvaður on 2009-10-28
> **bkratz said:**
> just relalized you said you were in terminal --so ignore this!!!


In the menus
if installed


system---preferences---compiz config manager

you might need to find compiz conig settings manager (ccsm) under (Applications &#8594; **Add/remove**) or (System &#8594; Administration &#8594;** Synaptic Package Manager**)

that program is only to change the config files that you already have, but is a nicer way to deal with compiz.

---

### Post by shadow120 on 2009-10-28
if you have installed "Advanced Desktop Effects Settings (ccsm)" then it will be under system - preferences - compizconfig settings manager

---

### Post by community nerd on 2009-10-28
I have it installed but it does not show up in the menu. I also installed the emerald theme thing but I also cant find that too.

---

### Post by shadow120 on 2009-10-28
try to run it from the terminal
```
ccsm
```

---

### Post by Pott on 2009-10-28
Ah thanks guys, it's installing now :) 

Aaaand it works. Thanks!


Waaait

There's still something I don't get then.

When does Compiz take over from the standard Gnome appearance settings?

Is it basically just like a much more powerful version of the Visual Effects, where I can configure every aspects of it?

---

### Post by Bölvaður on 2009-10-29
> **Pott said:**
> 
Is it basically just like a much more powerful version of the Visual Effects, where I can configure every aspects of it?

no, it's just a gui tool to change the config files.
the stuff in visual effects just give you a choice of turning it off or on... and perhaps 1 other option that has some preset config.

so you will have to have compiz running.

---

### Post by HydroTech on 2009-10-29
Glad you got your compiz running. I like linux ubuntu/mint anyway but the experience is much nicer and much more convenient when all the visual effects are on. I had an old video card on my computer and it was pretty bad performance graphically so make sure you have a good video card that can handle compiz effects. I think you said something like 'what is compiz for?' or something: Besides being more visually pleasing it helps by making your workspace expanded into four desktops. It's good to play with settings until you get them the way you like.

---

### Post by Pott on 2009-10-29
So how does it work? 
I can either select the none/some/extra on the Appearance settings or control it all manually through the Compiz settings, and whichever I chose would automativally override the other?
Or are they not mutually exclusive and could both work at once..?

---

### Post by thiebaude on 2009-10-29
Just make a choice of which one you want to use

---

### Post by HydroTech on 2009-11-01
From my understanding(because I didn't program compiz)turning on effects turns on certain Compiz settings by default which if not liked can be changed from Compiz settings in the menu. Or if you want additional settings turned on then you can go back to the Compiz settings in menu. Now turning certain settings on will override other settings and should notify you that it's doing that.  :)

---

