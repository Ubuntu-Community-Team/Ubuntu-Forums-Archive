---
title: "Issue with HP Bluetooth Keyboard K4000"
date: 2018-02-15
forum: Networking &amp; Wireless
---

### Post by konigstiger1990 on 2018-02-15
Hello Ubuntu team;

I have an issue with my bluetooth keyboard "HP Bluetooth Keyboard K4000".
When i try to pair the keyboard, the systems shows a PIN, i set the PIN but when i press the "enter" key, it does not have any effect and i cannot connect the keyboard.

I read some forums and a bug about this issue, the "solution" is to apply a patch to the bluez software to "[COLOR=#333333]Add ssp parameter fix[/COLOR]", the version in the patch is 4.101-0ubuntu19, but in my system, the bluez version is 5.370ubuntu5.1.

How i can solve this issue?
My system is 16.04 LTS.

Regards from Colombia.
Cristian.

---

### Post by konigstiger1990 on 2018-02-15
UPDATE:
I find some info on Internet:

It seems the issue is related with gnome-bluetooth:
[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=821142](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=821142)
[http://launchpadlibrarian.net/182118615/bluez_4.101-0ubuntu19_source.changes](http://launchpadlibrarian.net/182118615/bluez_4.101-0ubuntu19_source.changes)

Regards!

---

