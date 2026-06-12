---
title: "Left-side Application Panel Not Working"
date: 2011-04-13
forum: New to Ubuntu
---

### Post by kopilavalley on 2011-04-13
Hello, 

First please forgive my lack of Linux/Ubuntu knowledge.  I am a teacher at an NGO-sponsored school in Nepal.  We have installed Ubuntu 10.10 on donated laptops (many are older machines.)

All installations have gone well except on a Samsung P30.  Model code: NP30RH6LTC/SEG

10.10 installed but when you click or mouse over the left panel which contains application icons, all open windows and the panel disappear.  Only the red/black default desktop background is left.

Also, there is no upper panel or lower panel for minimized programs that are running.  I can't right click on the desktop.  You can click the ubuntu icon in the top left corner.  If you don't mouse over the left panel the software works fine, but it is very annoying and also difficult for our teachers to learn how to use the computer with this issue happening.

Is this a graphics card problem?  We have already tried uninstalling and reinstalling.

Thank you for any help or suggestions.

Lisa

---

### Post by poodoopealeoaph on 2011-04-13
It may be, since the donated computers are older, that your system may not be able to handle the requirements of ubuntu. You should try downloading xubuntu or lubuntu at [www.xubuntu.com](www.xubuntu.com) or [www.lubuntu.com](www.lubuntu.com) and see if either of those work. It is basically the same system but with much lower requirements. So, try out xubuntu 10.10 and see if that works. If it seems to work slightly better but is just slower than you expected, try out lubuntu. It doesn't look like much but it gives you the same access as regular ubuntu to the repositories and everything but it is just extremely light weight and gives you a super fast desktop.

---

### Post by Elfy on 2011-04-13
> 10.10 installed but when you click or mouse over the left panel which contains application icons, all open windows and the panel disappear. Only the red/black default desktop background is left.

Also, there is no upper panel or lower panel for minimized programs that are running. I can't right click on the desktop. You can click the ubuntu icon in the top left corner.This I assume is the netbook version then.

Try installing ubuntu-desktop from a terminal if you have issues with the panel. 

Logout and then when in the login window choose the new option from the drop down menu at the bottom. More info on this here if I make no sense :) [https://help.ubuntu.com/10.10/config-desktop/C/other-desktops.html#other-desktop-xfce](https://help.ubuntu.com/10.10/config-desktop/C/other-desktops.html#other-desktop-xfce)

```
sudo apt-get install ubuntu-desktop
```

---

### Post by poodoopealeoaph on 2011-04-13
p

---

