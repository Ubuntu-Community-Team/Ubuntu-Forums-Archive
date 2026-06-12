---
title: "what is a good wifi stumbler/sniffer?"
date: 2006-07-29
forum: Networking &amp; Wireless
---

### Post by Andrew12106 on 2006-07-29
the utilities that come w/ ubuntu really dont tell much about the networks in range

---

### Post by Ziox on 2006-07-29
do you have network-manager installed...its an gnome panel item...but you may have to install it:

sudo aptitude install network-manager-gnome

here's a warning though: netoworkManager cannot manage any cards that have entries in /etc/network/interaces.  If you've addd your network card to that file, make sure you remove it before you start working with NetworkManager.

EDIT: after installation, you need to add the nm-applet to the session startup tab.  System => preference => Sessions... and add "nm-applet" without quotes to the Startup Programs Tab.  Reboot and you should see an icon in your notification area.

Hope this helps

---

### Post by calx on 2006-07-29
Try Kismet.. [http://www.kismetwireless.net/]("http://www.kismetwireless.net/")


> **Andrew12106 said:**
> the utilities that come w/ ubuntu really dont tell much about the networks in range

---

### Post by Ziox on 2006-07-29
> **calx said:**
> Try Kismet.. [http://www.kismetwireless.net/]("http://www.kismetwireless.net/")

you can download kismet from the repositories: sudo aptitude install kismet

---

### Post by Andrew12106 on 2006-07-29
thanks

---

### Post by Andrew12106 on 2006-07-29
i notice that kismet has no gui, can you suggest a gui sniffer?

---

### Post by Ptero-4 on 2006-07-29
wifi radar.

---

