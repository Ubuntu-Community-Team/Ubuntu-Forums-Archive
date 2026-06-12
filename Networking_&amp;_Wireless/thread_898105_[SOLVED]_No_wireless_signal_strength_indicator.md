---
title: "[SOLVED] No wireless signal strength indicator?"
date: 2008-08-22
forum: Networking &amp; Wireless
---

### Post by Ack226 on 2008-08-22
New Ubuntu user here.  I'm posting this from my new Ubuntu install!  :D

I got my wireless set up pretty easily, and it's working great, but I have no signal strength indicator on my desktop panel.  From the documentation I've read I should have a wireless signal strength indicator showing in place of the "2 black monitors" network indicator in the upper-right.  Well, even when I'm connected via wireless and not plugged in at all I only get the "2 monitors."  

Is this normal?  How can I get a wireless signal strength indicator up on my desktop?

---

### Post by spd106 on 2008-08-23
The signal strength indicator is actually the panel icon for the Network-Manager control applet (nm-applet). If you have disabled roaming mode for the interface in System -> Administration -> Network, then you are using the old Network-Admin capplet, which doesn't have a signal strength indicator for it's panel icon.

If you switch roaming mode back on it should re-appear, but you can't set static IP address etc in this mode. This feature will be added in Ubuntu 8.10.

---

### Post by Ack226 on 2008-08-23
Turning on Roaming Mode did it.  I don't need any special settings for this connection, so everything's working great now.  Thanks a lot!

---

### Post by caljohnsmith on 2008-08-23
Ack226, if you want a wifi signal strength monitor that works regardless of whether you are using roaming mode, DHCP, or a static IP, try "kwifimanager". It works great in Gnome:
```
sudo apt-get install kwifimanager
kwifimanager
```

---

