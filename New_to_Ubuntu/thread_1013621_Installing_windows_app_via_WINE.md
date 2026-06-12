---
title: "Installing windows app via WINE"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by tegnoto89 on 2008-12-17
If I want to use a windows application through wine, do I just install it to the default location and then add the application to wine?  Or do I have to install it with wine?  How would I do that?

---

### Post by Tatty on 2008-12-17
First check if it will run under wine at the appdb:
[http://appdb.winehq.org/](http://appdb.winehq.org/)

If you just double-click the installer file (which i assume will be either .exe or .msi) then it should be run automatically with wine.  If not you can simply run it from the command line:

```
wine <path to file>
```

---

### Post by adobrakic on 2008-12-17
When I used WINE, I would first check with the Wine AppDB to see how the prog works with the version of linux I have. Then if I wanted to install it, I'd right click the app and go to 'Open with Wine'. After I opened them like that, they would just install by themselves, exactly how they would on windows.

If you want Wine to be the default application to open .exes:
1. right click a .exe file
2. go to properties
3. go to 'open with' tab
4. select wine

from now on, all of your .exe files should automatically be opened with wine.

---

