---
title: "gksu"
date: 2011-01-03
forum: New to Ubuntu
---

### Post by shashanksingh on 2011-01-03
whats the difference between sudo and gksu?

---

### Post by overdrank on 2011-01-03
> **shashanksingh said:**
> whats the difference between sudo and gksu?

From [RootSudo]("https://help.ubuntu.com/community/RootSudo")
> Graphical sudo
You should never use normal sudo to start graphical applications as Root. You should use gksudo (kdesudo on Kubuntu) to run such programs. gksudo sets HOME=~root, and copies .Xauthority to a tmp directory. This prevents files in your home directory becoming owned by Root. (AFAICT, this is all that's special about the environment of the started process with gksudo vs. sudo)

---

### Post by sisco311 on 2011-01-03
sudo is a (CLI) setuid root application which allows you to run a command as another user. 

gksu is GUI frontend for su and sudo.

---

### Post by shashanksingh on 2011-01-04
Thank you.

---

