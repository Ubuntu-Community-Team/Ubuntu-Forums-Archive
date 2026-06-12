---
title: "Built Wine but where did it go?"
date: 2011-05-13
forum: New to Ubuntu
---

### Post by Haur on 2011-05-13
Hi guys and gals.

So i'm a total noob but am hoping to graduate someday. Anyways i built the latest version of wine and applied a custom patch to it, the mouse was slow in games thats why i needed the patch. Everything went well and i don't think i got any show stopping errors in the build process but there is one problem, how do i run or find the Wine executable?

Unity can't find it, Gnome Do can't find it and I can't either :confused:

Little sidenote, i compiled the latest version of Transmission using info from these forums and that worked straight after, maybe the difference is when i compiled Wine i only did 
```

./configure
make
sudo make install

```But there was way more to it when i did Transmission

---

### Post by JDShu on 2011-05-13
in the console run:

```

wine

```

and it should start up

---

### Post by stoneage on 2011-05-13
```
whereis wine
``` should tell you where it installed to.

---

### Post by LowSky on 2011-05-13
To run wine config this is the command from terminal...

```
winecfg
```

---

### Post by kroq-gar78 on 2011-05-13
> **stoneage said:**
> ```
whereis wine
``` should tell you where it installed to.
shouldn't it be 
```
which wine
``` or are they the same? Also, I suggest using checkinstall. It uses packages to compile to a .deb file so you can install it anywhere that as the same ubuntu version and architecture (32bits or 64bits). I just like it better than "sudo make install"

---

### Post by deconstrained on 2011-05-13
The output of make install probably told you where it is. If "which wine" doesn't give you anything, the path it installed to isn't in your $PATH environment variable. To find it you could try running "find /usr/local -name '*wine' "

---

### Post by LinuxNo0b445 on 2011-05-13
when trying to open up the game or whatever, it says "open with" and then click other applications and Wine should be right at the bottom

---

### Post by Haur on 2011-05-14
Running ```
wine
``` from the console works but there is no gui just output to the terminal. Running ```
whereiswine
``` gives me wine: /usr/local/bin/wine /usr/local/lib/wine. ```
whichwine
``` gives me /usr/local/bin/wine. ```
Winecfg
``` worked but asked me to install some gecko or gekko stuff and i did. 

The open with app thing works but there is one problem, "winebrowser" is listed three times, "wine core exe" is listed six times and then "wine program loader" is listed just once, which i guess is fine.

Then again i still can't run for example winecfg without the terminal.

I will try using checkinstall in the future, it sounds pretty neat.

---

### Post by grahammechanical on 2011-05-14
I had wine and one windows program already installed when I upgrade to 11.04 and Unity. Wine and my windows program are there in the Dash. They are in the list of installed applications. This is what I see and you should see something similar.

1) an icon labeled Configure wine, 2) an icon labeled Uninstall Wine software (By the way it has a button that you use to install software using wine. Perhaps this is what you are looking for). 3) an icon labeled winetricks (you will not see that if you have not installed winetricks). I also see an icon for the Windows program, which still works.

You can also type winefile in a terminal and that will load a Windows Explorer type window where you can browse to the CD drive and select Setup.exe or Install.exe of the program you want to install. This works. I have installed Windows programs this way but I have not used the Add/Remove wine utility that is called Uninstall wine software for some reason. I have not use it because I did not know that you use an uninstall utility to install. It like using the Start menu to shutdown, I suppose.

Regards

---

### Post by frankbooth on 2011-05-14
> **Haur said:**
> Then again i still can't run for example winecfg without the terminal.

You can create menu entries if you want.

[http://www.ubuntugeek.com/howto-add-entries-in-gnome-menu.html](http://www.ubuntugeek.com/howto-add-entries-in-gnome-menu.html)

---

### Post by Haur on 2011-05-14
The "Dash" is the button in the top left corner that shows me all my apps and lets me search for them right? If i type in wine there or check installed apps it shows nothing.

Edit:
How does creating a menu entry work with unity. I tried making one in accessories but it didn't show up in the list of installed apps in the application tab when i right click on it and select accessories.

---

### Post by frankbooth on 2011-05-14
> **Haur said:**
> The "Dash" is the button in the top left corner that shows me all my apps and lets me search for them right? If i type in wine there or check installed apps it shows nothing.

Sorry for my previous answer, didn't see you were using Unity.
Try this:

**1)** create a file called winecfg.desktop (or whatever you want a shortcut to)
**2)** open it with your preferred text editor and write this (for example):
```

[Desktop Entry]
Name=Wine Config
Exec=winecfg
Icon=/add/a/path/to/icon/if/you/want
StartupNotify=true
Terminal=false
Type=Application
Categories=Wine

```
**3)** Place 'winecfg.desktop' in /usr/share/applications/
**4)** Relog and try the dash again, I'm *not* 100% sure it will work.

---

### Post by Haur on 2011-05-14
Yes that worked for me :) On a side not editing the main menu entries also seemed to have worked. Both show up in the dash search thingy now.

---

