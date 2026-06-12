---
title: "Sniffing in monitor mode with wireshark and Edimax 7318Usg adapter?"
date: 2008-01-31
forum: Networking &amp; Wireless
---

### Post by Fanatico on 2008-01-31
I need to sniff specific wireless LAN with Wireshark in monitor mode.
Essid and wep key is known. Unfortunately I receive only broadcast
and multicast packets.

My configuration:
Ubuntu 7.10 Gutsy
Wireless network adapter Edimax 7318 USg
I use driver from rt2x00.serialmonkey.com

I uninstalled Network Manager and configure WiFi adapter manually
as follows:

ifconfig wlan0 up
iwconfig wlan0 mode monitor
iwconfig wlan0 channel 6
iwconfig wlan0 essid MY_SSID


After that I am starting Wireshark and start capturing.
(No kismet or other utilities are in use).

So I have a few questions:

1. Can anyone explain why I receive only broadcast and multicast packets in above situation?

2. I concern that my decision to sniff network in monitor mode was wrong.
As far as I understand in monitor mode Wireshark can capture packets
from all available wireless networks. In promisc mode Wireshark can capture packets
only from wireless network with specified essid. So since I need to sniff specific
wireless LAN with known essid and wep key, I need to sniff in promisc mode and not
in monitor mode. Can anyone comment? How to set up promisc mode?

By the way if this is true, then setting parameter essid in above example was useless.

3. Wy wireless interface is shown as wlan0? Should it be rausb0? I concern that
I might install (or use, since not blacklisted) wrong driver (RT2500) for my network
adapter instead of RT73. Can anyone comment/suggest how to check?

Thank you in advance

---

### Post by hahahan on 2008-01-31
This works for me.

ifconfig wlan0 up
iwconfig wlan0 mode managed
iwconfig wlan0 essid MY_SSID
iwconfig wlan0 key MY_KEY
dhclient wlan0
ifconfig wlan0 promisc
fireup wireshark

Regards.

---

