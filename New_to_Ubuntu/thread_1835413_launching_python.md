---
title: "launching python"
date: 2011-08-29
forum: New to Ubuntu
---

### Post by bspymaster on 2011-08-29
I was wondering how I can create a python program that automatically runs in terminal when you double-click on the file. I was told elsewhere that you have to put
```
#!/usr/bin/env python
```
in the beginning of the code for it to work, but that still doesn't work. If I make it executable, I still have to tell it to open in terminal. Is there a way to do this?

---

### Post by HarrisonNapper on 2011-08-29
Not familiar with gnome, but have you tried right-click>Properties and see if there's an option for automatically running in a terminal? EDIT: I took my suggestion about gnome-terminal out because apart from the command being wrong, I do remember that this is an option when creating a launcher, so that's the way to go.

Cheers.

---

### Post by cgroza on 2011-08-29
When you mark the file as executable, you should be presented a dialog when double-clicking. It will ask you if you want to display the file, run it, or run it in terminal.

---

### Post by mcduck on 2011-08-29
> **bspymaster said:**
> I was wondering how I can create a python program that automatically runs in terminal when you double-click on the file. I was told elsewhere that you have to put
```
#!/usr/bin/env python
```
in the beginning of the code for it to work, but that still doesn't work. If I make it executable, I still have to tell it to open in terminal. Is there a way to do this?

You'll have to create a launcher (or a shell script) for your program to accomplish that.

You *can* get Nautilus to run the program when clicked, but it will run in the background (unless the program itself creates a graphical window or something).

---

### Post by bspymaster on 2011-08-29
Unfortunately, My program **is** the launcher :P

EDIT: cgroza: I don't want that, because the average user would click run (which doesn't work).

---

### Post by mcduck on 2011-08-29
> **bspymaster said:**
> Unfortunately, My program **is** the launcher :P

EDIT: cgroza: I don't want that, because the average user would click run (which doesn't work).

I mean a proper .desktop file, like the ones used for all your menu entries etc.

Using a launcher like that allows you to define that the program should be executed in a terminal. And you can also set an icon for it.

Alternatively you can just make a simple shell script to open a terminal and execute your program in it:

```
#!/bin/sh
gnome-terminal -x python /path/to/your/program.py
```

---

### Post by bspymaster on 2011-08-29
> **mcduck said:**
> I mean a proper .desktop file, like the ones used for all your menu entries etc.

Using a launcher like that allows you to define that the program should be executed in a terminal. And you can also set an icon for it.

Yes! This is what I want to do.
You can check out the project this is for at [https://launchpad.net/linlife]("https://launchpad.net/linlife")

---

### Post by mcduck on 2011-08-29
Looks like a neat project. And for that kind of stuff you'll definitely need to look at .desktop files at some point or other.

Anyway, a simple way to create a basic launcher in Gnome is to right-click on the desktop and select "Create Launcher". Set the type to "Application in Terminal", command to whatever command you use to start your program, and name, comment & icon as you wish.

This will create a basic .desktop file for you. Gnome will of course detect it and show it as a program launcher icon, using the values you set, instead of showing the .desktop text file. But if you check it in a terminal you'll see that it indeed is a .desktop file.

I haven't got much experience with more advanced .desktop files (apart from adding a few right-click menu options to some launchers for Unity), but I suppose you should get pretty far simply by looking at the .desktop files in /usr/share/applications.

---

### Post by bspymaster on 2011-08-29
Hmm... I'll experiment with this. In the meantime, are there any other ways to do something like this?

---

### Post by mcduck on 2011-08-29
> **bspymaster said:**
> Hmm... I'll experiment with this. In the meantime, are there any other ways to do something like this?

Apart from the shell script approach, not really. Unless the program itself launches the terminal, you'll always need some external file to do it for you as there is no file permission or any other filesystem-level parameter that would tell that the program should be started in a terminal (I don't really think that such approach would even make sense if one existed, as the whole idea of starting a program in a terminal emulator window is a desktop-specific situation, and the .desktop files *are* the way simplest to handle such things on desktops.)

Anyway, if you actually want to develop the project into something that normal users would use, you'll definitely need to create the .desktop file at some point or other. That's how you get the program to appear in the menus of various desktop environments, and to appear in Unity searches etc.

---

### Post by bspymaster on 2011-08-29
Ok. I'll try experimenting and I'll post here if I encounter any problems. Thanks!

---

