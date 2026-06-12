---
title: "GTK problems"
date: 2009-02-07
forum: New to Ubuntu
---

### Post by nemodot on 2009-02-07
This may already have been posted, it's a problem that I have with GTK.

First of all, I had installed a theme called Shiki-Colors wich is very cool, but the problem is that Some apps, like the synaptic lose the theme. Like this:

[http://img443.imageshack.us/my.php?image=pantallazogc4.png](http://img443.imageshack.us/my.php?image=pantallazogc4.png)

Also I have a problem with gnome apps in KDE 4, they look as the synaptic in the link above. How can I fix that?

---

### Post by m_duck on 2009-02-07
One way to solve the problem in gnome, is to run the following in the teminal:```
sudo ln -s /home/yourusername/.themes /root/.themes
sudo ln -s /home/yourusername/.icons /root/.icons
```This creates two symlinks in the /root folder so when running a program as root, it uses the same gtk theme as your user as the themes you add with the "Appearance" dialogue, install for only your user.

The alternative is to install themes for all users, by extracting them to /usr/share/themes.

---

