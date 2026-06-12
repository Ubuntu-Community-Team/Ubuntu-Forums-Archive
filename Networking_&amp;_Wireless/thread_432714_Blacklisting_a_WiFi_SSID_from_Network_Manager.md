---
title: "Blacklisting a WiFi SSID from Network Manager?"
date: 2007-05-04
forum: Networking &amp; Wireless
---

### Post by dmorris68 on 2007-05-04
I have a peculiar problem that I don't see addressed after a cursory search through the forums here.

I'm using my Toshiba laptop running Feisty to connect to my office WiFi AP (Intel ipw3495 Wifi) .  That works fine, except for a small problem.  Sometimes it will prefer an unwanted SSID instead of the one I'm trying to connect to.  This presents a problem at work when I'm trying to get on the company LAN (we're in a downtown office building with several nearby public AP's), and has even effected me at home when sometimes a neighbor's unsecured AP gets priority over my own.

I'm using Network Manager rather than customized wpa_supplicant configs, and I don't see a place to either set SSID priority, or to disable/blacklist those SSID's that I never want to connect to.  I like the ability of NM to roam around and pickup any available SSID, but I'd like more control over priority and blacklists.  With Edgy I ran wpa_supplicant manually, with mixed results due to roaming, so I'd prefer to keep NM for this.

Anybody have any suggestions?  Does wicd support what I'm trying to do, and does it have an applet that works as well as NM works?

---

