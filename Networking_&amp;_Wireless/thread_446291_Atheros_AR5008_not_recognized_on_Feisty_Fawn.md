---
title: "Atheros AR5008 not recognized on Feisty Fawn"
date: 2007-05-16
forum: Networking &amp; Wireless
---

### Post by anhnguyen on 2007-05-16
Hi guys,

I decided to dual boot XP Home and Ubuntu on my T60 this morning and the installation went extremely smooth. Ubuntu however does not recognize my Atheros AR5008 wireless card (probably due to the new n standard) when I run lspci. It was something along the line of Network Controller: Atheros Communication unknown device. Is there a fix for this? I apologize if this question has already been posted and answered before.

Thanks!

---

### Post by spd106 on 2007-05-18
Unfortunately the AR5008 is not supported by the madwifi driver yet, see [http://madwifi.org/](http://madwifi.org/).

You could compile the latest development version from svn, just be aware that it's still under major development. I would recommend that you wait until an official release.

You might be able to get it working with NDISwrapper and the windows driver, there are various guides for this around the forum. You might want to consider downloading a newer version than the one included with 7.04 as there have been some Atheros related improvements since then.

---

