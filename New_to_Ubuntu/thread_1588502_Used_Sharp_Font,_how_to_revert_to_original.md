---
title: "Used Sharp Font, how to revert to original ?"
date: 2010-10-05
forum: New to Ubuntu
---

### Post by Mobidoy on 2010-10-05
I have use the Ubuntu-10.04-Script and made it use the sharp font option in it. If I would like to revert back to Lucid-Lynx original font, how can I do it ?

Thanx

---

### Post by migs73 on 2010-10-05
Try right clicking on the desktop and select Change desktop theme. Then select the font tab. I think (not at my Ubuntu machine right now) there is a default option on it. If not check out the other fonts available.

Edit; If you meant you made the sub pixel smoothing or the like to sharp(?) then these options are there too.

---

### Post by fatality_uk on 2010-10-05
If you paste the following code into a terminal, it will revert your Desktop font:

```
gconftool-2 --set /apps/nautilus/preferences/desktop_font --type string "Sans 10"
```

---

