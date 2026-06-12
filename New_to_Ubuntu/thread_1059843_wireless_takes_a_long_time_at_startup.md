---
title: "wireless takes a long time at startup"
date: 2009-02-04
forum: New to Ubuntu
---

### Post by aBitLater on 2009-02-04
when i reboot 8.10, the network manager will show other wireless access points nearby my home, but takes a long time to connect to the hidden wireless network (my home wireless).

It does 'eventually' do this, it just takes a long time.  Faster to do it manually.  But if I have my wired connection plugged in, the wireless will establish much more quickly.

Is there a file I can edit to fix this?  I looked at 
/etc/networking/interfaces - nothing there but 
```

auto lo
iface lo inet loopback

```

Also, should I set my wireless (wlan0) to "system setting" like the wired (eth0) is configured?

---

### Post by Kobalt on 2009-02-04
Your Network Manager is in roaming mode, try to switch to a manual configuration entering your wireless network details. Maybe it'll help as you use a hidden SSID.

---

### Post by aBitLater on 2009-02-04
I don't see any options for Roaming Mode, but I did enter the settings for my wireless, which was necessary due to the fact that it's hidden and uses authentication.  There is an option in the GUI Network Manager to 'connect automatically', and I did check this box.

maybe I didn't understand your advice (?)

---

