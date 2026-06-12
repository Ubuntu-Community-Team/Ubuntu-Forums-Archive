---
title: "Help with Shell"
date: 2010-08-02
forum: New to Ubuntu
---

### Post by DTHCND on 2010-08-02
Quick question... When you run a shell script using sudo, and there are commands within the script, is the word sudo required when writing the script? What I am trying to do is get a script working but some lines require sudo, but I would prefer if it would work in non debian linux distros...

---

### Post by da burger on 2010-08-02
If the script is run with root privileges (which it will be if it's prefaced with sudo) all the commands in it will be run as root, meaning they do not need to be prefaced with sudo. (People on other distros will just need to log in as root before running the script)

---

