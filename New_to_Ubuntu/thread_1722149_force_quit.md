---
title: "force quit"
date: 2011-04-05
forum: New to Ubuntu
---

### Post by ub9876 on 2011-04-05
can you set up force quit to act immediately  without confirming??

---

### Post by bodhi.zazen on 2011-04-05
You can from the command line:

```
kill -9 `pidof application_name`
```

You would need to use sudo for apps run / owned by system or other users.

---

### Post by spillage2 on 2011-04-05
Sure you can setup xKill as a keyboard shortcut ctrl+x if this is what you mean..

---

### Post by ub9876 on 2011-04-05
where is xkill?

---

### Post by spillage2 on 2011-04-05
just type in the terminal sudo xkill and your cursor will change to a x click on any frozen running application (firefox, or even desktop) and it will kill it.

Its a bit like alt+ctlr+del in wuzoft.

---

### Post by rosencrantz on 2011-04-05
KDE comes with default Ctrl+Alt+Esc as xkill shortcut. Not so sure about Gnome. You have to be careful where you click, though. As spillage2 mentions, clicking anywhere on your desktop  with xkill kills your desktop, which can be a bit awkward.

---

### Post by spillage2 on 2011-04-05
sorry should have pointed out that this is for gnome.

even clicking on you desktop will only reboot gdm.

a bit like sudo /etc/init.d/gdm restart.

---

