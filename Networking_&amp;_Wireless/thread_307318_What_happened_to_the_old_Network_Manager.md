---
title: "What happened to the old Network Manager?"
date: 2006-11-26
forum: Networking &amp; Wireless
---

### Post by threethirty on 2006-11-26
OK when I was in Dapper I used network manager and loved it.  It was right in the notification area, it worked, I was in love.  But I recently went to Edgy  I have installed network manager and now it doesnt show up in my add to pannel menu, and to top all of this off I have KDE, GNOME, and XFCE installed so I would like to use the same kinda app across all three desktops.  Can anyone help me out? ](*,)

---

### Post by threethirty on 2006-11-26
i tried following this thread and got nowhere [http://www.ubuntuforums.org/showthread.php?t=306006&highlight=network+manager](http://www.ubuntuforums.org/showthread.php?t=306006&highlight=network+manager)

---

### Post by spd106 on 2006-11-26
You should have the line ```
nm-applet --sm-disable
``` in the start-up programs tab of the sessions dialog.
Then you just restart X or gdm to get the nm-applet in the notification toolbar.
I think this is installed as default with network-manager-gnome, I'm not sure about KDE or XFCE.

---

### Post by Jamie Jackson on 2006-11-26
I did it with:

sudo apt-get install --assume-yes network-manager-gnome
sudo /etc/init.d/dbus restart

Then, if it's not up for you at this point, try:
nm-applet

One thing that threw me is that the icon didn't appear quite as advertised, so I thought it wasn't installed, but it was. When you're connected to a wired connection, NM will show as two overlapping monitors a the top right of the gnome screen (next to the time). Through right and left clicking, you can get into the wireless options. When you're connected to a wireless AP, you'll get signal bars instead of the two overlapping monitors icon.

---

### Post by Jamie Jackson on 2006-11-26
> **spd106 said:**
> You should have the line ```
nm-applet --sm-disable
``` in the start-up programs tab of the sessions dialog.
Then you just restart X or gdm to get the nm-applet in the notification toolbar.
I think this is installed as default with network-manager-gnome, I'm not sure about KDE or XFCE.

FWIW, I didn't have to do this, as the *apt-get install* did it for me.

---

### Post by groggyboy on 2006-11-26
if you want network-manager to appear in kubuntu (kde) install the "knetworkmanager" package.  its the kde sibling package to network-manager-gnome - simply a pretty little icon for the systray.

---

