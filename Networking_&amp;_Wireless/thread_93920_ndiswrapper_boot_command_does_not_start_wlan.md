---
title: "ndiswrapper boot command does not start wlan"
date: 2005-11-23
forum: Networking &amp; Wireless
---

### Post by gwen on 2005-11-23
i followed the [http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation#Install_Windows_driver](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation#Install_Windows_driver) installation and my wireless car works perfectly, but the problem is: it does not start automatically on boot, even after adding ndiswrapper to /etc/modules

i could not find anything to fix this

im sure it's a quick fix....so please help :)

---

### Post by az on 2005-11-23
Does not start?  Do you mean the module is not loaded, or the connection is not made?

And how are you making it start by hand?

---

### Post by mlomker on 2005-11-23
If the module is loading then you might just need **auto wlan0** in your /etc/network/interfaces file.

---

