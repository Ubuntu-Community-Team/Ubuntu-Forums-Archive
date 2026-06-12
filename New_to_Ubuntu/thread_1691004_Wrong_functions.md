---
title: "Wrong functions"
date: 2011-02-19
forum: New to Ubuntu
---

### Post by PhilRogers34 on 2011-02-19
Ok, I seem to have some sort of glitch on my system,  everytime i try and open a folder using the places menu on the toolbar at the top of the screen,  i don't get a folder, instead banshee media player opens up.   I'm trying  places>pictures        places>videos      places>downloads etc etc, every single time banshee opens.  the only way i can browse my folders is to go Places>computer and then select the desired folder.

How can i sort this out so banshhe doesn't open and i get the desired folder?


2nd glitch.  Firefox

Sometimes when i click the firefox logo to open my browser it does nothing, i get a tab at the bottom of the screen saying 'opening firefox' but after a few seconds the tab disappears and i get nothing, i wait a minute or two and then try opening firfeox again only i get two firefox tabs and a message saying ' firefox is already running but not responding' and the force quit option,  so i have to shut both tabs and start firefox all over again, why is this happening and how do i rectify it?

thanks

---

### Post by cgroza on 2011-02-19
Right click on a folder, select Open With, select nautilus or file manager, make sure that the bottom box is check(something like "Remember this application for folders") and hit OK.

Try running firefox from command line and see if it spits errors.

```
firefox
```

---

### Post by PhilRogers34 on 2011-02-19
right clicking any folders on the 'places menu' just opens banshee as well.  all my music has decided to double up so every single song id on bashee twice as well now

---

### Post by Brad55 on 2011-02-19
Try opening up a terminal and type nautilus after you have a folder open right click on any folder and select Open with other Application. Now you can select the correct application to open folders. If you want it to always open with that application just make sure Remember this application is checked.

If you Ubuntu Tweaks installed you can correct your problem there. Once you start Ubuntu Tweaks look near the bottom under System for File Type Manager for each file you can select a program to open that file type, if you don't see the file type just uncheck the box by Only show filetypes with associated applications.

---

### Post by PhilRogers34 on 2011-02-22
Right, i have the folder issue sorted now, i changed the programme it opens with, thanks for that!

i typed firefox into the terminal and it just opened normally.  it's not every single time i try and use firefox that it plays up, it seems to just happen at random.



where can i get ubuntu tweaks from? i looked in the software centre but couldn't see anything.

Cheers

---

### Post by Frogs Hair on 2011-02-22
The link is for the stable .deb package and there is a PPA as well. [http://ubuntu-tweak.com](http://ubuntu-tweak.com)

---

