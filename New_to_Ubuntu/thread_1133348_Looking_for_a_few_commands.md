---
title: "Looking for a few commands"
date: 2009-04-22
forum: New to Ubuntu
---

### Post by beastrace91 on 2009-04-22
When you right click on the applications menus and select "edit menus" is there a command I can run in console to get to the menu it displays with out having to go through the clicks?

Also is there a command I can use to terminate a process if I know it's name?

Thanks,
~Jeff

---

### Post by taurus on 2009-04-22
```
killall app_name
```
or
```
sudo killall app_name
```
If you need root privilege.

---

### Post by llamabr on 2009-04-22
or you can use ps or top to find out the process id (pid) and issue:

```
kill -9 pid
```

More useful if you want to kill one instance of something, but leave others going, with the same name.

---

### Post by beastrace91 on 2009-04-22
Thank you much. Anyone have any idea about a command to open the menu editor?

~Jeff

---

### Post by oldos2er on 2009-04-22
> **beastrace91 said:**
> Thank you much. Anyone have any idea about a command to open the menu editor?

~Jeff

```
alacarte
```

---

