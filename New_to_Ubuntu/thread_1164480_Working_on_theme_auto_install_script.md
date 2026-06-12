---
title: "Working on theme auto install script"
date: 2009-05-19
forum: New to Ubuntu
---

### Post by altech6983 on 2009-05-19
Hey guys, its me again :-).

I am writing a script for a custom theme package install (I'm not saying I made the theme, icons, and pointer, I just packaged it together for me, did mod the theme a little though)

Everything works pretty good as it is but there is one thing annoying me :-( . When I go to install the theme, icons, or pointer the command I use is 
```
gnome-appearance-properties -i [path to theme]
```The problem is that by using this method the actual appearance box pops up and ask if you want to apply the theme and on top of that then you have to close the appearance box (plus another two times). I really wanted the script to be automatic with no interaction. The steps to clicking out of it goes like this

First theme pops up:
Click Apply theme
Click Close

Second theme pops up:
Click Apply theme
Click Close

Third theme pops up:
Click Ok
Click Close

That is what I wanted to avoid. Anybody know how to do this?

```
#!/bin/bash
#Script by: Albert Eardley

#finds the user installing the theme
user=`who am I | awk '{print $1}'`

#installs required gtk engine
sudo apt-get install gtk2-engines-nodoka

#Installs Background Blue World.jpg

	#checks if folder ~/.backgrounds exist if not creates it
	if [[ ! -d "/home/$user/.backgrounds" ]]; then
		mkdir ~/.backgrounds
	fi

	#copies the background to the folder ~/.backgrounds
	sudo cp ./Background/Blue\ World.jpg /home/$user/.backgrounds/

	#This block sets up the options for the background
	gconftool-2 --type=string -s '/desktop/gnome/background/color_shading_type' solid
	gconftool-2 --type=bool -s '/desktop/gnome/background/draw_background'true
	gconftool-2 --type=string -s '/desktop/gnome/background/picture_filename' "/home/$user/.backgrounds/Blue World.jpg"
	gconftool-2 --type=int -s '/desktop/gnome/background/picture_opacity' 100
	gconftool-2 --type=string -s '/desktop/gnome/background/picture_options' centered
	gconftool-2 --type=string -s '/desktop/gnome/background/primary_color' '#68684b4b3333'
	gconftool-2 --type=string -s '/desktop/gnome/background/secondary_color' '#68684b4b3333'

#Installs Icon Set Black-white_2_Style
	rm -rf ~/.icons/BlackWhite2Style
	gnome-appearance-properties -i ./Icons/BlackWhite2Style.tar.gz

#Installs Pointer Set Obsidian
	rm -rf ~/.icons/Obsidian
	gnome-appearance-properties -i ./Pointer/Obsidian.tar.bz2

#Installs Dusty Albert Mod Theme
	rm -rf ~/.themes/Dust
	gnome-appearance-properties -i ./Theme/Dust.tar.gz
	wait 1

#Selects themes for use
	#gconftool-2 --type=string -s '/desktop/gnome/interface/icon_theme' BlackWhite2Style <-- This isn't needed right now because 		I have to click apply theme
	#gconftool-2 --type=string -s '/desktop/gnome/peripherals/mouse/cursor_theme' Obsidian <-- This isn't needed right now 		because I have to click apply theme
	gconftool-2 --type=string -s '/apps/metacity/general/theme' Dust
	gconftool-2 --type=string -s '/desktop/gnome/interface/gtk_theme' Nodoka-Midnight
```

---

