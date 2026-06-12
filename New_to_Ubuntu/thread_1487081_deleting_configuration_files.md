---
title: "deleting configuration files"
date: 2010-05-18
forum: New to Ubuntu
---

### Post by launchy on 2010-05-18
hi i installed a bunch of apps such as awn awn, docky, gnome-do and cairo to test them out.  i used sudo apt-get --purge remove avant-window-navigator and sudo  apt-get autoremove to uninstall it but when i tried reinstalling awn, my configurations stayed the same instead of a "clean-install" of the app. can you help me to make a clean install of the app? or is it possible to delete the folders of awn under gconf-editor? using ubuntu 10.04.

---

### Post by launchy on 2010-05-18
can anyone help?

---

### Post by ubunterooster on 2010-05-18
Configuration folders are often hidden in your home as a .*name* folder. You want to delete that folder for each program.

For example: to restore Mozzila Thunderbird to defaults, I woud uninstall it, remove the .thunderbird file, then reinstall it.

---

### Post by Dayofswords on 2010-05-18
if you cant see them, hit Ctrl + h

---

### Post by launchy on 2010-05-18
thank you! deleting those folders worked like a charm:popcorn:

---

### Post by ubunterooster on 2010-05-18
Glad to hear. :D [Just be easy on that initial thread bumping; rules say once per 24hr.]

---

### Post by EssexEagle on 2010-05-18
For future reference, I believe the command to uninstall and remove all config files is
```
sudo apt-get purge *package*
```
rather than
```
sudo apt-get --purge remove *package*
```

---

### Post by launchy on 2010-05-19
> **EssexEagle said:**
> For future reference, I believe the command to uninstall and remove all config files is
```
sudo apt-get purge *package*
```rather than
```
sudo apt-get --purge remove *package*
```

i tried the sudo apt-get --purge remove package as well but it didnt work. but manually deleting there folders as said above worked out well for me.

---

