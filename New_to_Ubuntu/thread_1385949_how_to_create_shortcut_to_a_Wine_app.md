---
title: "how to create shortcut to a Wine app"
date: 2010-01-20
forum: New to Ubuntu
---

### Post by macli on 2010-01-20
Sorry - this is a stupid question. 
 
I've installed Wine and installed a simpel win32 game to test it (Duo card game from sourge forge). When I navigate to the /.wine folder and executes to dou.exe-file it works like a charm, but how do I create a shortcut to the file and place it on the desktop or menu. I can create a shortcut in the same folder as the exe and it works, but when i drag it to the desktop nothing happens when double clicking the shortcut.
 
Thanks,

---

### Post by John Bean on 2010-01-20
you should point to the wine executable rather than the exe, and pass the path of the exefile as an argument. The path can be a real linux path or a Windows path as seen from inside wine. As an example here's an example to launch Photoshop on my system:
```
wine "C:\Program Files\Adobe\Adobe Photoshop CS2\Photoshop.exe"
```

---

### Post by macli on 2010-01-20
That helped but i think i need to exeute wine "c:\..." from the correct folder - it throws an error (but executes now - thanks). in windows you can tell the shortcut to use a folder - is that possible?
 
Thanks

---

### Post by John Bean on 2010-01-20
Not sure I understand... do you mean the path to wine itself? If so that can be found by:
```
which wine
``` and is normally found in /usr/bin.

If you meant the correct folder from the app's point of view, you can use winepath to map real paths to Windows paths inside wine.

---

### Post by macli on 2010-01-20
I need to change folder to the app-folder and then execute wine "c:\....". Can I make a "bacth" file and then make a shortcut to that an place it on the desktop?

---

### Post by anaconda on 2010-01-20
I know what you mean!
here is a batch file for first changing the current directory, and then starting a program: (some programs need this to work correctly)
```

#!/bin/bash
cd "/home/anaconda/.wine/drive_c/Program Files/Death Rally/" && wine dr.exe

``` 

Just copy the above "code" on a text editor, change it to suit your needs (file paths and the name of the executable), and save it to your home-directory with eg name: launcher.sh
then make the launcher.sh executable with:
```
chmod a+x launcher.sh
```
and then you can make a desktop or panel launcher, that points to the "script"

---

### Post by Cabs21 on 2010-01-20
Def going to try writing a script like this so I can open uTorrent from my desktop.  It can be a pain when you Macro out key combos in compiz and they dont work (uTorrent).  Thanks

---

