---
title: "Burg Lootloader help"
date: 2010-11-24
forum: New to Ubuntu
---

### Post by hunter99507 on 2010-11-24
I just installed BURG and it works great. The only thing is i want to remove entries from the menu. I only want windows 7 and ubuntu to be on the start up menu.  Right now i got windows xp, and some other ubuntu ones as well.  Can someone help me with burg to delete those entrys?  Thanks

---

### Post by yankysunny on 2010-11-24
The options should be in /boot/grub/menu.lst

---

### Post by hunter99507 on 2010-11-24
I checked there and i couldnt find the menu list.  In BURG it says the file is ect/defualt/burg but i cant find the list of OS's.

---

### Post by hunter99507 on 2010-11-24
Also on a side note, how do i edit these files? For example when i click /ect/defualt/burg it opens in gedit. When it opens its read only, and i cant edit anything.  How do i open it to edit the file? Thanks

---

### Post by yankysunny on 2010-11-24
I dont particularly remember the path for menu.lst
```
sudo locate menu.lst
```
If you find that list you can remove the excess off

Secondly it opens in readonly cuz you do not sudo it
```
sudo gedit {PATH} 
```

---

### Post by I'mGeorge on 2010-11-24
edit the file /boot/burg/burg.cfg or add only the entries you want in /etc/burg.d/40_custom removing them from the /boot/burg/burg.cfg file. After that in a terminal do
```

update-burg

```

---

