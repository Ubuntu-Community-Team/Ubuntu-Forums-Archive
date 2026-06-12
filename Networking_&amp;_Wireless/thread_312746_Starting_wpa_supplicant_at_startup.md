---
title: "Starting wpa_supplicant at startup"
date: 2006-12-04
forum: Networking &amp; Wireless
---

### Post by enigma83 on 2006-12-04
So, I've just had to get Ubuntu going on a managers laptop.  I haven't had a great deal of experience with Ubuntu, but I can handle myself with Gentoo quite well, so maybe I'm just going about this the wrong (Gentoo) way.

My general wireless setup consists of wpa_supplicant, with a suitable configuration file, running at bootup.  I'll then have ifplugd running.  When an association occurs, ifplugd will bring the interface up, and start a DHCP client.

From what I can tell with Ubuntu, wpa_supplicant isn't meant to run all the time.  At least, there's no /etc/init.d/wpa_supplicant file.  And I have wpasupplicant installed.  Wpa_supplicant seems to be meant to be started from the /etc/network/interfaces file, after an 'ifup eth#' is issued.  Of course, this breaks everything for the way I prefer to have things run.  It means that the interface must be brought up, without knowing what wireless networks are around, to start wpa_supplicant and then generally DHCP 5 seconds later.

If the laptop is started outside of a wireless-covered area, the wireless won't work.  When the laptop is brought into the covered area, we have to wait for the dhcp client to initiate a new lease request.  It can also make weird things happen when you migrate between two completely seperate networks, with dhcp not releasing/renewing straight away.

So basically, what I want is to have wpa_supplicant running at all times.
When it associates, ifplugd starts.  This then starts the DHCP client.  If the wireless network disappears, ifplugd stops the interface, stopping DHCP.  If we move between networks, ifplugd restarts the interface, ensuring we get a new IP address (all networks are DHCP).

Now, I have 90% of this set up.  The only thing I am missing is an init file for wpa_supplicant.  However, I was curious, surely other people have the same issue as me.  And the whole 'mapping' thing in /etc/network/interfaces seems roughly similar to what I want.  I can probably set up a mapping to scan for networks, check what is nearby ... etc etc.  But since wpa_supplicant handles this itself, I'd rather leave it to do it's job.  Not to mention that wpa_supplicant has semi-decent GUI configuration tools available.

So, my actual questions.

A) Is there a 'Ubuntu' way to run something, such that when a configured wireless network is detected, we associate with it.  And when we have associated, we start the DHCP client?

B) Is there a proper way to run wpa_supplicant at startup, or should I just write my own init script?

---

