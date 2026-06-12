---
title: "[SOLVED] network manager gone"
date: 2008-03-05
forum: Networking &amp; Wireless
---

### Post by Rytron on 2008-03-05
hi,
I can access the internet with my wireless adapter (d-link g122) - although sometimes it cuts out for no reason.

I once had the network manager on the panel at the top of the desktop - when I was online this showed some blue bars to represent signal strength. this icon is now missing and I do not know how to get it back.

I am still able to access the internet but I;d like to have this (network manager) icon back.

How do I get this back?

thanks.

---

### Post by ayampanggang on 2008-03-05
if you are using gnome, then right click on the gnome panel, then choose "add to panel", then in the add to panel dialog that appears, search for "notification area". it is located at the bottom so you'll have to scroll i believe. if it doesn't appear try to restart X (ctrl + alt + backspace)

---

### Post by Rytron on 2008-03-05
Thanks ayampanggang,

ironically though this solved a problem I just posted in another thread about not being able to open Glipper.

I can now use Glipper.:)

The network manager is still missing though.

---

### Post by Rytron on 2008-03-05
I must have inadvertently uninstalled nm-applet.
I reinstalled it using the Ubuntu 7.10 cd with the command:

```
sudo apt-get install network-manager-gnome
```

Internet working now with nm-applet 0.6.5 on panel.

I just wish the wireless internet would not cut out so much. Amazing if I remove the Usb adapter and connect the Usb adapter back again the internet sometimes comes back - strange.

---

