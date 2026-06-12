---
title: "Get rid of GTK on server"
date: 2009-11-13
forum: New to Ubuntu
---

### Post by RichardCL on 2009-11-13
Dear Forum,

I just made a mistake and installed transmission instead of transmission-daemon on my headless server. As a result, I pulled all of the gnome/GTK dependancies.

Can I remove them simply by ```
apt-get remove transmission && apt-get autoremove
``` or is it time for a reinstall?

---

### Post by 3rdalbum on 2009-11-13
That command should work, because the Gnome/GTK packages will now be "orphaned".

---

### Post by RichardCL on 2009-11-13
Thanks, it seemed to work. At least 108MB of disk space freed!

---

