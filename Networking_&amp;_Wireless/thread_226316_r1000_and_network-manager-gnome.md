---
title: "r1000 and network-manager-gnome"
date: 2006-07-31
forum: Networking &amp; Wireless
---

### Post by Krzysztof on 2006-07-31
Can anyone confirm using r1000 wired network driver and wired connection appearing in nm-applet? I can see only wireless connections even if I am plugged in. Wired network card works well in the system without Network Manager. However if it is commented out in /etc/network/interfaces it does not appear to Network Manager.
Any ideas?

---

### Post by Mach1US on 2006-07-31
I`v had problem with network-manager recognising one of my wireless cards due to fact that connection-manager had controll of the device ,what helped me was editing /etc/network/interfaces .
You can comment it as you did and type in the following statements.

auto lo
iface lo inet loopback

It seems Network Manager does not want to deal with interfaces that are
also handled by the other network management system. This fixed it for
me.

---

### Post by Krzysztof on 2006-07-31
My /etc/network/interfaces contains exactly the text that you wrote. No more lines.

---

