---
title: "KNetworkManager: no TKIP on WPA Enterprise?"
date: 2008-01-08
forum: Networking &amp; Wireless
---

### Post by SomeGuyDude on 2008-01-08
I'm actually running into this problem running OpenSUSE, but as it's KNetworkManager in general I'm assuming someone here can help (not much response on the forums there).

My university's network requires us to use WPA-Enterprise and a TKIP protocol. On Ubuntu this is no problem since the nm-applet has all the necessary options right underneath it. KNetworkManager, on the other hand, seems to lack the protocol box.

Apparently NetworkManager 0.65 has the TKIP protocol under WPA Enterprise, but for no reason I can figure out, that box is quite literally not there in its KDE frontend. Is there a way to fix this or perhaps get around it?

---

### Post by SomeGuyDude on 2008-01-09
Anyone?

---

### Post by wieman01 on 2008-01-09
I think the KDE version of Network Manager isn't as advanced. You can either compile the latest version from source yourself, or you revert to using WICD:

[http://wicd.sourceforge.net/]("http://wicd.sourceforge.net/")

That's my best shot. :-)

---

### Post by SomeGuyDude on 2008-01-09
> **wieman01 said:**
> I think the KDE version of Network Manager isn't as advanced. You can either compile the latest version from source yourself, or you revert to using WICD:

[http://wicd.sourceforge.net/]("http://wicd.sourceforge.net/")

That's my best shot. :-)

Where would I go to get the Network Manager? I found an SVN repo but I haven't a dang clue what to do with it.

---

### Post by wieman01 on 2008-01-10
> **SomeGuyDude said:**
> Where would I go to get the Network Manager? I found an SVN repo but I haven't a dang clue what to do with it.
Ok, here are instructions:

[http://wicd.sourceforge.net/download.php]("http://wicd.sourceforge.net/download.php")

Post here if you run into problems.

---

