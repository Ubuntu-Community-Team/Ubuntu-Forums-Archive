---
title: "KDE 4 Notifications?"
date: 2009-04-07
forum: New to Ubuntu
---

### Post by mjheagle8 on 2009-04-07
in gnome, i can use 'notify-send' to send a notification. 
how can i do this in kde?
thanks in advance for any and all help!

---

### Post by mrmagos on 2009-04-14
Try this:
```
kdialog --passivepopup <text> --title <title> <timeout>
```
Title and timeout are optional.

---

