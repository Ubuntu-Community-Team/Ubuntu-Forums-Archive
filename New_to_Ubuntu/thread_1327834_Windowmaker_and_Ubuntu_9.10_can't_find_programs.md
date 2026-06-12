---
title: "Windowmaker and Ubuntu 9.10 can't find programs"
date: 2009-11-15
forum: New to Ubuntu
---

### Post by Varoom on 2009-11-15
I have installed Ubuntu 9.10 on a spare drive in my computer.  Used Synatic and downloaded Windowmaker.  I cannot see all the programs that are in ubuntu gnome under Windowmaker. I also cannot get a wireless connection automatically as in gnome.  What must I do to have access to all programs to  run under Wmaker.

---

### Post by Meskarune on 2009-11-15
just type the name of the program you want to use in the terminal and it will load. Or install gnome-do and use that to launch programs...

---

### Post by Varoom on 2009-11-16
Thanks for input I have tried that but I am not succeeding.  I still cannot connect to the internet through wmaker wirelessly and most of the gnome programs are not setting up in wmaker.

Is there a program I am to run in order to link programs from gnome to wmaker ?

Thank You

---

### Post by cariboo on 2009-11-16
Wmaker is a pretty basic Window manager and it is no longer maintained, its been several years since I used it, but if you right click on the icons on the right I believe you will be able to access menus to add programs to the desktop.

As far as your wireless connection is concerned, there is not wireless connection applets, as wireless wasn't very prevalent back then. You can setup your wireless connection manually in /etc/network/interfaces. Just add the following to the file for a dhcp connection:

```

auto ethx
iface ethx inet dhcp
wireless-essid XXXXXXXXXXX
wireless-key XXXXXXXX
```

where ethx = your wireless device it could be either ethX or wlanX.

---

