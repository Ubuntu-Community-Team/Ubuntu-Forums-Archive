---
title: "WPA Key Gets Disabled at Reboot"
date: 2007-11-21
forum: Networking &amp; Wireless
---

### Post by Kazol on 2007-11-21
I installed and configured ndiswrapper for a "05:01.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)" using these directions: [http://64.233.179.104/translate_c?hl=en&u=http://www.tuxmind.altervista.org/%3Fp%3D388&prev=/search%3Fq%3Dhttp://www.tuxmind.altervista.org/%253Fp%253D388%26hl%3Den%26sa%3DG](http://64.233.179.104/translate_c?hl=en&u=http://www.tuxmind.altervista.org/%3Fp%3D388&prev=/search%3Fq%3Dhttp://www.tuxmind.altervista.org/%253Fp%253D388%26hl%3Den%26sa%3DG)

However, I only get a connection when delete the previous entry and type in my WPA (worked only under TKIP) key into the Network Manager each time I reboot. /etc/network/interfaces had normal entries with a PSK key (not the actual WPA key). I tried following these directions: [http://ubuntuforums.org/showthread.php?t=263136](http://ubuntuforums.org/showthread.php?t=263136) but they didn't work out (now I need to get rid of the junk I got from doing it; I only restored the interfaces file).

I have heard of a solution involving switching the boot order of ndiswrapper or something like that....any ideas?

---

### Post by Blutack on 2007-11-21
Have you tried wiping your key completely from gnome-keyring?  Go Administration --> Keyring Manager and delete all the network keys.  Reboot.  Enter key.  Reboot again.  Pray to relevant deity.  It works for me.  Also helps if your gnome-keyring password is the same as your login pasword.

---

### Post by Kazol on 2007-11-21
There are no keys in keyring.

---

### Post by Kazol on 2007-11-21
I have heard this is an Ubuntu-specific problem that has something to do with Network-Manager.
Any ideas?? I've spent hours trying to resolve this problem.

---

