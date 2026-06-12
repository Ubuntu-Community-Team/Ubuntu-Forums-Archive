---
title: "cairo-dock"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by patchido on 2008-12-04
i was using cairo dock in hardy... and it started to malfunction.. so i said.. well ill upgrade to intrepid... and i did... i thought that might solve something but it didnt... so i unistalled cairo and reinstalled .. well.. i think i did... the thing is that i still cant make it work.. can anyone help me to get rid of everything of cairo so i can fresh install?

---

### Post by ajmorris on 2008-12-04
> **patchido said:**
> i was using cairo dock in hardy... and it started to malfunction.. so i said.. well ill upgrade to intrepid... and i did... i thought that might solve something but it didnt... so i unistalled cairo and reinstalled .. well.. i think i did... the thing is that i still cant make it work.. can anyone help me to get rid of everything of cairo so i can fresh install?

hi there,
to completely remove cairo, and re-install it, run the following:
```
sudo apt-get remove --purge cairo-dock && sudo apt-get install cairo-dock
```
That will remove it from your system, however, you also need to remove config files (which is probably where the issue is coming from, and not the package itself)
So, back up anything you need in ~/.cairo-dock  and run:
```
rm -r ~/.cairo-dock
```

If doing the above does not fix it, open up a terminal, and run cairo-dock in it, and post here any output from the terminal.


AJ

---

### Post by patchido on 2008-12-04
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:263)  
  while opening module '/usr/lib/cairo-dock/libcd-xfce-integration.so' : (libthunar-vfs-1.so.2: cannot open shared object file: No such file or directory)
cairo_dock_get_desklet_decoration (personnal)
nouvelle icone d'appli (140509387)
warning :  (cairo-dock-application-factory.c:cairo_dock_create_surface_from_xpixmap:125)  
  This pixmap is undefined. It can happen for exemple for a window that is in a minimized state when the dock is launching.
 insertion de Gmail - gladys.dgr - Thunderbird apres Synaptic Package Manager -> iSeparatorType : 1
nouvelle icone d'appli (125829589)
warning :  (cairo-dock-application-factory.c:cairo_dock_create_surface_from_xpixmap:125)  
  This pixmap is undefined. It can happen for exemple for a window that is in a minimized state when the dock is launching.
nouvelle icone d'appli (33554435)
nouvelle icone d'appli (48234525)
nouvelle icone d'appli (136314958)
nouvelle icone d'appli (146800651)
iRotation:0°
decorations : default
 insertion de horloge apres Mercury 1.9.2 -> iSeparatorType : 3
iRotation:0°
decorations : default
  MaJ des decorations du fond -> 2852.00x43.00
add personnal
add Starcraft2
add CD box
add scotch
add frame&reflects
add dark
add none
add frame with scotch
add clear
add default
add personnal
add Starcraft2
add CD box
add scotch
add frame&reflects
add dark
add none
add frame with scotch
add clear

---

### Post by ajmorris on 2008-12-04
ok, so you're running xfce. The issue could be the xfce integration....
try reinstalling libthunar-vfs-1-2

Then restart xfce, and try starting cairo-dock again. If this does not work, try another DE/wm if you have one installed.


AJ

---

### Post by patchido on 2008-12-04
hmm... that wasnt installed and i istelled it.. and then runned cairo, same thing.

i dont know how to restart xfce and, it seems as if the cairo is working but i just cant see it cause if i open up by terminal cairo, when i minimize something it responds to it

---

### Post by ajmorris on 2008-12-04
> **patchido said:**
> hmm... that wasnt installed and i istelled it.. and then runned cairo, same thing.

i dont know how to restart xfce and, it seems as if the cairo is working but i just cant see it cause if i open up by terminal cairo, when i minimize something it responds to it

do you have direct rendering active (and compiz or another composite window manager active)

run: ```
sudo glxinfo | grep -i "direct rendering"
```  to check for direct rendering.


AJ

---

### Post by patchido on 2008-12-04
pato@pato-laptop:~$ sudo glxinfo | grep -i "direct rendering"
[sudo] password for pato: 
direct rendering: Yes
pato@pato-laptop:~$

---

### Post by patchido on 2008-12-08
any help?

---

### Post by patchido on 2008-12-10
plzzzzzzzz

---

### Post by AC_Blenda on 2009-02-25
lol. looks like your on your own here.

---

