---
title: "Make the desktop show ~/Desktop again"
date: 2009-08-14
forum: New to Ubuntu
---

### Post by InfectedWithDrew on 2009-08-14
I deleted ~/Desktop to create a symlink to my Windows desktop (the symlink works).  But in the process of doing so, my desktop shows /home now instead of, well, ~/Desktop.  I've tried rebooting and even deleting the symlink and making a directory called ~/Desktop but no luck, I'm stuck.

Any help?  Thank you in advance!

---

### Post by ajgreeny on 2009-08-14
Open gconf-editor and go to apps>nautilus>preferences and make sure that "desktop_is_home_dir" is not selected.  If that does not work, then I can't think of anything else.

---

### Post by InfectedWithDrew on 2009-08-14
> **ajgreeny said:**
> Open gconf-editor and go to apps>nautilus>preferences and make sure that "desktop_is_home_dir" is not selected.  If that does not work, then I can't think of anything else.It was not selected to begin with.

---

### Post by CatKiller on 2009-08-14
You could try checking that you've got ```
XDG_DESKTOP_DIR="$HOME/Desktop"
``` in ~/.config/user-dirs.dirs too. That's me out of ideas as well.

---

