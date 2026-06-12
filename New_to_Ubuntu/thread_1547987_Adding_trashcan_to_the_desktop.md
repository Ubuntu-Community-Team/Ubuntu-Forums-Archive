---
title: "Adding trashcan to the desktop"
date: 2010-08-07
forum: New to Ubuntu
---

### Post by Norm24 on 2010-08-07
How on Earth do I do this?I can find it in file manager but I get no option to add to the desktop when I right click on it.In Ubuntu you can rightclick on it in the panel or use Ubuntu Tweak to add it to the desktop but no such option in Lubuntu.This is driving me nuts!

---

### Post by jimbop99 on 2010-08-07
Download "Ubuntu Tweak" (google is your friend). Very easy from there.

---

### Post by Norm24 on 2010-08-07
> **jimbop99 said:**
> Download "Ubuntu Tweak" (google is your friend). Very easy from there.

Please read my post again before responding.#-o

---

### Post by jimbop99 on 2010-08-07
> **Norm24 said:**
> Please read my post again before responding.#-o

Sorry

---

### Post by cavalier911 on 2010-08-07
The best I can come up with is a trash.desktop file that if placed in /usr/share/applications will create a menu shortcut for launching pcmanfm with the trash contents open and the same for the Desktop if placed in ~/Desktop When this is placed on the desktop it will have no right click empty option and drag/drop a file/folder into it will not put those items in the trash. This is one of the features you lose without the full gnome or kde desktop.

Copy/paste the code into your editor and save as trash.desktop

```
#!/usr/bin/env xdg-open
[Desktop Entry]
Version=1.0
Name=Trash
Comment=Browser
Exec=pcmanfm trash:///
Terminal=false
X-MultipleArgs=false
Type=Application
Icon=gnome-stock-trash.svg
Categories=Application;Desktop;Filemanager
MimeType=text/html;text/xml;application/xhtml+xml;application/xml;application/vnd.mozilla.xul+xml;application/rss+xml;application/rdf+xml;image/gif;image/jpeg;image/png;
StartupWMClass=Pcmanfm
StartupNotify=true
```

---

### Post by nulldozer on 2010-08-07
You can make a launcher on the desktop that points to **Trash:///**

If you don't know how to do this:
- Right click on the desktop, select "Create Launcher"
- Under "Type", select "Location"
- Name it whatever you want (trash makes the most sense)
- Under "Location", type **Trash:///**
- Change the icon while you still can

---

### Post by roger_1960 on 2010-08-07
Hi

Have spent a while trying in lubuntu and dont think its possible for drag & drop!.............

---

### Post by Norm24 on 2010-08-07
[QUOTE=nulldozer;9691384]You can make a launcher on the desktop that points to **Trash:///**

If you don't know how to do this:
- Right click on the desktop, select "Create Launcher"
[QUOTE]

No option for this in Lubuntu.

---

