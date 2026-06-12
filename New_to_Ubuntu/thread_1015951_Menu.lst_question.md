---
title: "Menu.lst question"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by monton on 2008-12-19
I just updated my dual boot XP/7.10 computer to 8.04. In the past XP was moved to the end of the list. I need XP to be the default for other users. I have edited the menu.lst file moving XP to the top. When I open the Menu.lst file XP is completely gone. How do I fix this so that XP loads as the default?
Thanks for any help
Monton:confused:

---

### Post by Titan8990 on 2008-12-19
Post the output of the following:


sudo fdisk -l


cat /boot/grub/menu.list

---

### Post by Michael.Godawski on 2008-12-19
hey
until we are waiting for the output, here is a comprehensive guide dealing with grub and also the menu.lst


[LIST]
[*][http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
[/LIST]

---

### Post by cariboo on 2008-12-19
Normally you just leave the menu in the order it was created then change this setting

```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0
```

Start counting down the list starting with zero, in my case Windows is the seventh OS in the list so I would set the defautl to 6.

Jim

---

### Post by ajgreeny on 2008-12-19
Be warned, however, that if you folow cariboo907's way the system will not boot to windows if you install a new updated linux kernel, as the numbering of the menu.lst entries will be changed.  You can edit the menu.lst file again to put it right, by adding 2 to the default number, or you can uninstall the oldest kernel you have still on your machine, thereby removing the number change in the list.

---

