---
title: "Missing Application"
date: 2011-04-15
forum: New to Ubuntu
---

### Post by OEG on 2011-04-15
I just installed WINE on my Linux computer and it is not showing up on  my applications tab at the top of my screen. I noticed this first when I  tried to open a new Microsoft Word document. I looked under 'Edit  Menus' but the program was not there.Then I tried opening a document  (.doc - Microsoft Word format) and it started up. I have tried  everything that I know, but I cannot figure this one out. :sad:

---

### Post by d3v1150m471c on 2011-04-15
Wine doesn't always update it's menu properly. If you dig around in the ~/.wine folder and find the executable you can edit the menu button and manually add it by creating the path under its properties.
ie:
```

wine "/home/$USER/.wine/dos_devices/Program Files/YourProgram/YourProgram.exe"

```

---

