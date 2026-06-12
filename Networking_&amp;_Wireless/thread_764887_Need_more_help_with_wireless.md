---
title: "Need more help with wireless"
date: 2008-04-24
forum: Networking &amp; Wireless
---

### Post by lakelovers on 2008-04-24
About four weeks ago I asked for help with my wife's dell wireless connection. I got good direction but still have one hiccup. When the computer is shutdown and reopened, the wireless connection is not found and I have to activate ndiswrapper. That is a big nuisance. How can I get ndiswrapper to load on startup? Is there a start up script? Here's the thread addressing all the ndiswrapper info:

[http://ubuntuforums.org/showthread.php?t=735485](http://ubuntuforums.org/showthread.php?t=735485)

---

### Post by twright on 2008-04-24
all you need to do is type this in terminal
```
sudo -i
echo ndiswrapper >> /etc/modules
```

---

### Post by lakelovers on 2008-04-24
Thanks twright. . . but it didn't work, and I'm quite sure I entered the code correctly. I would appreciate more suggestions.

**Edit**
Well, obviously, I didn't enter the code correctly the first time. I tried it again and it worked perfectly. Thanks, so much.

---

### Post by prshah on 2008-04-24
> **lakelovers said:**
> can I get ndiswrapper to load on startup? Is there a start up script? Here's the thread addressing all the ndiswrapper info:


Either add the word "ndiswrapper" to your "/etc/modules" file, or add the phrase "modprobe ndiswrapper" to your "/etc/rc.local" file as the last but one line. (The last line _must_ be "exit 0" or you will never be able to log in.)

btw, you need to be "sudo" to access either file; eg.```
gksudo gedit /etc/modules
gksudo gedit /etc/rc.local
```

assuming you are using gnome ubuntu.

---

