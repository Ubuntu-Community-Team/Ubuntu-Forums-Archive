---
title: "shortcut, with program using wine + terminal?"
date: 2010-02-28
forum: New to Ubuntu
---

### Post by AlNaimi on 2010-02-28
Hi every one...
How could i make a shortcut for this commend:
WINEDLLOVERRIDES="GDIPLUS.DLL=n" wine "/home/####/.wine/dosdevices/c:/Program Files/Portable Offline Browser/POB.exe"
So, the terminal work background...
Thanks

---

### Post by asmoore82 on 2010-02-28
use the `env` command in the launcher ...

```
env WINEDLLOVERRIDES="GDIPLUS.DLL=n" wine "C:\\Program Files\\Portable Offline Browser\\POB.exe"
```

I have the game "Burger Shop" in its own wine container and the launcher looks like this...

```
**asmoore@lucid-laptop:Desktop$** cat "Burger Shop.desktop"
#!/usr/bin/env xdg-open

[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Icon[en_US]=/home/asmoore/.wine-subs/drive_c/Program Files/Burger Shop/BurgerShop.png
Exec=env WINEDEBUG="-all" WINEPREFIX="/home/asmoore/.wine-subs" wine "C:\\Program Files\\Burger Shop\\BurgerShop.exe"
Name[en_US]=Burger Shop
Name=Burger Shop
Icon=/home/asmoore/.wine-subs/drive_c/Program Files/Burger Shop/BurgerShop.png
```

---

### Post by undecim on 2010-02-28
Using this as the shortcut command should do what you want:
```
gnome-terminal -x bash -c "WINEDLLOVERRIDES=\"GDIPLUS.DLL=n\" wine \"/home/####/.wine/dosdevices/c:/Program Files/Portable Offline Browser/POB.exe\"
```

and, if you want to be able to read output after the command closes, try
```
gnome-terminal -x bash -c "WINEDLLOVERRIDES=\"GDIPLUS.DLL=n\" wine \"/home/####/.wine/dosdevices/c:/Program Files/Portable Offline Browser/POB.exe\"; read
```

---

### Post by AlNaimi on 2010-02-28
Thanks guys very much :D
asmoore82 + undecim
           :popcorn:

---

