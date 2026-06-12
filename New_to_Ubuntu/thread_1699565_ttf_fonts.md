---
title: "ttf fonts"
date: 2011-03-03
forum: New to Ubuntu
---

### Post by hellomcfly on 2011-03-03
i'm trying to install some of my ttf fonts from windows in ubuntu, and i'm having trouble with a few. i have copied the .ttf files to /usr/share/fonts/truetype. some of them work fine. others will not show up in libreoffice at all. in gimp, the font name will be there, but the font itself is just a generic font and does not display properly. is this just because some ttf fonts don't work in ubuntu, or am i just installing them wrong?

---

### Post by Foxheadz on 2011-03-03
are you updating the font cache after installing them? also you can just double click on the .ttf and press install on the window that pops up.

---

### Post by Foxheadz on 2011-03-03
You can update the cache by running ```
fc-cache -rv
```

---

### Post by hellomcfly on 2011-03-03
worked - thank you!

---

