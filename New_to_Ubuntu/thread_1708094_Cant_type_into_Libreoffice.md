---
title: "Cant type into Libreoffice"
date: 2011-03-16
forum: New to Ubuntu
---

### Post by Falc7 on 2011-03-16
I was playing around trying to get chinese input ibus working on my computer, but whatever i did seems to have disabled any type of input into Libreoffice, as I cant type anything into Libreoffice anymore, what can i do?

---

### Post by Falc7 on 2011-03-16
edit

---

### Post by grahammechanical on 2011-03-16
I do not know if this will help but I have just gone on my machine to System>Preferences>Keyboard Input Methods. The IBUS preferences utility loads and under the Advanced tab there is a tick box called Use System Keyboard Layout. This is ticked on my machine but the next box Share the same input method among all applications is not ticked. I am not having problems typing in OpenOffice.

Regards.

---

### Post by Falc7 on 2011-03-16
I am using Kubuntu, i don't think i have that menu

---

### Post by Falc7 on 2011-03-21
bump

---

### Post by Zorael on 2011-03-21
First off, do you still want to get Chinese input to work, or do you just want to get back to normal again?

```
$ im-switch -s default-xim
```
Log out and back in.

---

### Post by Falc7 on 2011-03-24
Ah thats good now I can type into Libreoffice again.Yes please i would like to get chinese input to work

---

