---
title: "Can't change permission"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by grifan526 on 2009-11-02
I went to change my grub menu and realized I couldn't because I obviously didn't have write permission on the menu.lst file. I tried to chmod and give myself write permissions but I was not allowed.  So I was wondering how can I give myself permissions to change this file?

---

### Post by unamanic on 2009-11-02
You don't want to give yourself permission, just use sudo to edit it in gedit:

```

sudo gedit [file]

```

---

### Post by Locke_99GS on 2009-11-02
```
sudo gedit /boot/grub/menu.lst
```
for Ubuntu 9.04 and earlier.

---

### Post by grifan526 on 2009-11-03
I tried that and after putting in my password it says "sudo: gedit: command not found". I am running 9.10 if that helps.

---

### Post by 3rdalbum on 2009-11-03
The earlier posters forgot that you are using Xubuntu. Xubuntu doesn't ship with the Gedit text editor - it has Mousepad instead, so change the 'gedit' bit to 'mousepad' in that command.

Also you might be using Grub2 as the bootloader. The configuration file is in a different place for Grub2, so you might need to find out about that.

---

### Post by grifan526 on 2009-11-03
Thanks that worked.

---

