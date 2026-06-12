---
title: "Getting rid of automatic network configuration daemons"
date: 2008-01-05
forum: Networking &amp; Wireless
---

### Post by jhoderd on 2008-01-05
Hey,

I'm getting mad trying to get the wireless network to run on a fresh Gutsy install.  The problem seems to be that the new Avahi/networkmanager/upstart stuff is getting in the way.

Now, I can get the network to run if I configure it manually (ifconfig, wpa_supplicant, route, etc).  On my previous Debian installation, I configured /etc/network/interfaces and everything worked fine.  However, with Gutsy, there's a bunch of daemons that get started automatically and that conflict with my configuration.

I have run the following commands to prevent the Avahi-daemon and wpa-ifupdown services from starting:

update-rc.d -f avahi-daemon remove
update-rc.d -f wpa-ifupdown remove

However, it doesn't seem to be enough, since there's still something starting the wpa_supplicant without my authorisation.

Therefore my questions is: what other services should I remove?  I really don't need any of this "supposedly user-friendly but just gets in the way" stuff...

cheers,
Jean

---

