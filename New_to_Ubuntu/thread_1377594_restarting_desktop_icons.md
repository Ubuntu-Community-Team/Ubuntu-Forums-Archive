---
title: "restarting desktop icons"
date: 2010-01-10
forum: New to Ubuntu
---

### Post by taith on 2010-01-10
hello,

having an issue whenever [filebrowser] crashes, and im forced to end the application... that all the icons on my desktop vanish, i cannot right click on it it is mearly, a picture...

anyone know how to fix this without restarting the computer?

---

### Post by mac9416 on 2010-01-10
Hey, taith,

Hit <alt>+<f2>, enter 'nautilus', and hit <enter>.

---

### Post by taith on 2010-01-10
yes i can still get file browser up... but the desktop icons are gone... i can still operate the computer in most regards... its just incredibly anoying having to restart the compy for convenience...

---

### Post by mac9416 on 2010-01-10
Strange, that should have got the desktop icons back. Assuming Nautilus is handling the desktop. You're certain that didn't bring them back?

---

### Post by taith on 2010-01-10
positive...

---

### Post by mechro on 2010-01-10
Try...

**sudo killall nautilus**

**nautilus&**

ctrl c and exit Terminal to leave nautilus desktop running.

---

