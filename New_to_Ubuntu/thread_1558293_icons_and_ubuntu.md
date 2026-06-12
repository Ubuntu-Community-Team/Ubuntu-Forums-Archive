---
title: "icons and ubuntu"
date: 2010-08-22
forum: New to Ubuntu
---

### Post by mushypeas on 2010-08-22
I have recently converted to ubuntu from windows

I have downloaded the chess software 'scid' but there are no icons. I can type in scid to the terminal but would like icons for my downloaded software. Any way of doing this please?

Thanks

---

### Post by dagdeniz on 2010-08-22
Well, many of the applications for x and any of the cli applications are not listed in the menus by default. You can edit menus and activate Debian menus (I think scid will be there) or create a desktop entry for the application: 

```
[Desktop Entry]
Name=Scid
Exec=scid
Terminal=true
Type=Application
Icon=application-x-executable
```
save as scid.desktop and exit. 

You may need to change "Terminal=true" to false. I hope these help.

---

### Post by mushypeas on 2010-08-22
> **dagdeniz said:**
> Well, many of the applications for x and any of the cli applications are not listed in the menus by default. You can edit menus and activate Debian menus (I think scid will be there) or create a desktop entry for the application: 

```
[Desktop Entry]
Name=Scid
Exec=scid
Terminal=true
Type=Application
Icon=application-x-executable
```save as scid.desktop and exit. 

You may need to change "Terminal=true" to false. I hope these help.

Thanks; how do I activate debian menus or edit menus.  Sorry, I am very new

---

### Post by dagdeniz on 2010-08-22
right click on the main menu, click "edit menus" or something like that, or better way press Alt+F2 write "alacarte" without quotes and press enter. there should be a "debian" group in the menus which is not ticked. You can tick it and its submenus.

---

