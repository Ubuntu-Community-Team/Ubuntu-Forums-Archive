---
title: "[SOLVED] WiFi connection broken"
date: 2007-11-21
forum: Networking &amp; Wireless
---

### Post by Trevor4706 on 2007-11-21
Last week I did a fresh installation of 7.10.  WiFi worked "out of the box" with my GigaFast WF728-AEX adapter (Prism54 chipset).  Connection was relatively quick stable, and the Gnome NM applet showed my own wlan and two or three others in the neighbourhood as available.  When I booted my laptop this morning I wasn't paying close enough attention when Keyring Manager asked for the passphrase for my wlan and I think I may have entered an incorrect passphrase.  Since then my wireless connection has disappeared.  NM does not show any available networks, and iwlist gets the same negative result.  I have tried Manual Configuration through NM and connection via the command line with no luck.

My /etc/network/interfaces hasn't changed, and shouldn't inhibit NM showing available networks:

auto lo
iface lo inet loopback

auto eth0
#iface eth0 inet dhcp

auto eth1
#iface eth1 inet dhcp

auto eth2
#iface eth2 inet dhcp

auto ath0
#iface ath0 inet dhcp

auto wlan0
#iface wlan0 inet dhcp

auto ppp0
#iface ppp0 inet ppp
#provider ppp0

Any suggestions on what I can do to get my wireless back?

---

### Post by Blutack on 2007-11-21
Administration --> Keyring Manager and wipe all your network keys

---

### Post by Trevor4706 on 2007-11-22
Looks like my wireless adapter chose to go south yesterday at the exact moment I entered the wrong password.  It no longer works in XP either.  Now I'm in the market for a Ubuntu/Kubuntu compatible PCMIA or USB WiFi adapter.

---

