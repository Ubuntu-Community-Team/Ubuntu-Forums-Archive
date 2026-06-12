---
title: "Location of Plasma Get new wallpapers"
date: 2010-01-22
forum: New to Ubuntu
---

### Post by proaditya on 2010-01-22
Hi

I just installed kde 4.3 on my ubuntu system.
Using the plasma desktop properties, i am able to "Get New Wallpapers". But where is it being stored? It is not in the default. I need add the folder list for screensavers.

Please help

Thank You
Aditya

---

### Post by jbruced on 2010-01-22
Needed that myself.

Go to terminal and type

find /home/yourusername/ -name filename.*


Obviously yourusername is replaced with your user name, and filename is the name of the wallpaper filename minus the extension. 

Hope it helps.

---

