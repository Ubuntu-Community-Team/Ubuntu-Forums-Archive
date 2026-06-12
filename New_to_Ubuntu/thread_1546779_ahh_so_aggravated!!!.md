---
title: "ahh so aggravated!!!"
date: 2010-08-05
forum: New to Ubuntu
---

### Post by zyrtek69 on 2010-08-05
ok i'm trying to fix the lame <snip> your profile could not be opened google chrome error.. i found an article and im trying to follow step 2 

[http://ubuntuforums.org/showthread.php?t=1485136&highlight=profile+opened+correctly](http://ubuntuforums.org/showthread.php?t=1485136&highlight=profile+opened+correctly)

now im a total n00b and i have no clue where to find the .config folder..

---

### Post by kerry_s on 2010-08-05
file & folders -> file manager(the 1 with the house on it)
press-> ctrl+h <-to show hidden

---

### Post by tekkidd on 2010-08-05
open up your home folder and press CTRL+H, you will then see a bunch of folders with a "." in front of them, now just find the .config one.

---

### Post by cavalier911 on 2010-08-05
~/  is a wildcard abbreviation for the home folder of the logged in user
If I'm logged in as user tom it would be /home/tom
A filename with a dot in front aka dot files such as .config is hidden unless you use Ctrl+H in nautilus,thunar,pcmanfm filemanagers to show hidden files or ls -la in terminal
So ~/.config would be /home/tom/.config for user tom

---

