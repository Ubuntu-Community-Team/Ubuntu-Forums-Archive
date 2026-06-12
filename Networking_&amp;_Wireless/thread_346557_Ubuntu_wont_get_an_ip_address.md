---
title: "Ubuntu wont get an ip address"
date: 2007-01-25
forum: Networking &amp; Wireless
---

### Post by Praetorian65 on 2007-01-25
Im using 6.10. Was a troublesome install on my Asus P5B Deluxe/C2D/X1950. It was the only distro that would boot the install program properly. I eventually managed to install (although there are always a few I/O error messages at bootup) but for some reason neither ethernet or wireless want to work. They are detected fine and appear to be configured fine but neither gets a network address. I tried deactivating and reactivating them but still the same thing happened. Everything appears to be fine it just doesnt work.

---

### Post by K.Mandla on 2007-01-26
Double check inside the /etc/iftab and /etc/network/interfaces files to make sure the information there matches the settings you need. Most importantly, make sure the MAC addresses in /etc/iftab are correct for the cards, and that the interface names in /etc/network/interfaces match the ones in /etc/iftab. Beyond that ... :-k

---

