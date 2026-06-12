---
title: "I installed a .deb. How do I run it?"
date: 2009-07-15
forum: New to Ubuntu
---

### Post by Swerve1000 on 2009-07-15
Hi,

I installed a .deb file using the package manager, and believe everything installed fine.

There is no option for the program showing in my menus though.

How can I locate and run the .deb file?

Thanks for any help, it's most appreciated!

---

### Post by drs305 on 2009-07-15
To start it from the command line, you can probably find the run command by typing:
```

which <appname>

```
If you aren't sure of the complete name, type a few of the letters and hit TAB twice and it will give you completion options.

Since it was a .deb, you can also find it listed in Synaptic. The app's properties can also show you where the files are located, and the run command is often the exact name of the package in Synaptic (e.g. *firefox-3.5* )

---

### Post by Swerve1000 on 2009-07-15
Thanks drs305

That worked, it shows:

> /usr/bin/appname

How could I create a shortcut in my menus?

---

### Post by Paqman on 2009-07-15
> **Swerve1000 said:**
> 
How can I locate and run the .deb file?


On Linux you don't need to know the location to launch the app. For example, Firefox is located at /usr/bin/firefox, but the command to launch it is simply:
```

firefox

```

To add an app to the menus just right click on the Ubuntu icon top left and "edit menus".

---

### Post by 3rdalbum on 2009-07-15
> **Paqman said:**
> On Linux you don't need to know the location to launch the app. For example, Firefox is located at /usr/bin/firefox, but the command to launch it is simply:
```

firefox

```

To add an app to the menus just right click on the Ubuntu icon top left and "edit menus".

And when you are creating the launcher or the menu item, in the field marked "command" you can type the name of the program.

The above method for finding the actual name of the program, does not work if you don't know what the actual executable is called. My signature contains a link to a video that explains a different method, that always works.

Note too that when you get a program in a Debian package and it doesn't add itself to the menus, usually it means that it's a command-line program. Not always, but often.

---

### Post by Swerve1000 on 2009-07-15
Hey Paqman and 3rdalbum, I now have it working.

Thanks very much :)

---

### Post by drs305 on 2009-07-15
> **Swerve1000 said:**
> Thanks drs305

That worked, it shows:



How could I create a shortcut in my menus?

Right click on the Main Menu icon, Edit Menus (or in a terminal "alacarte"), select the Category in the left pane, and on the right side select New Item. Then enter a name, the run command (try it in terminal to make sure it works - the full path may or may not be necessary).

You can make a shortcut on the panel by right clicking, Add to Panel, and either selecting Application Launcher or Custom Application Launcher, depending on whether or not the app is listed in the menus.

---

