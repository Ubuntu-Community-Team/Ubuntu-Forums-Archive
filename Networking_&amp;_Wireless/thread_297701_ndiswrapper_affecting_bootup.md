---
title: "ndiswrapper affecting bootup"
date: 2006-11-11
forum: Networking &amp; Wireless
---

### Post by Tommerz on 2006-11-11
Hey everyone,

I have this annoying problem with booting up in dapper where sometimes I end up having to wait ages when my computer is configuring the network.

Sometimes it won't boot up at all, and I end up having to power off and reboot.

Any ideas why this is? Any way to make it so that I can configure network once i get to my desktop? It's a pain in the boo-tum. :(

---

### Post by flosofl on 2006-11-11
Tommerz,

Your subject mentions ndiswrapper, so I am assuming you are using wireless.

Install network-manager and network-manager-gnome.

Make sure that the wireless adapter is *not* set to be active at boot.  Network-Manager will take care of that.  Ndiswrapper will load the windows driver as usual, but the network config will now be handled by Network-Manager.  When you login to Gnome, you will have an icon next in the system notification tray (next to the clock).  If everything went well, a left click will list the available wireless networks.  Just click the one you want.  (It will set that as the preferred when that WLAN is available).

If you are using WEP, WPA, WPA2 you will need to enter your key.  It will be stored in the Gnome-Keyring, so make sure to allow Network-Manager access to it (you will be prompted).  It will also ask you for a password for Gnome-Keyring.  I would recommend using the same password as your user name.  You will have to enter that password when Network Manager is connecting to the network.  There is a PAM module floating around that passes you user password to Gnome-Keyring (at least in FC5 there was), so if you find that you will not need to enter the password a second time.

---

### Post by Tommerz on 2006-11-11
Oops, forgot to specify that I'm using xubuntu, should hopefully still work though, shall I add a command to start the tray icon to xfce's start up programs?

---

### Post by Tommerz on 2006-11-11
Ok, I think I managed to find the command in the terminal, nm-applet, but it's showing properties for my ethernet connection rather my wireless lan.

What should I do now? And also, boot up time didn't seem to be any different :( but that could just be because my card happened to find the wifi network in rapid time.

Any ideas?

---

