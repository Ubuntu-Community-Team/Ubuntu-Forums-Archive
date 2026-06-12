---
title: "[SOLVED] Wastebin icon problem/Ubuntu 8.10"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by germanix on 2008-12-16
I installed Ubuntu 8.10 . I have noticed that the wastebin icon, bottom left corner, shows up full even after I have emtied the wastebin. If memory serves me correct, on Ubuntu 8.04 when there were waste in the bin, the icon showed a full wastebin, and after emtying it the icon changed to show a empty bin. This is not the case by me at the moment. The icon always shows a full bin regardless if it is full or empty. Is this normal for 8.10? If not how can one fix it?

---

### Post by PartisanEntity on 2008-12-16
Perhaps there are hidden file in there. Have you tried to view hidden files in the trash?

Alternatively you can try to force emptying the trash from the command line: **[COLOR="Red"](warning: make sure to enter the command exactly as written here, be very careful)[/COLOR]**

This will delete files in the root trash
```
sudo rm -rf ~/.local/share/.Trash/files/*
```

This will delete your own trash, replace [user] with your username
```
sudo rm -rf /home/[user]/.local/share/.Trash/files/*
```

Hope this helps.

---

### Post by Michael.Godawski on 2008-12-16
Hi germanix, 
[[COLOR=#D40000]**PartisanEntity**[/COLOR]]("http://ubuntuforums.org/member.php?u=192328") was faster...

you can also check in 
```
gconf-editor
```and navigating to apps/nautilus/desktop/ 
if there is a option to change the display of the trash icon.

---

### Post by PartisanEntity on 2008-12-16
p.s. to delete hidden files replace the '*' with '.*'. But again, be very very careful.

---

