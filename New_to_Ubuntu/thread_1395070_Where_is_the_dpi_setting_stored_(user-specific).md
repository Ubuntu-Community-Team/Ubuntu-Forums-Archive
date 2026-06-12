---
title: "Where is the dpi setting stored (user-specific)?"
date: 2010-01-31
forum: New to Ubuntu
---

### Post by RobHK on 2010-01-31
I was messing about with my dpi setting in gconf-editor and accidentally set it so small that I can't see the characters. Catch-22: this means I can't see to reset the dpi, and I'm not familiar enough with it to do it blind.

I logged out and into another user desktop and everything there is fine, so this is user specific. Can someone tell me where the value is stored? Then maybe I can get in to change it from this other desktop.

Any help much appreciated.

---

### Post by J V on 2010-01-31
~/.gconf

---

### Post by RobHK on 2010-01-31
> **J V said:**
> ~/.gconf

Thanks very much.

I'm in Windows at the moment so I can't look now. Do I take it that "~" means my /home/username directory?

---

### Post by mcduck on 2010-01-31
Yes, ~/ is same as your home directory.

Anyway, you can use gconftool-2 to set the dpi value back to default, so no need to edit gconf files by hand...

```
gconftool-2 --type int --set /desktop/gnome/font_rendering/dpi "96"
```

---

### Post by Pedric on 2010-01-31
You can run this command to set the dpi:

```
gconftool-2 -s --type float /desktop/gnome/font_rendering/dpi 96
```

---

### Post by RobHK on 2010-01-31
> **Pedric said:**
> You can run this command to set the dpi:

```
gconftool-2 -s --type float /desktop/gnome/font_rendering/dpi 96
```

Thanks to both Pedric and McDuck, who posted similar information. 

I'd have to do this from another user desktop as I can't use the terminal in the problem one because of the font issue. But presumably I can just navigate there in a terminal from the other user desktop. 

Thanks again. I'll give it a try shortly. For the moment I'm still in Windows.

---

### Post by Pedric on 2010-01-31
You'll have to run this as the user that has the messed up configuration, simply press Ctrl-Alt-F1 before logon, login there, run the command and press Alt-F7 to return to the logon (GDM) screen, then logon as usual.

---

### Post by falconindy on 2010-01-31
Actually, you don't. You can use sudo to do it from any user who's a member of the admin group.

```
sudo -u afflicteduser gconftool-2 .....
```

---

### Post by RobHK on 2010-01-31
> **mcduck said:**
> Yes, ~/ is same as your home directory.

Anyway, you can use gconftool-2 to set the dpi value back to default, so no need to edit gconf files by hand...

```
gconftool-2 --type int --set /desktop/gnome/font_rendering/dpi "96"
```

Thanks McDuck. I used your suggestion and all is now well.

Thanks to the others for your suggestions too. :)

---

