---
title: "Menu help"
date: 2009-09-08
forum: New to Ubuntu
---

### Post by scared0o0rabbit on 2009-09-08
So I have a wine application that can only be launched by either right clicking in nautilus OR by going into the CLI and changing directory to the directory the program is in and running it.  If I try and run the program by typing /path/program from any other directory but the one the program is stored in, it will open and immediately close.  Is there a way I can automate this into a menu item?

I did write a little script that will change to the directory and then run the program, but if I try and point a menu item at that script though it doesn't seem to do anything.  There must be some way to do this?

---

### Post by lindsay7 on 2009-09-08
There are two easy ways to do this,

1.  Right click anywhere on the desktop and you can set up a launcher for this program.

2.  Right click on the Application on the top menu bar.  You can add this program to one of the menus under applications and click Edit menu.  Just play around with it,  You should be able to figure it out.

---

### Post by CatKiller on 2009-09-08
> **scared0o0rabbit said:**
> Is there a way I can automate this into a menu item?

Menu launchers (and launchers generally) are [.desktop files]("http://www.freedesktop.org/wiki/Specifications/desktop-entry-spec"). It's just a list of attributes that specify what that launcher represents; the syntax is pretty straightforward. The attribute that you're likely to be interested in is the *Path=* attribute. All you need to do is find the right .desktop file and edit it in a text editor so that it contains this attribute, with the value of the full path that you would normally *cd* to.

I believe Wine puts its .desktop files in ~/.local/share/applications/wine, although I don't have any Wine applications installed at the moment so I could be mistaken.

For some reason, Nautilus doesn't let you edit .desktop files directly, but if you open a text editor window you can drag-and-drop the file into the window to open it.

---

### Post by scared0o0rabbit on 2009-09-08
> **lindsay7 said:**
> There are two easy ways to do this,

1.  Right click anywhere on the desktop and you can set up a launcher for this program.

2.  Right click on the Application on the top menu bar.  You can add this program to one of the menus under applications and click Edit menu.  Just play around with it,  You should be able to figure it out.


That's just it though, the only two ways I have found to get the program to work is if I right click it in nautilus or I go into the program's directory and launch it while I'm in that directory in the CLI, if I try and launch the program through the CLI when I'm not in the program's directory it fails.  The same can be said for any other way I've tried to launch it.  If I just put the command into the menu it does the same thing as if I were to try and launch the program from the CLI while not being in the proper directory.  The program spits out a log file into whatever directory I'm in that is full of errors if I'm not in the directory when I launch it.

I guess what I really need is the ability to put something into the applications list that opens a CLI window, cd's to the program's directory, and runs the program, and then when I quit the game (or while the game is still playing as I haven't tried that) will close the CLI window.  Is there a way to set something like that up?  I was hoping creating a bash script that went to the folder and launched the application would accomplish this for me, but that will only work if I already have a CLI window open and then manually run the script.

---

### Post by scared0o0rabbit on 2009-09-08
> **CatKiller said:**
> Menu launchers (and launchers generally) are [.desktop files]("http://www.freedesktop.org/wiki/Specifications/desktop-entry-spec"). It's just a list of attributes that specify what that launcher represents; the syntax is pretty straightforward. The attribute that you're likely to be interested in is the *Path=* attribute. All you need to do is find the right .desktop file and edit it in a text editor so that it contains this attribute, with the value of the full path that you would normally *cd* to.

I believe Wine puts its .desktop files in ~/.local/share/applications/wine, although I don't have any Wine applications installed at the moment so I could be mistaken.

For some reason, Nautilus doesn't let you edit .desktop files directly, but if you open a text editor window you can drag-and-drop the file into the window to open it.

I'm not really sure what you're getting at here.  I found the .desktop files, however none of them seem to have anything about Path in them.  I tried in the CLI to add the directory that the program is installed in to the path and seeing if I could just run it that way, but that didn't change my outcome at all.  I think I actually have to be in the directory when it launches for it to work properly.

Edit: The program didn't install a group btw, it just went onto the hard drive and didn't try and automatically setup a link to run it in the Wine Group.

---

### Post by CatKiller on 2009-09-09
> **scared0o0rabbit said:**
> I'm not really sure what you're getting at here.  I found the .desktop files, however none of them seem to have anything about Path in them. 

That's correct; the defaults don't (since it's not a mandatory entry), and the Launcher Properties tool is quite limited in what it will let you adjust. That's why you need to adjust it with a text editor.

> 
Edit: The program didn't install a group btw, it just went onto the hard drive and didn't try and automatically setup a link to run it in the Wine Group.Ah. Didn't realise. In which case, you need to create the .desktop file before you can adjust it. You can right-click on the Desktop and select Create Launcher, in which case the .desktop file will be in ~/Desktop, or you can add it to the menu, in which case it will be in ~/.local/share/applications, or you can add it to the panel, in which case it will be in ~/.gnome2/panel2.d/default/launchers.

Call it whatever you want, set the icon to be whatever you want, and set the command to be whichever command you'd use if you were in the correct directory. Then edit it to add a line that says ```
Path=/full/path/to/program
```

---

### Post by scared0o0rabbit on 2009-09-09
So I made a launcher on the desktop and added the path and it worked, so that's obviously a step in the right direction?  Where are the .desktop files for the rest of the applications list besides wine?  All that's in ~/.local/share/applications are my wine applications and I'd really rather add the link to one of the other sections.

---

### Post by CatKiller on 2009-09-09
> **scared0o0rabbit said:**
> So I made a launcher on the desktop and added the path and it worked, so that's obviously a step in the right direction?  Where are the .desktop files for the rest of the applications list besides wine?  All that's in ~/.local/share/applications are my wine applications and I'd really rather add the link to one of the other sections.

If you modify any of the existing menu entries, or create a new one, it will be just for that user and kept in ~/.local/share/applications.

System-wide entries are in /usr/share/applications.

Glad it worked.

---

### Post by lindsay7 on 2009-09-09
Right click on Applications and pick edit menu. Click on properties and you can find the path for the start up.  Here is a screen shot for an example.

[ATTACH]128022[/ATTACH]

---

### Post by scared0o0rabbit on 2009-09-09
is there a reason why instead of naming the .desktop file something meaningful it instead names it alacarte-made-1.desktop etc?  I think that's what threw me off.

---

