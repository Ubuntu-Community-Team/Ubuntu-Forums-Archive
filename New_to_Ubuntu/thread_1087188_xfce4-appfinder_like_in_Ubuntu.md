---
title: "xfce4-appfinder like in Ubuntu"
date: 2009-03-04
forum: New to Ubuntu
---

### Post by revival on 2009-03-04
Hello,

I tried XUbuntu some weeks ago and then I switched to Ubuntu. One of the applications that I found very useful in XUbuntu and that I am missing in Ubuntu is the **xfce4-appfinder**. Is there an application like it in Ubuntu? It is very useful when you don't know where a binary is or simply to find additional information about the file.

Thanks in advance!

---

### Post by dbbolton on 2009-03-04
Even though you're using Gnome, you could go ahead and try installing xfce4-appfinder. I'm not sure of a Gnome equivalent, although you can find some program's commands using alacarte (System > Prefs > Main Menu). Right click on an entry and choose "Properties". It will tell you the command that the menu entry launches.

Another trick, if you like using the terminal, is tab completion. It's helpful if you know the first few letters of a command but not the whole thing. For example, if you open a terminal, type "xfce" and then press the Tab key twice, it will print all the commands in your path that start with those letters:
```
xfce

xfce4-about             xfce4-panel             xfce4-session-logout
xfce4-appfinder         xfce4-popup-menu        xfce4-terminal
xfce4-autostart-editor  xfce4-popup-notes       xfce4-terminal.wrapper
xfce4-dict              xfce4-popup-places      xfce4-tips
xfce4-kiosk-query       xfce4-popup-windowlist  xfce-mcs-manager
xfce4-menueditor        xfce4-screenshooter     xfce-setting-show
xfce4-mixer             xfce4-session  


```

---

### Post by revival on 2009-03-04
Tab completion is very useful, I use it a lot, but if you don't know what each program does is like searching for a needle in a haystack.

I already knew about Alacarte, but it doesn't give you the full path to the application. I am sure there must be a xfce4-appfinder like for Ubuntu.

---

### Post by dbbolton on 2009-03-04
> **revival said:**
> Tab completion is very useful, I use it a lot, but if you don't know what each program does is like searching for a needle in a haystack.

I already knew about Alacarte, but it doesn't give you the full path to the application. I am sure there must be a xfce4-appfinder like for Ubuntu.
You can look at your path by entering one of the following two commands:
```

echo $PATH

env | grep "PATH"

```

All of your binaries will be in those folders, with the majority in /usr/bin and root's binaries in /usr/sbin .

Anyway, xfce4-appfinder does not depend on Xfce. You can read the dependencies here: [http://packages.ubuntu.com/intrepid/xfce4-appfinder](http://packages.ubuntu.com/intrepid/xfce4-appfinder)
I'm sure the only extra packages you would need to install to use it in Gnome would be [libxfce4util4]("http://packages.ubuntu.com/intrepid/libxfce4util4") and [libxfcegui4-4]("http://packages.ubuntu.com/intrepid/libxfcegui4-4"). In other words, there's no harm in using it in Gnome. But if you really want a pure Gnome system, I don't know what to tell you. The deskbar applet might be a start.

---

