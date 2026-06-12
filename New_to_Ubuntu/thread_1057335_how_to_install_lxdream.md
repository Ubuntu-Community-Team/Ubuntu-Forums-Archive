---
title: "how to install lxdream"
date: 2009-02-01
forum: New to Ubuntu
---

### Post by philipballew on 2009-02-01
i want to install a dreamcast emulator for ubuntu 8.10. i looked at lxdream-0.8.3 and downloaded lxdream-0.8.3.tar.gz but i need step by step instructions installing it. i opened up the termanl and pan the shell script but nothing. please help!!!!1

---

### Post by Partyboi2 on 2009-02-01
Open a terminal and install build-essential if you have not already
```
sudo apt-get install build-essential
```  then change directory to where you downloaded the lxdream-0.8.3file to, so if its to your Desktop then
```
cd ~/Desktop
```then extract it
```
tar xvzf lxdream-0.8.3.tar.gz 
```then change into the newly create directory
```
cd lxdream-0.8.3/
```then 
```
./configure
``` If it finishes with no errors or does not complain about any missing libraries you can go to the next stage which is to run make
```
make
```If that finishes with no errors then you can install with
```
sudo make install
```

---

### Post by philipballew on 2009-02-01
it says 
No package 'gtk+-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GTK_CFLAGS
and GTK_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

then if i press make it says

philip@philip-desktop:~/Desktop/lxdream-0.8.3$ make
make: *** No targets specified and no makefile found.  Stop.

---

### Post by Partyboi2 on 2009-02-02
Open a terminal and install  libgtk2.0-dev, then run ./configure again
```
sudo apt-get install libgtk2.0-dev
```

---

### Post by philipballew on 2009-02-02
I did the "sudo make install" and then it finished and I don't know how to open it. its not in the menu. did i do Something wrong?

---

### Post by Partyboi2 on 2009-02-02
To launch type in the terminal
```
lxdream
```You can make a launcher by right clicking on your Desktop and selecting "Create Launcher"
and add
Name: lxdream
Command: lxdream
Comment: leave blank or add what ever

Or you can add it to your Applications Menu by going to Main Menu (System>Pref>Main Menu) and highlighting on the left the menu you want it under then selecting on the right "New Item" and filing in the details.

---

### Post by philipballew on 2009-02-02
i do that and it opens up but in the terminal and says: 

17:20:36 00000000 WARN  Unable to load file 'bios/dcboot.rom': No such file or directory
17:20:36 00000000 WARN  Unable to load file 'bios/dcflash.rom': No such file or directory

plus is there a way to have the program under app-games?

---

### Post by Partyboi2 on 2009-02-02
To add it to games go  to Main Menu (System>Pref>Main Menu) and click on the left "games" then selecting on the right "New Item" and fill in the details like this:
Name: lxdream
Command: lxdream
Comment: leave blank or add what ever

>  17:20:36 00000000 WARN  Unable to load file 'bios/dcboot.rom': No such file or directory Is probably only a warning, I notice you can go to Settings>Path and can change bios rom location. Not sure what you would set it to though.

---

### Post by philipballew on 2009-02-02
soeey to other you one more time, but is there a way to give it a different picture or icon in the menu?

---

### Post by Partyboi2 on 2009-02-02
After you have clicked on "New Item" you will see a icon on the left click on it and choose the icon you want. 
See screenshot below.

---

### Post by Malik on 2009-08-29
No program is loaded, and no BIOS is configured (required to boot a CD image). To continue, either load a binary program, or set the path to your BIOS file in the Path Preferences

I get that when i try to load the shenmue .cdi file. Any help?

---

