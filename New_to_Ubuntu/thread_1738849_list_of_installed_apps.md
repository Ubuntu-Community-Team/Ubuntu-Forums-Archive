---
title: "list of installed apps?"
date: 2011-04-25
forum: New to Ubuntu
---

### Post by georgelappies on 2011-04-25
Hi all, where can I find a list of all the installed packages that comes with xubuntu 11.04?

---

### Post by Perfect Storm on 2011-04-25
Type:
```
dpkg --get-selections
```
and you'll get all the package that are installed.

---

### Post by Blasphemist on 2011-04-25
If anyone, including possibly OP, is looking for the listing of just what is included "out of the box" in natty, it appears someone will need to run the command shown in the previous post after a clean install. And then you'd have information that I can't seem to find now. This seems like something that would be available in marketing information at the least but if so I can't find it.

---

### Post by georgelappies on 2011-04-25
Thanks, that command worked well. Weird that they do not list the vanilla install packages anywhere...

---

