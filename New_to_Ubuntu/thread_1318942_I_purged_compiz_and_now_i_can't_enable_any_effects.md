---
title: "I purged compiz and now i can't enable any effects"
date: 2009-11-08
forum: New to Ubuntu
---

### Post by baz of linux on 2009-11-08
so i managed to mess up compiz and make all the windows black so i opened a terminal session and purged compiz. now when i log back in, not only when i reinstalled compiz does it not have all the effects it used to, but they don't even work even if i enable them. what do i do?

---

### Post by RedSingularity on 2009-11-08
You could try completely reinstalling it.  Do this in terminal.

sudo apt-get autoremove --purge compiz & sudo apt-get autoremove --purge compizconfig-settings-manager

Also delete the config files in /home/you/apps/compiz and home/you/.config/compiz  ((the .config is hidden press CTL + h to reveal it.))

then do this.....

sudo apt-get install compiz & sudo apt-get install compizconfig-settings-manager

---

