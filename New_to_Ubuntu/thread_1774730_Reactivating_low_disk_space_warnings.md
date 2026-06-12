---
title: "Reactivating low disk space warnings?"
date: 2011-06-03
forum: New to Ubuntu
---

### Post by Skios on 2011-06-03
Topic title says it all really. I just got a low disk space warning in Ubuntu 10.10, and because I wasn't really paying attention I ticked the box that disables these warnings in the future. I've been searching all over for a way to activate these warnings again, and I haven't had any luck yet, so any help is appreciated. Thanks in advance.

---

### Post by matt_symes on 2011-06-03
Hi

Open a terminal and copy an paste into a terminal

```
gconftool-2 -g /apps/gnome_settings_daemon/plugins/housekeeping/active
```

If it returns a value of **false** copy and paste this.

```
gconftool-2 -s -t boolean /apps/gnome_settings_daemon/plugins/housekeeping/active true
```

Then reboot your PC.

Kind regards

---

### Post by Skios on 2011-06-03
Done, thanks :)

---

