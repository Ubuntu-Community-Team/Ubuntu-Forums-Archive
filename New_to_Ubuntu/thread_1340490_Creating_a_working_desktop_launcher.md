---
title: "Creating a working desktop launcher?"
date: 2009-11-28
forum: New to Ubuntu
---

### Post by ed-koala on 2009-11-28
I'm having an issue that I'm not certain what the cause is.

I'm trying to run a Wine game - Sins of a Solar Empire.  Running the game directly from the .wine directory using the Sins of a Solar Empire.exe file works fine.  When I try to create a desktop launcher pointing to the file, it crashes giving a mini dump error.  What is the difference between the launcher I created on my desktop and pointed directly to the file (and I added wine before it also) and just right clicking the file and choosing run using wine?  How can I get a working launcher on my desktop?

---

### Post by Virtual Liberty on 2009-11-28
```
wine "~/.wine/apps/application.exe"

```

** Change the path to your executable.

---

### Post by lvlo on 2009-11-28
Or:```
sh -c "cd PATH_TO_PROGRAM && wine PROGRAM.exe"
```

---

### Post by ed-koala on 2009-11-28
That does not work.  I found this [http://ubuntuforums.org/archive/index.php/t-1218513.html]("http://ubuntuforums.org/archive/index.php/t-1218513.html") but I'm having trouble making sense of it.

The file is in /home/ed/.wine/drive_c/Program Files/Stardock Games/Sins of a Solar Empire/Sins of a Solar Empire.exe

Can someone tell me step by step what to do to make a working desktop launcher after reading that link?

---

### Post by Virtual Liberty on 2009-11-28
```
env WINEPREFIX="/home/ed/.wine" wine "C:\Program Files\Stardock Games\Sins of a Solar Empire\Sins of a Solar Empire.exe" 

```

---

### Post by ed-koala on 2009-11-28
Again, those do not work, they crash with a mini dump error.  The thread listed gives the reasons, something about making a shell script, changing directories, etc, but the info in the thread is scattered and I'm not quite sure how to piece it together. They got it working though, so the solution is there, I just need it explained and laid out better to understand it.

Hopefully someone can read through that thread and lay it out for me, step by step with explanations.

---

### Post by tom.swartz07 on 2009-11-28
> **ed-koala said:**
> That does not work.  I found this [http://ubuntuforums.org/archive/index.php/t-1218513.html]("http://ubuntuforums.org/archive/index.php/t-1218513.html") but I'm having trouble making sense of it.

The file is in /home/ed/.wine/drive_c/Program Files/Stardock Games/Sins of a Solar Empire/Sins of a Solar Empire.exe

Can someone tell me step by step what to do to make a working desktop launcher after reading that link?

Use quotation marks ("") around the path. For some reason, launchers and terminal commands dont like spaces in the commands.

---

### Post by ed-koala on 2009-11-28
Ok, got it figured out by slowly going over that thread post by post and trying various things.  Seems wine, or the program, needs to actually be IN that directory to run the file.  So, the solution is to create a small bash script that changes to the directory, then runs the file.  Running it from another directory and specifying the path doesn't work.

I'll make a separate post with a "how to" on making wine desktop launchers, this info is very much needed I think!

---

### Post by alfu on 2009-12-17
I downloaded a program and the installer placed it in an "opt" subdirectory in the filesystem, and added its icon to the Applications menu under the Graphics submenu. 

Selecting its icon from this menu results in a "Could not launch application  Failed to change to directory '~' (No such file or directory)" error.

Doubleclicking on its executable in the filesystem/opt/VariCAD Viewer/bin/ directory launches the program satisfactorily from where it installed, but moving it into the usr directory resulted in an unfound file error crash so I moved it back, restoring its original function.

**[COLOR="Red"]I have created two launcher icons, one works, the other does not.  The Launcher Properties dialog box for both are IDENTICAL.[/COLOR]**

**Working launcher**: dragged the executable icon from its listing window into the launcher bar.  This resulted in an icon of a platform with a spring under it.  Clicking the springy thingie works as expected, and its Command in the launcher is "/opt/VariCAD-View/bin/varicad-view".  I was finally able to change the icon to the custom one by pasting its path into the icon browser, so it works.

**Failed launcher**: Under the Applications menu, I right-clicked on the icon and selected "Add this launcher to panel".  This loads the custom icon ("/opt/VariCAD-View/desktop/x-varicadview.desktop") for the program in the launcher bar, with the Command as "varicad-view" that fails as above.  Changing the Command to "/opt/VariCAD-View/bin/varicad-view" results in no change in the error situation.

I have looked at the Command lines from working apps in the launcher bar, but there is no discernable similarity among them.  Firefox, for example is "firefox %u" whereas the Help is just "yelp", Evolution contains a modifier: "evolution --component=mail".

---

