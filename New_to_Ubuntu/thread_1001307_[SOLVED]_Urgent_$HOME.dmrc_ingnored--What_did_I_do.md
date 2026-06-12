---
title: "[SOLVED] Urgent: $HOME/.dmrc ingnored--What did I do"
date: 2008-12-03
forum: New to Ubuntu
---

### Post by nakama85 on 2008-12-03
Hi when I boot My computer on startup I got a warning saying something like

Users $HOME/.dmrc file is being ignored......HOME dir must be owned by user.

I don't know what I did other than (sense last reboot) Mount an ISO Via command line,installed seamonkey then uninstalled it cause I did not like it (which for whatever reason is still there), installed realplayer, and did updates.

Please help.!!!

Ubuntu 8.10 i386 Up to date

---

### Post by unutbu on 2008-12-03
Perhaps try this first: [http://ubuntuforums.org/showthread.php?p=6208727](http://ubuntuforums.org/showthread.php?p=6208727)

---

### Post by iaculallad on 2008-12-03
On your terminal:

```
sudo chmod 644 ~/.dmrc
sudo chmod 700 ~
```

---

### Post by nakama85 on 2008-12-03
Thank you Thank you Thank you!!!!!!!!!):P:p:D

If I could hit the thanks button more than once for you guys I would

---

