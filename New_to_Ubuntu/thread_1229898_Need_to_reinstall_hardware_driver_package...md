---
title: "Need to reinstall hardware driver package.."
date: 2009-08-02
forum: New to Ubuntu
---

### Post by Rootsdem on 2009-08-02
Hello, all this weekend i have been trying to get my new wifi card working, i finally got the drivers loaded but somehow accidently removed the hardware drivers program under system > administration..so i can't connect to the inet with ubuntu 9.04 to repackage it!

I have connection via windows vista, is there any way of downloading that package onto UBS stick and reinstalling it from there? if so, would anybody know the command to type in the terminal for this action?

Thanks in advance

RD

---

### Post by cariboo on 2009-08-02
Unless you removed jockey-gtk there is no need to reinstall the package. Press Alt-F2 ant type:

```
gksu jockey-gtk
```

To re-enable in the menu right click applications and select edit menus then System-->Administration and put a check mark beside Hardware Drivers.

One way to check what packages you have installed/removed is to to System-->Administration-->Synaptic Package manager-->Edit-->History.

---

### Post by Rootsdem on 2009-08-02
Thanks for the speedy reply. I have removed the jockey-gtk. Can i get it back any other way, or do i have to reinstall Ubuntu?

Thank you

---

### Post by braete on 2009-08-02
In software sources, 1st tab, check install from cd/dvd (sry i dont have english as default language so i dont know the name for sure) and reinstall it via synaptic.

ps: i never did this and i dont know if it works

---

