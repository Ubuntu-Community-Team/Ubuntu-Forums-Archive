---
title: "wine programs gone"
date: 2009-06-09
forum: New to Ubuntu
---

### Post by cooljeff3000 on 2009-06-09
somehow while trying to use [http://linux.wareseeker.com/System/directx-support-for-wine-2005-06-13.zip/332299](http://linux.wareseeker.com/System/directx-support-for-wine-2005-06-13.zip/332299), all the programs I had on wine completely dissapeared. nothing is left but internet explorer. I use wine 1.1.23. help?

---

### Post by whoop on 2009-06-09
are the just gone from your main menu or are the files actually missing from ~/.wine ?

---

### Post by Bölvaður on 2009-06-09
**DirectX support for Wine 2005-06-13 **

That is seriously outdated and probably have been fixed long ago.
I wouldn't recommend downloading random programs.. but alright lets find your wine directory.


open up your terminal (Applications &#8594; Accessories &#8594; Terminal)

copy and paste this (you paste with ctrl+SHIFT+v or right click paste in the gnome-terminal):

```
cd / && locate wine
```

look at the list and it should give you an idea where your wine directory is

it should be named:

.wine

with a dot at front (meaning it is a hidden file)

---

### Post by cooljeff3000 on 2009-06-09
No, I mean ~/.wine/windows/program\ files is empty but for internet explorer and "common files"

---

### Post by cooljeff3000 on 2009-06-10
I mean ~/.wine/drive_c/Program\ Files/

---

