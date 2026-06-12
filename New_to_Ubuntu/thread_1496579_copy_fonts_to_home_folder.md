---
title: "copy fonts to home folder"
date: 2010-05-29
forum: New to Ubuntu
---

### Post by bj218 on 2010-05-29
How do I copy my fonts to my home folder ie bill .fonts?

---

### Post by sandyd on 2010-05-29
> **bj218 said:**
> How do I copy my fonts to my home folder ie bill .fonts?
fonts are located in two places

SystemWide: /usr/share/fonts
User: /home/*username*/.fonts

To install the fonts only for you, open your home folder in nautilus, click view, check the "show hidden files" option. You can now see the ".fonts" folder, into which you can copy fonts to install them.

---

### Post by hok00age on 2010-05-29
Don't forget to run:
```
fc-cache -f -v
```
after copying fonts to get instant effect. :)

---

