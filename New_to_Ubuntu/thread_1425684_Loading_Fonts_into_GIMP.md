---
title: "Loading Fonts into GIMP"
date: 2010-03-09
forum: New to Ubuntu
---

### Post by MikesGuitar on 2010-03-09
I have problems loads fonts into GIMP. When I DL a font, I open it and then drag the correct file into the font folder (Edit->Pref-Folders-> Font). The font I add will stay there until I restart GIMP. There are several that I loaded in a similar way that DO stay, but only those few. What I need is SPECIFIC instructions that will guide me through the process of loading/installing the font so I can see if my method is wrong, or if there is a deeper issue with GIMP. Thanks people!

---

### Post by halitech on 2010-03-09
there are 2 thoughts on adding fonts to a linux system. You can add them to /usr/share/fonts or you can create a folder in your home folder called .fonts (the . is important to have) and place them there. Personally I perfer to have them in my home folder so I don't lose them during a reload but others prefer to have them in /usr/share/fonts. Its up to you.

---

### Post by MikesGuitar on 2010-03-09
When I try to drop my fonts into the usr/share/fonts folder it says that I do not have permission, as I do not have root access. Now what haha

---

### Post by halitech on 2010-03-09
to do anything outside your home folder you need to give yourself the right permissions. Press ALT + F2 and type in 
```
gksudo nautilus
```
this will open nautilus as root and allow you to copy the files where you want them.

[color="red"]Be *Very Careful* with this as you can royally mess your system if you do something you shouldn't do.[/color]

---

