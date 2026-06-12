---
title: "the contents of my Home folder are replicated on my desktop"
date: 2010-08-31
forum: New to Ubuntu
---

### Post by the8thstar on 2010-08-31
Hello,

Something just happened after I deleted the Desktop icon in my Home folder (this was an accident). Now all the contents of my Home folder are replicated on my desktop! This is most annoying and I can't seem to find a solution through gconf-editor.

Your help would be appreciated.

---

### Post by dv3500ea on 2010-08-31
To solve this:
[LIST=1]
[*]Make a folder called 'Desktop' in your home folder
[*]Make sure XDG_DESKTOP_DIR is set to "$HOME/Desktop" in the file: ~/.config/user-dirs.dirs
[/LIST]

---

### Post by the8thstar on 2010-09-05
Actually, I checked my existing ~/.config/user-dirs.dirs before anything and I realized there were inconsistencies as my home folder was set to be the desktop.

Thanks for the hint!

---

