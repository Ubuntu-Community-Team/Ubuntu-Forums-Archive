---
title: "Google Gadgets GTK stopped working"
date: 2010-01-30
forum: New to Ubuntu
---

### Post by doctorj on 2010-01-30
I am running Kubuntu 9.10. I did have Google Gadgets going but then when I restarted my machine for some reason Google Gadgets does not start when selected from the menu. It seems to be loading and then it just stops - nothing. What is going on? How can I fix it?

---

### Post by NightwishFan on 2010-01-30
I believe there is a QT/KDE package for Google Gadgets for Kubuntu users. Try running the Google Gadgets from the terminal to see any debug messages.. I am not sure what the command is, try looking for it with:
```
apropos google
```

---

### Post by doctorj on 2010-01-30
I tried that and get a return message of :

ggl-gtk (7)

What does that mean?

---

### Post by NightwishFan on 2010-01-30
That is likely the command to run Google Gadgets. Try opening a terminal and running:
```
ggl-gtk
```

Post the output here surrounded by code or quote tags.

---

### Post by doctorj on 2010-01-30
I get the answer of:

```
Not a regular file: /
Not a regular file: /
Not a regular file: /
Not a regular file: /
```

And Google Gadgets actually appeared when run from the terminal.

---

### Post by NightwishFan on 2010-01-30
Did you install using the package manager or manually from the internet? You can always try reinstalling or removing and trying the KDE/QT one. Both are in the Software Center.

---

### Post by doctorj on 2010-01-30
Strange as it may seem, after running Google Gadgets from the terminal, I can now run it from the menu. Don't know what happened but it now works.

---

### Post by NightwishFan on 2010-01-31
Perhaps it rewrote a config file, well enjoy! ;)

---

