---
title: "Desktop link works only in terminal"
date: 2009-05-24
forum: New to Ubuntu
---

### Post by ubuntu1sttimer on 2009-05-24
Built a box for a friend to try out Ubuntu and the net. Being in the country he has to use dial up. Installed wvdial which works fine from the terminal. Put a link on the desktop so he could just click it there. 

Clicking the link does not work. No error message, just nothing happens. If I go into terminal  and run "me@linux1:~/Desktop$ wvdial" it works. Don't know if it is via the link or running wvdial dorectly.

Anyone have an idea how I can do it via clicking on the desktop?

---

### Post by ubuntu1sttimer on 2009-05-24
Bump

---

### Post by hullap on 2009-05-25
i dont actually use wvdial, but heres a guess
make a file called wvdial.desktop on your desktop which has
```
[Desktop Entry]
Type=Application
Name=wvdial
Icon=wvdial
Exec=/usr/bin/wvdial
Terminal=false
```
;)
thank you ad_267 :)

---

### Post by ad_267 on 2009-05-25
You probably also need to add a:

Exec=/path/to/executable/file

---

