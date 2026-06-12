---
title: "How do I install a TrueType Font from my desktop"
date: 2010-08-12
forum: New to Ubuntu
---

### Post by Spacestationmax on 2010-08-12
I downloaded a ttf file to my desktop.  I searched other TTF files but am unable to copy into it with gui

How do I install LokiCola.ttf from my desktop?

---

### Post by Bachstelze on 2010-08-12
Basically, you need to copy the font file either to ~/.fonts if you want to install the font just for yourself, or to /usr/share/fonts if you want it to be available to all users on the system.  I'm quite surprised Gnome doesn't have An App For That&#8482;, KDE does... You can always use the terminal, though.

---

### Post by Spacestationmax on 2010-08-12
max@EeePC901:~/Desktop$ sudo cp *.ttf /usr/share/fonts

Worked for me

---

### Post by MockY on 2010-08-12
I thought you could just double click the file, and then click Install once it is opened.

---

