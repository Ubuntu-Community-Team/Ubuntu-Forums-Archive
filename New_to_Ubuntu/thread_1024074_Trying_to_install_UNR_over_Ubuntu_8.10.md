---
title: "Trying to install UNR over Ubuntu 8.10"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by unluckystuntman on 2008-12-28
I installed UNR using a bootable USB key on my Samsung NC10 netbook. The layout of UNR is great but after playing around with UNR for a day, I uninstalled it because the program kept freezing up on me.

I installed Ubuntu 8.10 onto my Samsung NC10 netbook. It works great but I still want the UNR layout. I am following the directions found at [https://wiki.ubuntu.com/UNR](https://wiki.ubuntu.com/UNR) and installing the UNR package over Ubuntu 8.10 hoping I won't have the same freezing issues.

I am having problems with these two sections:

**_* Neither the netbook-launcher or maximus automatically start, you will need to add them to your session through gnome-session-properties_**

I think I figured this out doing some searches. I opened up System > Preferences > Sessions and added Maximus and Netbook-Launcher.

Is this the correct way to add these programs to gnome-session-properties?

I also do not know how to accomplish this:

[B][U]As there isn't a configuration package available yet, you will need to setup the gnome-panel to mimic the standard UNR set-up. The applet order is as follows:

go-home-applet | window-picker-applet | notifcation-area-applet | mixer-applet | clock[/U][/B]

Thank you in advance for the help.

---

### Post by unluckystuntman on 2008-12-29
bizzump

---

### Post by mikeyphi on 2008-12-29
1. First install the UNR packages. 
If you've correctly followed the instructions at [https://wiki.ubuntu.com/UNR](https://wiki.ubuntu.com/UNR)
 -  Ubuntu 8.10 (Intrepid) UNR Package Installation
then all you need to do is add the two programs to sessions (as you already said).

The final bit is about getting the top menu panel set-up.
First right click on unwanted icons and remove.
Then right-click on empty space and select add - choose from the pop-up menu - place and lock to panel.
Put the icons in the stated order - or as you want.

---

