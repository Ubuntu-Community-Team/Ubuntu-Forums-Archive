---
title: "Massive printer buffer: how do I delete the file?"
date: 2010-08-23
forum: New to Ubuntu
---

### Post by Isaacgallegos on 2010-08-23
_[COLOR="DarkRed"]I have a small hard drive and I tried to print a large 50 page document from the internet. During the process I ran out of harddrive space. Where is this file?[/COLOR]_ This caused me to have to use CTRL+ALT+F1 to use the terminal and delete some files so I could log-in (for some reason it wouldn't log in with sda1 at 100%...lol who knows why...) But I still cant find the file that the printer program made.

---

### Post by ubudog on 2010-08-23
See if it is in /tmp.  If not, search for it using:
```
locate nameoffile
```
(if you know the name)

---

