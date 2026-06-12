---
title: "ipw2200 + WPA"
date: 2008-03-03
forum: Networking &amp; Wireless
---

### Post by pestilence on 2008-03-03
Hello everyone,
I am experiencing problems with my ipw2200 card, I can connect to open networks, and on WEP protected networks but I cannot connect on WPA enabled networks for some reason.
I tryed both Network-Manager and wpa_supplicant methods without any success.I do see the network through iwlist scan commands but I cannot authenticate with it (Network-manager keeps trying and then pops up the authentication window again).
Changing the security to WEP does the work and I am able to connect, changing to open does again the work, the problem only occures when connecting on WPA enbled networks.

---

### Post by pestilence on 2008-03-04
Forgot to mention Gutsy 7.10 distro up to date...
bump :(

---

### Post by ubutufan on 2008-03-04
Try Wicd. You can find it at 
[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

It works brilliantly with all sorts of encryption methods. Surely it works with wired as well

---

