---
title: "No more wireless applet after upgrade?"
date: 2008-11-03
forum: Networking &amp; Wireless
---

### Post by sdcope on 2008-11-03
Hi all,

I was wondering if the wireless applet that used to load next to the sound controller in gnome disappeared for anyone else after upgrading to 8.10 &/or if anyone would be kind enough to enlighten me on it's reinstallation.
 The netwqork tools on 8.04 where great, and I'd really like to have them back.
Thanks!

---

### Post by eks on 2008-11-03
Never happened to me. But you can also try wicd:

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

### Post by bscbrit on 2008-11-03
Yes!  I discovered this afternoon that the 4 computers that I had upgraded had all lost the applet.  I experimented with a clean install and that put the applet back but of course lost all my previous network settings.

If you have a wireless network connection then NetworkManager is OK but it cannot cope with wired connections very well. After each reboot it forgets its settings and has to be told to go back to your chosen wired network connection.

I am just updating all my computers to wicd.  It works.

[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

---

