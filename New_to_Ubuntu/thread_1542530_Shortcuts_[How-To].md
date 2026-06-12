---
title: "Shortcuts [How-To]"
date: 2010-07-30
forum: New to Ubuntu
---

### Post by Apostolique on 2010-07-30
Can anyone explain how to make a shortcut in Ubuntu? I remember in Windows, to make a shortcut all I had to do was point to the file and it would work. In Ubuntu, I saw that it was a launcher but I was not able to make it point to a file and make it execute when I double click that Launcher.

---

### Post by jtarin on 2010-07-30
In the launcher properties enter the name of the application then the command to launch the aplication. Most applications can be launched using only the name. You also change the icon from the same dialog. Sometimes when an application won't launch properly with name only....I use the menu editor to locate the application and see what other command parameters are involved.

---

### Post by Lootbox on 2010-07-30
For a shortcut to a folder, type into the terminal:
```
ln -s *original_path_name* *shortcut_name*
```
[http://www.nixtutor.com/freebsd/understanding-symbolic-links/](http://www.nixtutor.com/freebsd/understanding-symbolic-links/)

---

### Post by Apostolique on 2010-07-30
What would it be for a linux executable? Also, when I'm browsing the files in some of my folders using the terminal, some of the files don't have any extensions, how do I know how to make a working shortcut in order to be able to execute them?

---

### Post by p.s. on 2010-07-30
If the file is already executable, I think the name should usually suffice. Try looking at the properties of other launchers to see how they're formatted.

---

### Post by theozzlives on 2010-07-30
You can create launchers to programs, websites, etc. You can put them on your desktop, panel, wherever. Ubuntu is a lot more flexible than Windows.

---

### Post by Apostolique on 2010-07-30
> **theozzlives said:**
> You can create launchers to programs, websites, etc. You can put them on your desktop, panel, wherever. Ubuntu is a lot more flexible than Windows.

I wonder if it would be possible to have the option to right click a file and be able to select shortcut.


Edit: I saw that there was the create a link button, but as soon as I move that file to an other directory, the link doesn't work anymore.

---

### Post by jtarin on 2010-07-30
Lets take this one situation at a time. First give us a shortcut you would like to make. Where would you like it to be and what application is it?

---

### Post by Apostolique on 2010-07-30
> **jtarin said:**
> Lets take this one situation at a time. First give us a shortcut you would like to make. Where would you like it to be and what application is it?

Let's see. I have a game called Christmas Eve Crisis. In it's folder, there is a file called Game_Launcher. When I double click it, the game starts. When I try to make a launcher by only pointing to the name of that file, nothing happens.

---

### Post by jtarin on 2010-07-30
Drag and drop whatever you want linked while holding shift-ctrl. You will note that the move-arrow and the copy-plus become an infinity-loop on the icon when you do this--this is the symbol for link creation.
If this does not work you probably need to [make a "hard" link.]("http://www.cyberciti.biz/tips/understanding-unixlinux-symbolic-soft-and-hard-links.html")

---

### Post by Garudi on 2010-08-27
So i've got this command to launch Final Fantasy 7 using the terminal, which launches it perfectly. 

padsp wine ~/.wine/drive_c/Program\ Files/Square\ Soft\,\ Inc/Final\ Fantasy\ VII/Ficedula/FF7Music.exe

but I want to put this into a launcher icon for the desktop so I don't have to type it out every time. 

However I can't seem to make it work, nothing happens. Any ideas?

If I don't use this command sequence, Final Fantasy doesn't load up, or the sound messes up and lots of different things.

---

### Post by jtarin on 2010-08-27
Find your path in your /home/user/.wine directory
Tap ctrl-h to show the wine folder since its hidden by default.


If you want to manually build a shortcut for an exe file in wine use this and fix the username and program path parts.
Example:
```
env WINEPREFIX="/home/username/.wine" wine "C:\Program Files\program\program.exe
```

---

### Post by Garudi on 2010-08-29
That worked fine, thanks!

---

