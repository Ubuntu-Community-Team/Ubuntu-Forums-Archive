---
title: "Network Manager"
date: 2006-12-26
forum: Networking &amp; Wireless
---

### Post by eamonn on 2006-12-26
Hi,

I just installed NetworkManager following the directions on [https://help.ubuntu.com/community/Wi...NetworkManager](https://help.ubuntu.com/community/Wi...NetworkManager) and the Add/Remove Applications program said that everything went fine and that I should expect to find NetworkManager in "Application/Internet/NetworkManager," but I didn't find it there. I already refreshed the gnome panel and the desktop, I logged out and then back in, but I still can't find it. Any help?

---

### Post by eamonn on 2006-12-26
Nobody knows how to fix it?

---

### Post by Floppyjoe on 2006-12-26
Do you see two computers connected together on your panel? The icon I mean.

---

### Post by eamonn on 2006-12-26
Yeah, I see one. You mean the one with the series of arrows indicating how strong my signal is?

---

### Post by Floppyjoe on 2006-12-26
I'm not sure if the network manager is the program that shows up on your panel as an icon and tells you if you are connected. to me it doesn't seem like a very usefull tool.

---

### Post by eamonn on 2006-12-26
[http://www.gnome.org/projects/NetworkManager/](http://www.gnome.org/projects/NetworkManager/)

That explains what it does. But I still don't know how to get it to show up.

---

### Post by eamonn on 2006-12-27
Somebody must know how to fix this.

---

### Post by lemoniceblock on 2006-12-30
Hihi, don't know if this will solve your problem or not, but I just d/l'd network manager and I didn't get an icon from the Applications>Internet menu either.  But, I did see a new icon pop up on the notification area of the navigation panel, so I'm guessing that's how you get into Network Manager?

---

### Post by jml on 2006-12-30
lemoniceblock is right.  That new icon on the upper right is the icon for the applet.  I believe there is no entry in the drop down menu because it is alway on.  If you left click on the icon, you will see all available networks listed.  If you right click on the icon, you will see options to enable/disable networking and wireless networking.

Joe

---

### Post by Jeff Hewett on 2007-01-01
Hello-

I'm having the same problem where Network Manager appeared to be installed properly, but I can't locate it.  As for the icon in the upper right corner, it is the Network Monitor, not the Network Manager.  Right clicking on it produces a pull down offering Properties.  This is equivalent to System->Administation->Networking and pressing Properties.

Jeff

---

### Post by fredj on 2007-01-01
When you install network-manager you usually also install network-manager-gnome
and it is this latter program that puts an icon in the systray on the either the top or bottom
right of your screen. You do not need to use System->Networking, in fact this will not work
with network-manager and should not be used to configure your wireless card.

Having said all that I have not found network-manager and network-manager-gnome to
provide a stable wireless connection. If they don't work for you then post again.

---

### Post by Floppyjoe on 2007-01-01
I just get the two networking computers icon on the gnome panel and it can't see my wireless connection for some reason. When i hover the mouse over it it says no network connection. Right clicking it just gives me three options 1 enable networking which is checked off. 2 Connection information which is shaded out. And 3 About -which gives some info about this seemingly useless application. There is no Icon for it in the menu system.

Does anyone know how to make it work?

---

### Post by gardara on 2007-01-02
at first, network-manager didn't appear at my systray. But this fixed it:

```
sudo gtk-update-icon-cache -f /usr/share/icons/hicolor
```

hopefully it will work for you guys too.

---

