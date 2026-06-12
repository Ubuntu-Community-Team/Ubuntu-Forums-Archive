---
title: "Rhythmbox appears twice ( 2x ) in Sound &amp; Video menu"
date: 2011-03-10
forum: New to Ubuntu
---

### Post by hugstable on 2011-03-10
In Maverick, under the System>Preferences>Main Menu, the Sound & Video entry has two listings in the Items list for Rhythmbox Music Player. The only difference I can see is that the first entry has "rhythmbox %U" in the 'Command:' textbox of the Properties window, while the second has "rhythmbox-client --select-source %U".

Does anyone know the reason for these two different entries? Thanks for reading, Hugs.

---

### Post by Krytarik on 2011-03-11
I only have the first one. Check in "~/.local/share/applications" if there is another, custom, Rhythmbox desktop file. If so, remove it.

---

