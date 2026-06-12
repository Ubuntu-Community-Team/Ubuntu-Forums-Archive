---
title: "Wifi Rader solves some wireless problems"
date: 2007-04-03
forum: Networking &amp; Wireless
---

### Post by mrund on 2007-04-03
Like a lot of people here, I have trouble connecting with Ubuntu to a wireless access point that works just fine with the same machine booted in Win XP. Ubuntu is aware of the wifi adapter and able to see all available wifi nodes, but it is unable to make a connection.

network-manager did nothing for me. But with Wifi Radar, I managed to get a connection -- if the access point's security is disabled. In other words, Wifi Radar will let me connect to unprotected access points, but not to protected ones even if I know their passwords. Regardless if they use WEP or WPA encryption.

Wifi Radar isn't currently available in Synaptic under Edgy, but I found it easy to download and install it from here:

[http://wifi-radar.systemimager.org/]("http://wifi-radar.systemimager.org/")

---

### Post by mrund on 2007-04-03
Anyone know what I might enter into the "WPA driver" box in Wifi Radar? And where I can get such a driver?

---

### Post by king_growler on 2007-04-03
> **mrund said:**
> Anyone know what I might enter into the "WPA driver" box in Wifi Radar? And where I can get such a driver?Try "wext".
man wpasupplicant for more details.

---

### Post by SteveHoffmanUK on 2007-04-03
mrund wrote:
> Wifi Radar isn't currently available in Synaptic under Edgy, 

Strange . . . it shows up in my Edgy Synaptic! 

I installed it on my Dell Latitude laptop and took it to London today to see whether it would work. It certainly detected some wifi networks (even as I went along in the train it picked up some local ones) but at Victoria Station it only showed two encrypted "managed" and one unencrypted "ad-hoc" network and didn't offer me even the chance to connect. I think Ubuntu doesn't do ad-hocs, does it?

Can you connect straight from Wifi Radar itself when there's an unencrypted one available?

---

### Post by bradweiser on 2007-04-03
WiFi Radar also shows up in my Edgy Synaptic.

I've also been having similar wireless problems. WiFi Radar shows wireless connections, but fails to obtain an IP address when connecting to any unprotected networks.

---

### Post by mrund on 2007-04-04
King Growler, no luck with "wext", and there's no man page for wpasupplicant on my system though the software itself is installed.

---

### Post by king_growler on 2007-04-30
> **mrund said:**
> King Growler, no luck with "wext", and there's no man page for wpasupplicant on my system though the software itself is installed.Sorry for the late reply. Try "man wpa_supplicant" and "man wpa_supplicant.conf". Don't forget the underline!

---

### Post by JerseyShoreComputer on 2007-04-30
Agreed. WiFi radar worked great for me too and solved my wireless problems. It can be installed via Synaptic or the program installer.

good luck!

---

