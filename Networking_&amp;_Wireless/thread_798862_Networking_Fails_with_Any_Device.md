---
title: "Networking Fails with Any Device"
date: 2008-05-18
forum: Networking &amp; Wireless
---

### Post by IndigoAK on 2008-05-18
Greetings,

As has happened with the previous few releases, I am unable to connect to my router with any device using all variants of Ubuntu.  Currently, I use an Atheros based D-Link wifi card as my main device in Windows, but since the drivers for this under Linux are difficult to understand and install, I decided to try and use either my Realtek wireless chip (on the mobo) or the two NVIDIA LAN ports that are available.  None of them work from within Ubuntu or its variants, while they function perfectly within Windows.

Firstly, the LAN ports do not respond when in roaming mode.  My router has DHCP disabled, so when I go to set a static IP address in the network manager, the wired networks disappear completely from the right-click list (where you select the network from the desktop).  The only way to get them to reappear is to put them back in roaming mode, which brings me back to square one.

As for the Realtek chip, it will properly detect my router's SSID, but every time I enter the passphrase, it just asks for it again and again and again.  If I set this to a static IP address, the Realtek chip also disappears from the list of available networks devices.

Long story short, I've been unable to get my network working for four releases now.  Each release, these same issues still occur.

The complete list of hardware I've tried follows:

2x NVIDIA nForce 590 LAN Ports
1x D-Link AirPlus Atheros-based Wifi Card
1x Realtek Onboard Wireless Chip

My router is a D-Link DGL-4300.

Is there any fix for these?

---

