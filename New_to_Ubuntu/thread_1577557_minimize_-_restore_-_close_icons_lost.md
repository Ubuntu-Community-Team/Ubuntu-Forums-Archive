---
title: "minimize - restore - close icons lost"
date: 2010-09-19
forum: New to Ubuntu
---

### Post by navinbht13 on 2010-09-19
minimize-restore-close icons disappeard when I used Extra Visual Effects.
What to do
From  gconf-editor  all doesn't works??????????
:(

---

### Post by Paddy Landau on 2010-09-19
You don't say what version of Ubuntu you use.

First thing is to disable extra visual effects.

I recommend that you do **not** use gconf-editor to do this. Instead, go to System > Preferences > Appearance > Visual Effects > None.

Then try again: System > Preferences > Appearance > Visual Effects > Extra.

If you still have problems, install [compizconfig-settings-manager]("apt:compizconfig-settings-manager") (if you haven't already done so). Go to System > Preferences > CompizConfig Settings Manager > Preferences > Reset to defaults.

Post again if you still have problems.

---

