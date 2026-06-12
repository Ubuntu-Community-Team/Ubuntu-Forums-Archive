---
title: "madwifi + nm-applet no good"
date: 2007-02-24
forum: Networking &amp; Wireless
---

### Post by lesshaste on 2007-02-24
I have struggled through various instructions and have eventually got wpa working on my toshiba portege r200 in xubuntu.  The main difficulty has been that nm-applet does not seem to recognise the madwifi driver at all,  Even now with the wireless working the little icon has an X next to it meaning there is no network.  

Is this a bug in nm-applet?  If so, it would help other people hugely if it could be fixed.  I had to do the whole thing manually (if anyone wants to know details please ask).

uname -a
Linux ubuntu 2.6.17-11-386 #2 Thu Feb 1 19:50:13 UTC 2007 i686 GNU/Linux

edgy 6.10

Raphael

---

### Post by lesshaste on 2007-03-04
In the end I found the fix.  If you have anything at all configured for your wireless card in 

/etc/network/interfaces

then nm-applet completely ignores that device and pretends it doesn't exist. So removing everything from there except for the "lo" lines allowed nm-applet to "just work".

Raphael

---

### Post by spd106 on 2007-03-04
Sorry this thread was ignored for a week.

You are quite right, this wiki page explains what to do [https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

---

### Post by lesshaste on 2007-03-04
Thanks. It would be *much* better if nm-applet told you something about the interfaces it thinks are being handled elsewhere.  It could simply list them and say "configured in /etc/network/interfaces" with a comment that nm-applet will therefore ignore them.

Raphael

---

