---
title: "How to connect as soon as USB device is plugged in"
date: 2007-02-19
forum: Networking &amp; Wireless
---

### Post by wej1971 on 2007-02-19
I've finally managed to sort my wireless woes which have been driving me nuts for the past two weeks, but I'm left with one question. For my wireless dongle to work, I have to boot up without it, plug it in and then launch wireless assistant. After a few seconds the access point is shown and I can connect.

Question is, how can I do this automatically as soon as my dongle is plugged in? Given that the wireless doesn't work if I boot up with it in from the start, I'm assuming my settings in /etc/network/interface are set but the connection is automatic. Can I create a script or something similar that will connect to my chosen access point once the dongle is inserted?

---

### Post by teaker1s on 2007-02-19
install  [COLOR="Red"]network-manager-gnome[/COLOR]
and to stop gnome keyring asking for password each time look here
[http://www.ubuntuforums.org/showthread.php?t=187874]("http://www.ubuntuforums.org/showthread.php?t=187874")

---

