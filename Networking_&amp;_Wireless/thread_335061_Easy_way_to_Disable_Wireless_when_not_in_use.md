---
title: "Easy way to Disable Wireless when not in use?"
date: 2007-01-09
forum: Networking &amp; Wireless
---

### Post by redbluemangle on 2007-01-09
I'm setting up a laptop for my mom (IBM Think pad T40) and I'm noticing that even when on a wired connection the wireless light is blinking on every now and then. I have network-manager-gnome managing the connection. For the sake of battery usage, is there easy way to effectively turn off the wireless when its not in use perhaps a command I could put in a launcher to toggle it on/off? Something a windows user could do easily when in need :rolleyes:

---

### Post by scrooge_74 on 2007-01-09
sudo ifdown eth1 (or the correct network card the system recognizes)

---

