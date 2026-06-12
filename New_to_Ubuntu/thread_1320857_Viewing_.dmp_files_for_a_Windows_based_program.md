---
title: "Viewing .dmp files for a Windows based program"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by The Gray Train on 2009-11-09
Hey, new user here (just threw off the shackles of Windows a couple days ago), and I decided to try out Wine v.1.0.1 to see if I could run the Windows game "Hired Guns: The Jagged Edge." Everything installed ok, and I declined installing Direct X as I read you are supposed to do. When opening the game menu, it pops right up, and the update link works fine. However, when I click play, a second bar at the bottom (signifying it's trying to open the actual game) pops up, then blinks away. Puzzled, I decided to go through the applications-wine-programs-hired guns tree to the quickstart file. When I click on that, the game actually starts to load and an animated intro screen starts to load (if i remember correctly it's a screen displaying the logo of one of the developers). Anyway, it runs for a few seconds then the program quits. I've also tried using winetricks and adding d3dx9, but no luck.

I went into the install location for the game to check the logs and view the .dmp files, but I can't view them. Is there an app or something I need to install in order to read them?

Any help would be appreciated.

---

### Post by lavinog on 2009-11-10
go to the folder using the terminal
```
cd ~/.wine/drive_c/Program\ Files/gamefolder
```
start the game in the terminal
```
wine programfile
```
replace gamefolder and programfile as required.

when the game exits you should get some info as to why it exited.

---

