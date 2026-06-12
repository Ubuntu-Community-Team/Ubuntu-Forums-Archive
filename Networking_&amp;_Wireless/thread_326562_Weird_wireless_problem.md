---
title: "Weird wireless problem"
date: 2006-12-27
forum: Networking &amp; Wireless
---

### Post by malfist on 2006-12-27
I have just recently set up a wireless network and through reading on this forum and the wiki I have been able to configure it to work properly...almost. The connection though the wireless (USB netgear WG111v2) wlan0 works fine. But ocasionaly it just drops the connection. I've changed channels incase of fequency interfearance, I've restarted things with:
sudo /etc/init.d/networking restart
and
sudo /etc/init.d/dbus restart

I even restarted gnome (with little hope that would fix it, don't know what gnome would have to do with networking). Nothing will fix it, ocasionally it will reconnect with the first restart thingy but not always, usually it takes several tries.
Only one thing fixes it for sure and that is a reboot, that always fixes it...until it happens again. The iwlist wlan0 scan is never consistant except in one thing, the signal level, it's always at 0 despite the fact that the wireless router is less than 30 feet away and doesn't cross walls (Only doors when closed). No TV or radio, the wireless phone is set to 900MHz so it shouldn't interfear. 

Any ideas on how to fix this?
I'd really appreciate it.

---

