---
title: "X locks up when enabling wifi"
date: 2014-03-19
forum: Networking &amp; Wireless
---

### Post by kjkrum on 2014-03-19
In the last day or two, my wifi connection has been becoming unresponsive after a few minutes of use.  My browser starts timing out when loading pages.  Then it starts saying there is no route to anything.  Even my LAN gateway becomes unreachable.

If I toggle wifi, X locks up when I turn it back on.  Ctrl-alt-backspace doesn't work.  Sometimes this situation persists even after a warm boot.  I must reboot cold before I can turn wifi back on.

I first noticed this after updating a bunch of packages.  I don't even know what packages I updated; I just updated what was recommended.  Is there a way to tell what packages were recently updated?

Edit: running 12.04 LTS.

---

### Post by kjkrum on 2014-03-19
I found a temporary workaround: by attempting to connect to a different wireless network, canceling, and then connecting to my network again, I can reset it without the whole system locking up.  I have to repeat this procedure every few minutes.

---

### Post by 7sbaV8Kt5PTh on 2014-03-19
Are there any entries in /var/log/syslog for this?  I notice that on my Lenovo, after is did the 12.04.3 LTS updates, I had to get a new WLAN driver from Lenovo to get it to work.

---

### Post by kjkrum on 2014-03-23
The problem seems to have magically fixed itself.  Knock wood...

---

