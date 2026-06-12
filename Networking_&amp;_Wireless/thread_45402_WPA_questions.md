---
title: "WPA questions"
date: 2005-06-30
forum: Networking &amp; Wireless
---

### Post by fizgig on 2005-06-30
I'm following the neat guide in the how-to section and I'm having a problem.  First off, I've been using ndiswrapper just fine with WEP.  I've deactivated the wireless connection in the gnome network settings so no WEP gets done now.

I follow the guide and I run the [b]wpa_supplicant -Bw -Dndiswrapper -iwlan0 -c/etc/wpa_supplicant.conf -dd

[/b]I don't get any error messages, the last line says "Daemonize..." and sure enough I see it in my list of processes.

Trouble is, if I do an iwconfig, I don't see it associated with my access point.  I know the access point is configured properly because I got XP (this is a dual-boot laptop) to use WPA with it (took about 5 seconds to configure).

Should I see it associated with my access point after running wpa_supplicant properly?  I do try to get an ip address (dhclient wlan0) but it never works.  Thanks for any help.

---

### Post by fizgig on 2005-06-30
Got it to work.  It was helpful to run it in the foreground to get more debugging info.

Turns out, I have to run it with sudo and use the switch **-B** not **-Bw**.  Now it works perfectly.

---

