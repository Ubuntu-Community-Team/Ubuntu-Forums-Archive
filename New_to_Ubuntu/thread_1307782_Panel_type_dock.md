---
title: "Panel type dock"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by AndyP79 on 2009-10-31
Hi All,
 I have been seeing some panels, that have neat square type icons. What are those? Is it some sort of dockbar? 

Thanks

---

### Post by ibuclaw on 2009-10-31
Yep, they are dockbars.

I prefer Gnome-Do, but other people will have other recommendations.

Regards
Iain

---

### Post by tacantara on 2009-10-31
The other two popular docks are Awn and Cairo-Dock.  Both are available in the repositories.  I've used both, and find that they're fairly similar, although I think Cairo has more customization options.

To use these docks, you will have to enable Compiz Fusion (to support the more intense graphics required to make these docks work).

---

### Post by ibuclaw on 2009-10-31
> **tacantara said:**
> To use these docks, you will have to enable Compiz Fusion (to support the more intense graphics required to make these docks work).

Ehh? Compiz is a window manager, not a graphic card driver... (Hint, I'm using a dockbar without compiz).

---

### Post by tacantara on 2009-10-31
I stand corrected.  Thank you for pointing that out, tinivole.

---

### Post by NCLI on 2009-10-31
> **tacantara said:**
> The other two popular docks are Awn and Cairo-Dock.  Both are available in the repositories.  I've used both, and find that they're fairly similar, although I think Cairo has more customization options.

To use these docks, you will have to enable Compiz Fusion (to support the more intense graphics required to make these docks work).
Actually, the three most popular would now also include Docky, included with gnome-do in Karmic.

---

### Post by AndyP79 on 2009-11-01
I think everyone mis-understood what I was asking about. I was asking about in the PANEL. In the regular bar across the top of your screen, not AWN or any of those. I use AWN, but I have seen where people are placing their icons in the panel instead. Normally when you do this, it is just adding it from the menu, but these that I have seen, it is like they are there and have the function of a dock.

---

### Post by captainmnb on 2009-11-02
I think DockBar will accomplish what you're looking for:

[http://www.gnome-look.org/content/show.php/DockBar?content=97822](http://www.gnome-look.org/content/show.php/DockBar?content=97822)

There's also an experimental branch called DockbarX that's linked from that page, which adds some extra features.

---

### Post by fabounet on 2009-11-02
you can get the same with Cairo-Dock too (for instance the "Square-Dock" theme is a nice replacement of a classic panel)

PS : Docky is no more included in Gnome-Do (which is normal), so I think a better 3rd one is Kiba-Dock.

---

### Post by dxxvi on 2009-11-28
I'm using DockBarX and not satisfied with it: 1. it's not like other dock bars (e.g. awn) where icons for both running and non-running applications appear. only running applications appear in that dock bar. 2. the icons don't get bigger when I move the mouse over :)

If anybody finds an in-panel dockbar (which has icons for both running and non-running apps), could you please let me know? 

Thank you.

PS: in my definition, an in-panel dockbar is a dockbar which can be added to a panel (not like awn which needs a separate panel).

---

### Post by M7S on 2009-11-29
What do you mean with your first point, dxxvi? Dockbarx does support launchers. Just drag-and-drop the launchers you want from gnome-menu and enter the Resource class name of the program. If the program you add a launcher for is already running, just select it's resource class name from the drop-down list. (The next version of dockbarx will guess the resource class name and it will also make it possible to create launchers by "pinning" running programs.)

Your second point would be quite hard to implement in a gnome applet, assuming that you want the icons to get bigger than the panel is high (or wide if you use a vertical panel).



M7S
Developer of Dockbarx

---

### Post by dxxvi on 2009-11-30
> **M7S said:**
> Just drag-and-drop the launchers you want from gnome-menu and enter the Resource class name of the program.Wow, I didn't think my question would be answered by a dockbarx developer. I'll try that this evening. I didn't know about that drag-and-drop feature (maybe I didn't look for the documentation carefully or maybe the documentation is not easy to find).

Thanks for a good dock bar.

---

