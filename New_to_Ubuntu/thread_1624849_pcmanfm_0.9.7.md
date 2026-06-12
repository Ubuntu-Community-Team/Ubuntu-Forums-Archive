---
title: "pcmanfm 0.9.7"
date: 2010-11-18
forum: New to Ubuntu
---

### Post by dzon65 on 2010-11-18
Does anyone know how to edit the rightclick-open-with menu in pcmanfm 0.9.7?
I tried to add a command line for md5sum, got the wrong one and now I can't get rid of that option popping up in the menu.

---

### Post by drs305 on 2010-11-18
You can probably find the listing in ~/.local/share/applications/mimeapps.list

Just delete or edit the associated listing.

If you were using pcmanfm as root, look in /root/.local/share/applications/mimeapps.list

---

### Post by dzon65 on 2010-11-18
Okay,will have a look there.

---

### Post by dzon65 on 2010-11-18
Very nice.Required reboot but indeed they're gone.
Kind regards,J.

---

