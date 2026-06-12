---
title: "Wireless icon problem ubuntu 9.10"
date: 2010-02-04
forum: New to Ubuntu
---

### Post by Tiekiller2 on 2010-02-04
Hi! Newbie here. I switched to ubuntu a few months back and started customizing just recently. well i installed Wicd on ubuntu and i lost the original wireless icon that was on the task bar. so now i can't connect to my netgear at home. how do i get it back? please help


ps. i already tried to remove Wicd but then i have nothing to connect to my netgear with.

---

### Post by audiomick on 2010-02-04
If you right click on an empty bit of the task bar, you should be able to choose the icon out of the "add to panel" list.

---

### Post by coolbrook on 2010-02-04
```
sudo apt-get install network-manager-gnome
```if you want to go back to the original network manager/panel applet.    


A reboot has worked for me to get WICD's applet back in the panel.  Try that first.

---

### Post by Tiekiller2 on 2010-02-05
> **coolbrook said:**
> ```
sudo apt-get install network-manager-gnome
```if you want to go back to the original network manager/panel applet.    


A reboot has worked for me to get WICD's applet back in the panel.  Try that first.
   


thanks for the help :)

this will teach me to be more careful with ubuntu.

---

