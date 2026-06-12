---
title: "DockbarX launcher problem"
date: 2009-08-28
forum: New to Ubuntu
---

### Post by Zopiac on 2009-08-28
I just started using DockbarX a few days ago, and love it, but I have one problem. I have five launchers (Opera, Skype, Rhythmbox, Pidgin, and Limewire), and want to add two more (Nautilus and Gnome-Terminal) but when I add them, when I log out and back in (or restart my computer, etc.), those two are gone? Is there problem with those two launchers on DockbarX or can you only have five?

Thanks in advance :)

---

### Post by Zopiac on 2009-08-28
Well, I took off Limewire and Skype and put on Nautilus, but when I logged out and back in it was gone again, even though there were only four launchers when I logged out. So, I now only have three launchers and know it isn't a quantity problem.

So I put Limewire back on, and logged out and back in. Now it won't stay on, as well! Apparently it is also not a problem with specific programmes.

What is the problem here?

EDIT: I just figured it out; I looked in the ~/.dockbar/launchers.list and found a big problem. I currently only have Opera, Rhythmbox, and Pidgin as launchers, but the file apparently keeps all of the launchers, in some way. copy of file:

```
(lp0
(S'Opera'
p1
S'/usr/share/applications/opera.desktop'
p2
tp3
a(S'org-limewire-ui-swing-Main'
p4
S'/home/zopiac/.gnome2/panel2.d/default/launchers/limewire.desktop'
p5
tp6
a(S'Rhythmbox'
p7
S'/usr/share/applications/rhythmbox.desktop'
p8
tp9
a(S'Pidgin'
p10
S'/usr/share/applications/pidgin.desktop'
p11
tp12
a.
```

I changed it to the following and now everything works!

```
(lp0
(S'Gnome-terminal'
p1
S'/home/zopiac/.gnome2/panel2.d/default/launchers/gnome-terminal.desktop'
p2
tp3
a(S'Nautilus'
p4
S'/home/zopiac/.gnome2/panel2.d/default/launchers/nautilus.desktop'
p5
tp6
a(S'Opera'
p7
S'/home/zopiac/.gnome2/panel2.d/default/launchers/opera.desktop'
p8
tp9
a(S'Rhythmbox'
p10
S'/home/zopiac/.gnome2/panel2.d/default/launchers/rhythmbox.desktop'
p11
tp12
a(S'Pidgin'
p13
S'/home/zopiac/.gnome2/panel2.d/default/launchers/pidgin.desktop'
p14
tp15
a.
```

EDIT AGAIN:
Apparently I have to have the launchers on the Panel itself, too? I removed the launchers from the panel and now they wont show up in the Dockbar either :mad: 

I still need help on this, then :(

---

### Post by M7S on 2009-08-28
Hi. I'm the developer of DockbarX. The file you listed is containing only two things. The resource names of the applications so that dockbarx knows which launcher that belongs with which windows and an address to an .desktop file so the launcher knows what program to launch and what icon to use. You can't remove an .desktop file that dockbarx uses. This means that you can't make an dockbarx launcher from a launcher on the panel and then remove the launcher from the panel.

To avoid double launcher you should either add the launcher directly from gnome-menu or make a new launcher in a folder somewhere where you don't have to see it and drag it to dockbarx from there.

Hope this solves your problem.

---

### Post by Zopiac on 2009-08-28
> **M7S said:**
> Hi. I'm the developer of DockbarX. The file you listed is containing only two things. The resource names of the applications so that dockbarx knows which launcher that belongs with which windows and an address to an .desktop file so the launcher knows what program to launch and what icon to use. You can't remove an .desktop file that dockbarx uses. This means that you can't make an dockbarx launcher from a launcher on the panel and then remove the launcher from the panel.

To avoid double launcher you should either add the launcher directly from gnome-menu or make a new launcher in a folder somewhere where you don't have to see it and drag it to dockbarx from there.

Hope this solves your problem.

I tried dragging straight from /usr/bin, but that didn't work. I also tried editing the file to "S'usr/bin/opera' etc., but that didn't work either, I will try from the menu though :) thanks!

---

### Post by M7S on 2009-08-29
Draging straight from /usr/bin wont work, no. You need to drag launchers - not the bin file. You can drag them directly from gnome-menu or from a folder where you made your custom launcher earlier.[FONT=monospace] Dragging from [/FONT]/usr/share/applications/ should work as well.

---

### Post by mattlandry on 2009-11-09
I have been using dockbarx and I love it. The only issue I have found with it is that some launchers won't add. When I drag them to the dockkbarx they just disappear and do not give me an option to choose the class name. 

I have successfully added firefox, gnome terminal, gedit, virtualbox, vlc, and evolution but I can't seem to get Nautilus, Totem and Banshee launchers to add. I have tried dragging them from both the menu and .desktop files I added to the desktop. 

I can add them in dockbar with no issue but I really prefer the look and options of dockbarx. Any ideas on why these particular launchers don't seem to play nice and how I might be able o get this working?

---

