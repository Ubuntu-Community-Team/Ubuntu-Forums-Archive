---
title: "Getting rid of Wine files after uninstalling windows progs."
date: 2008-12-31
forum: New to Ubuntu
---

### Post by adobrakic on 2008-12-31
I just uninstalled Soldat via Wine, but all of the Soldat files are still in my menu under Wine, is there a way to get rid of these?

---

### Post by wmoore on 2008-12-31
Right-click on your menu (Applications / Places / System) and choose Edit Menus. The rest should be self-explanatory.

---

### Post by adobrakic on 2008-12-31
Is there a way of getting rid of the files, instead of just hiding them?

---

### Post by wmoore on 2008-12-31
> **adobrakic said:**
> Is there a way of getting rid of the files, instead of just hiding them?Are you talking about the actual files now and not the Applications menu? Wine files are stored in ~/.wine/. If you're happy you have uninstalled the apps, you can just remove them from the terminal. So if Soldat is installed under the default location, you can run up a terminal and type something like:
```
rm -rf ~/.wine/drive_c/Program Files/Soldat
```

---

### Post by adobrakic on 2008-12-31
Nah, I meant the files under the Applications Menu. After uninstalling Soldat, all of it's files still stayed under the Applications Menu, however, they were not in the Wine folder at all.

I figured out they're stored in ~/.local/share/desktop-directories and ~/.local/share/applications/wine/Programs

Thanks for your help though!

---

