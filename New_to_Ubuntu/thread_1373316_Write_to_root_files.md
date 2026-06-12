---
title: "Write to root files"
date: 2010-01-05
forum: New to Ubuntu
---

### Post by confubar on 2010-01-05
I went to save a gimp brush in the appropriate folder, on my own computer on which I am the only user... The thing tells me I don't have permission, the file belongs to root. What is the easiest workaround... I would prefer to minimize using the terminal.

---

### Post by The Cog on 2010-01-05
Read this to understand more about permissions:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Launching nautilus with root privileges will enable you to do dangerous things like writing to system areas. Press Ctrl-Alt-F2 and enter the command **gksu nautilus**.

---

### Post by Enigmapond on 2010-01-05
```
gksudo nautilus
```This will enable root browsing with nautilus.

---

### Post by confubar on 2010-01-06
This did the job, thanks. Ctrl-Alt-F2 didn't do anything... was it supposed to call up a terminal?...but I got into nautilus as root and changed the permissions of the brushes file.

---

### Post by The Cog on 2010-01-06
> **confubar said:**
> This did the job, thanks. Ctrl-Alt-F2 didn't do anything... was it supposed to call up a terminal?...but I got into nautilus as root and changed the permissions of the brushes file.

I'm a dick-head! Sorry. It's just Alt-F2. It brings up a small one-line command entry box where you can type the commands to launch graphical programs.

---

