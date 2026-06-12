---
title: "Finding launcher/commands for installed packages"
date: 2010-01-17
forum: New to Ubuntu
---

### Post by knurledflanges on 2010-01-17
Hello, new to Linux and I've run into a certain issue a couple times. When I install a .deb package using GDebi (which I realize isn't the most preferred way to install software in Ubuntu if you have a choice), how exactly do you know where it is or how to run it if you don't have any other documentation for it? For example, I just downloaded this: [http://www.zelda-solarus.com/jeu-zsdx-demo&lang=en](http://www.zelda-solarus.com/jeu-zsdx-demo&lang=en) (the 32-bit version for Ubuntu). I opened it with GDebi and installed it, but then didn't know what to do. It didn't appear automatically in the "Games" folder or elsewhere in the menu, and there are no instructions available in a language I speak. By trial and error I discovered that I can start the game using the terminal command 'zxds', and I know how to use that to make my own launcher which I presume I could put in "Applications - Games" somehow, but what's the non-trial-and-error-based thing to do in this situation?

---

### Post by mc4man on 2010-01-17
If the .deb is already installed and you have synaptic package manager installed  then just search it and look at the installed files.

(don't use xubuntu so don't know if it uses synaptic (though you can install it

Typically most apps will have a file in a directory 'in your path' that executes the app. (and the command is usually the file name

Directories 'in your path' that can contain executables are 
/usr/bin
/usr/local/bin
/usr/games

You'd also be surprised what info you gain get from Gdebi either before or after the install - just look at the included file tab - there's a dir/file tree and sometimes the contents are displayed in r. side box

Ex.  - your deb
screen one shows the likely file to launch - /usr/games/zxds
In the box I can see it's a script, so that also points to being the command to launch

screen 2 shows the readme, which mainly about building the source does show how to run

screen 3 shows a more typical app that uses a binary rather than script to launch - (using gedit as ex. though it makes a menu item)  in /usr/bin named gedit

( this with Gdebi on 9.10, don't think earlier versions let you browwse the .deb as much

---

### Post by knurledflanges on 2010-01-17
mc4man, thanks so much for your detailed help!

---

