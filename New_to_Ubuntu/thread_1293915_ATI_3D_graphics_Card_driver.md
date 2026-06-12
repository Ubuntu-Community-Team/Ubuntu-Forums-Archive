---
title: "ATI 3D graphics Card driver"
date: 2009-10-17
forum: New to Ubuntu
---

### Post by mosaabJ on 2009-10-17
Hello
I followed all the steps from the following Link "https://help.ubuntu.com/community/RadeonDriver" to use the Free, Open Source driver for my ATI, which should provide 2D and 3D acceleration in my video hardware, I think I followed all the steps successfully but I still can't see the 3D effects I am expecting when flipping between windows using Alt+Tab, even though I Restarted the X server, and by the way my graphics card is ATI Radeon X1650SE.

---

### Post by Darkwing-Duck on 2009-10-17
This worked on an older ATI card that I had. One thing that I found was that ATI and Linux don't like each other very much. Also, trying to get the effects to work on that card required me to setup XGL vice fglrx.
 
Anyway, here are the steps that worked for me. 
 
If you want the XGL layer then do the following... 

1. Try installing XGL extension for X. 


```
sudo apt-get install xserver-xgl
```

2. Then create a speacial XGL session, so that it doesn't mess up your computer completely.


```
sudo gedit /usr/bin/startxgl.sh
```

and paste this into the text editor:

[B]#!/bin/sh
Xgl :1 -nolisten tcp -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
exec gnome-session[/B]

Save the file, and make it executable by typing


```
sudo chmod +x /usr/bin/startxgl.sh
```

3. Add an entry to your GDM session list (in the login screen)


```
sudo gedit /usr/share/xsessions/xgl.desktop
```

and paste the following in the text file: 

[B][Desktop Entry]
Encoding=UTF-8
Name=Xgl
Comment=Start an Xgl Session
Exec=/usr/bin/startxgl.sh
Icon=
Type=Application[/B] 

4 Restart X.

---

### Post by mosaabJ on 2009-11-06
> **Darkwing-Duck said:**
> This worked on an older ATI card that I had. One thing that I found was that ATI and Linux don't like each other very much. Also, trying to get the effects to work on that card required me to setup XGL vice fglrx.
 
Anyway, here are the steps that worked for me. 
 
If you want the XGL layer then do the following... 

1. Try installing XGL extension for X. 


```
sudo apt-get install xserver-xgl
```

2. Then create a speacial XGL session, so that it doesn't mess up your computer completely.


```
sudo gedit /usr/bin/startxgl.sh
```

and paste this into the text editor:

[B]#!/bin/sh
Xgl :1 -nolisten tcp -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
exec gnome-session[/B]

Save the file, and make it executable by typing


```
sudo chmod +x /usr/bin/startxgl.sh
```

3. Add an entry to your GDM session list (in the login screen)


```
sudo gedit /usr/share/xsessions/xgl.desktop
```

and paste the following in the text file: 

[B][Desktop Entry]
Encoding=UTF-8
Name=Xgl
Comment=Start an Xgl Session
Exec=/usr/bin/startxgl.sh
Icon=
Type=Application[/B] 

4 Restart X.

[SIZE="5"]**[COLOR="DarkOrange"]I don't know why but this what I get when typing this first command:[/COLOR]**[/SIZE]
```
sudo apt-get install xserver-xgl
```
[SIZE="5"][COLOR="DarkOrange"]**This is what I get:**[/COLOR][/SIZE]
```
mosaab@mosaab-desktop:~$ sudo apt-get install xserver-xgl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xserver-xgl

```

---

### Post by 3rdalbum on 2009-11-06
Sorry... The above ibstructions given to you are ancient and not appropriate for today.

What graphics driver are you using, what is your card (the lspci command will tell you) and what happens if you run the 'compiz --replace' command?

---

### Post by mosaabJ on 2009-11-06
> **3rdalbum said:**
> Sorry... The above ibstructions given to you are ancient and not appropriate for today.

What graphics driver are you using, what is your card (the lspci command will tell you) and what happens if you run the 'compiz --replace' command?

My graphics card is ATI Radeon x1650se

---

### Post by Mark Phelps on 2009-11-06
> **mosaabJ said:**
> ... which should provide 2D and 3D acceleration in my video hardware, ...

If you do a "man radeon" in a terminal, you will see a lot of options that you can tweak to improve performance, since the open source driver provides SOME 3D acceleration, but nowhere near the level needed for modern, graphics-intensive games.

If you think the open source driver is going to provide the same degree of 3D acceleration as the former restricted driver, then you are in for a MAJOR disappointment!

---

### Post by mosaabJ on 2009-11-07
> **Mark Phelps said:**
> If you do a "man radeon" in a terminal, you will see a lot of options that you can tweak to improve performance, since the open source driver provides SOME 3D acceleration, but nowhere near the level needed for modern, graphics-intensive games.

If you think the open source driver is going to provide the same degree of 3D acceleration as the former restricted driver, then you are in for a MAJOR disappointment!
But what do I do if I want to change a certain setting after I knew what it is from "man radeon"

---

