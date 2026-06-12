---
title: "How to remove gnome do dock bar?"
date: 2009-05-09
forum: New to Ubuntu
---

### Post by Mr.Kuchinawa on 2009-05-09
Title. 

Any help will be appreciated.

---

### Post by swoody on 2009-05-09
Mr.Kuchninawa,

Just go to a terminal "Applications">"Accessories">"Terminal" and enter this command:
```
sudo apt-get remove gnome-do
```
It'll ask you for your password, so type that in (note: for security reasons, when you type your password into the Terminal, it won't actually display any characters. Just type it in as normal) and hit enter. It may ask if you're sure you want to remove it, just type "y" or "yes" and hit enter again. After it does it's thing, gnome-do may still be open, so just press <super>+<space> (<super> is the Windows key on most keyboards) to bring up the Gnome-do interface, then click the little down arrow in the top right corner then click quit. After this, gnome-do should be nothing more than a memory :)

---

### Post by lvleph on 2009-05-09
If you stil want the functionallity of gnome-do and just don't like docky, you can change the gnome-do theme.

---

### Post by miaviator278 on 2009-11-06
Where is this theme change button?

I used to use gnome-do for every application launch.  Now it is utterly useless to me.

---

### Post by chickencaesar on 2009-11-06
> **miaviator278 said:**
> Where is this theme change button?

I used to use gnome-do for every application launch.  Now it is utterly useless to me.

Bring up Gnome Do. Type in 'Gnome Do'  and select 'Internal Gnome Do Items'. Press the right cursor key and select 'Preferences'. Select the 'Appearances' tag and choose any theme bar 'Docky'.

---

