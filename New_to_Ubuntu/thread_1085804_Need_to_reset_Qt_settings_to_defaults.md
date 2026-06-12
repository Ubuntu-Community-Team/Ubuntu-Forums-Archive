---
title: "Need to reset Qt settings to defaults"
date: 2009-03-03
forum: New to Ubuntu
---

### Post by zorblek on 2009-03-03
I've been using Ubuntu Intrepid, and I decided that I wanted to give Kubuntu a try, so I installed kubuntu-desktop. I decided it wasn't for me, so I uninstalled KDE and am back to Gnome. However, while I was using KDE I experimented with the appearance settings. I have a few Qt-based apps (Opera, launchy, etc.) and their color settings have stayed the same, making them very difficult to read in Gnome. Is there some way I can reset Qt to its default settings?

---

### Post by zorblek on 2009-03-05
Can anyone help me with this? I would really appreciate any suggestions...

---

### Post by snova on 2009-03-05
I can think of a few places Qt might store settings.

~/.qt/
~/.config/Trolltech/
~/.config/Trolltech.conf

Try removing those files/directories.

---

### Post by zorblek on 2009-03-06
That did the trick! I had to restart for the changes to take hold in some programs, but everything is back to normal now. Thanks!

---

