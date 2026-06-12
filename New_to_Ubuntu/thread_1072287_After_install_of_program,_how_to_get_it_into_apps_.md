---
title: "After install of program, how to get it into apps menu?"
date: 2009-02-17
forum: New to Ubuntu
---

### Post by Gelateria Punk on 2009-02-17
I opened synaptic and found a program (called lmms).  It seems I can ONLY open it from the terminal, and I'm wondering if there is a way to get the program into the apps menu.  It doesn't show up on the main menu, but I can (like I said) open the program from the terminal.  I read the sticky on this subject in full, but it left out this minor detail...

---

### Post by dzark on 2009-02-17
System->Preferences->Main Menu gives you access to a menu editor when you can then add a new item

---

### Post by x33a on 2009-02-17
if you recently installed it and haven't rebooted the computer since, it might be that the menus didn't get refreshed.

try killall gnome-panel.

and see if comes up in the menu.

if not, then you can create your own shortcut, from the menu as dzark said.

---

### Post by Gelateria Punk on 2009-02-17
I tried both ways, but I don't think I'm entering the correct code.  I am indicating in the main menu option that I would like to open an application from the terminal.  I put in a variety of commands next, but they all came up with the same error message; "had a problem initializing child", or something like that (in the terminal.  I have rebooted.

---

### Post by mc4man on 2009-02-17
Couple of ways, this is pretty easy one (though I've never used ubuntu studio, should work

Create an new text file in home folder

Name it 

```
lmms.desktop
```

Run in terminal

```
gedit ~/lmms.desktop
```

Copy and paste this in 

> [Desktop Entry]
Name=Linux MultiMedia Studio
GenericName=music production suite
GenericName[ca]=Programari de producció musical
GenericName[de]=Software zur Musik-Produktion
Comment=easy music production for everyone!
Comment[ca]=Producció fàcil de música per a tothom!
Icon=/usr/share/lmms/themes/default/icon.png
Exec=/usr/bin/lmms
Terminal=false
Type=Application
Encoding=UTF-8
Categories=Application;AudioVideo;Qt
MimeType=application/x-lmms-project 

save, and then run this
```

cp ~/lmms.desktop  ~/.local/share/applications/
```

Afterwards you can delete the one you made in home folder

---

### Post by Gelateria Punk on 2009-02-17
Thanks, I'll try it

---

### Post by mc4man on 2009-02-17
Here's a thread on how to get latest lmms into hardy or intrepid, 3 ways
build - hardy or intrepid
a ppa - best for intrepid
a checkinstall .deb i uploaded - for hardy, must follow instructions for 3 preconditions (post #7

[http://ubuntuforums.org/showthread.php?t=1046909](http://ubuntuforums.org/showthread.php?t=1046909)

---

