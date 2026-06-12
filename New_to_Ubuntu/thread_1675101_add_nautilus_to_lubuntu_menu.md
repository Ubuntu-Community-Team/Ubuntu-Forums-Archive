---
title: "add nautilus to lubuntu menu"
date: 2011-01-25
forum: New to Ubuntu
---

### Post by lance bermudez on 2011-01-25
I have nautilus install and i can call it from a script on my destop the script has in it
#!/bin/bash
#
# Disable Nautilus desktop, because we really really do not want it!
gconftool-2 -s -t bool /apps/nautilus/preferences/show_desktop false &
# Do not let Nautilus set the background, because we really really do not want this either.
gconftool-2 -s -t bool /desktop/gnome/background/draw_background false &
# Make Nautilus use spatial mode, should start-up quicker.
gconftool-2 -s -t bool /apps/nautilus/preferences/always_use_browser true &
# Make Nautilus show the advanced permissions dialog -- if it has to start, lets at least make it usable :) 
gconftool-2 -s -t bool /apps/nautilus/preferences/show_advanced_permissions true &
nautilus

and nautilus works the way i want. mostly the person that wants nautilus is because of the trash bin safty that pcmanfm dose not have. So how do I add my script to the menu list in the lower left hand corner. Nautilus is not in the menu list either.

---

### Post by lance bermudez on 2011-01-25
[Desktop Entry]
Name=Nautilus File Browser
Comment=Browse the file system with the file manager
TryExec=nautilus
Exec=nautilus --no-desktop --browser %U
Icon=system-file-manager
Terminal=false
StartupNotify=true
Type=Application
NoDisplay=false
Categories=GTK;System;Utility;Core;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=nautilus
X-GNOME-Bugzilla-Component=general
X-GNOME-Bugzilla-Version=2.30.1
X-Ubuntu-Gettext-Domain=nautilus

changed 
NoDisplay=ture to NoDisplay=false and took out OnlyShowIn=GNOME;

---

### Post by lance bermudez on 2011-01-25
sorry forgot to say where file was that i edited /usr/share/applications

---

