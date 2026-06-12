---
title: "Using theme from .deb file"
date: 2009-06-14
forum: New to Ubuntu
---

### Post by mwilley on 2009-06-14
Okay, so I just got around to doing a full install of Ubuntu 9.04 a few days ago.  I found [this theme]("http://gnome-look.org/content/show.php/Shiki-Colors?content=86717") (with a gtx 2 theme, icons, and wallpapers) and downloaded a .deb file from it.  I opened it and it installed itself, but when I went to appearances it was not there.  I searched my folders and found the files in /usr/share/gdm/themes, but none of them were theme files so I could not install theme from Appearances.  How can I use this theme?

I'm guessing I'm just missing something very obvious, but this is all new to me.  Thank you in advance for putting up with noobish questions like these >_<

---

### Post by mikewhatever on 2009-06-14
Where did you find the deb file? What's wrong with the packages provided by the creator?

---

### Post by mwilley on 2009-06-14
The .deb file was from the creator.

---

### Post by mcduck on 2009-06-15
I assume you downloaded  the DEB package from the PPA repsoitory site? You should notice that there are several different packages listed there, arc-colors (GDM theme), shiki-colors and shiki-colors-murrine (GTK2, Metacity and XFWM themes) and gnome-colors (icon theme).

There is no single package that would install all these components, and if you got a GDM theme then you must have installed the GDM theme package.

GDM themes are for your login screen, and are selected in System/Administration/Login Window.

---

### Post by 3rdalbum on 2009-06-15
Did you click the "Customise" button in Appearances and see if it installed any items into the Controls or Window Borders?

---

