---
title: "HELP: bcm43xx Autostart in Hardy"
date: 2008-04-30
forum: Networking &amp; Wireless
---

### Post by LinuxLovesMJ on 2008-04-30
I currently disabled and blacklisted b43, b44, and ssb in hardy because I would like to use the original bcm43xx. It works fine, but the only problem is that I have to manually enable it every time I restart, such as I have to modprobe -r b43 and then modprobe bcm43xx to make it work on reboot. Is there anyway to make the bcm43xx driver autostart on reboot so I don't have to go through the process of unloading b43 and loading bcm43xx every time I reboot? I already checked modules and bcm43xx is listed there.

Thank you.

---

### Post by LinuxLovesMJ on 2008-04-30
ne one?

---

### Post by Ayuthia on 2008-04-30
Some of the ndiswrapper users have been adding that information to their /etc/rc.local file.  You might try adding your modprobe -r b43 and modprobe bcm43xx there.

---

