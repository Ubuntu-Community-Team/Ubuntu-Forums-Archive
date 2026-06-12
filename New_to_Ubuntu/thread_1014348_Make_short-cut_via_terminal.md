---
title: "Make short-cut via terminal"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by linuxguymarshall on 2008-12-17
How can I make a shortcut to a program via the terminal. Pretty simple. So what is the command?

---

### Post by Dr Small on 2008-12-17
alias.

Example:
```
alias :q="exit"
```

But next time you open the terminal, the alias is gone. I add aliases to .bash_aliases and for you ubunteros, just uncomment the section that refers to .bash_aliases in .bashrc ;)

---

### Post by Bakerconspiracy on 2008-12-17
Do you mean gui shortcut or like shorthand for a command, like previously mentioned?

---

### Post by linuxguymarshall on 2008-12-17
I think I did not convey that message well. I want to create a shortcut on the desktop via a terminal so I can click on it via the GUI later.

---

### Post by -grubby on 2008-12-17
> **linuxguymarshall said:**
> I think I did not convey that message well. I want to create a shortcut on the desktop via a terminal so I can click on it via the GUI later.

```

ln -s shortcut ~/Desktop/shortcut_name

```

---

### Post by linuxguymarshall on 2008-12-17
> **nathangrubb said:**
> ```

ln -s shortcut ~/Desktop/shortcut_name

```


Can I set the icon from that command?

---

### Post by handydan918 on 2008-12-17
Soundls like the hard way to do it, but...


```
touch home/username/Desktop/desktopbutton 
```

```
gedit home/username/Desktop/desktopbutton
```

in gedit, do 
```
#!/bin/bash
/absolutepath/to/executable
```

Then

```
chmod a+x /home/username/Desktop/desktopbutton
```


:lolflag:
But WHY?!

---

### Post by jerome1232 on 2008-12-17
Or do you mean a Desktop launcher?

Basically you would create a .desktop file and hand write it's contents, now i'm not sure of the syntax for .desktop files but this is what my google earth shortcut looks like maybe you can gleen from that what you need.

```
vim Desktop/shortcut.desktop


##### this is the contents of my desktop launcher for google earth
[Desktop Entry]
Encoding=UTF-8
Name=Google Earth
GenericName=3D planet viewer
Comment=Explore, search and discover the planet
Exec=/opt/google-earth//googleearth %f
Terminal=false
MultipleArgs=false
Type=Application
Icon=/opt/google-earth//googleearth-icon.png
Categories=Application;Network
MimeType=application/vnd.google-earth.kml+xml;application/vnd.google-earth.kmz;application/earthviewer;application/keyhole

```

---

