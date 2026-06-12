---
title: "atheros wifi card installation"
date: 2007-02-26
forum: Networking &amp; Wireless
---

### Post by nonewmsgs on 2007-02-26
ok now im using the netgear wpn511 card with the athros chipset and networking shows it (Yay -- further than i ever got with my other cards)

(now im using another laptop next to this in order to post this so im only writing in what looks relevent)

$ lspci
06:00.0 Ethernet controller: Atheros Communication, Inc. AR5212 802.11abg NIC (rev 01)

$ iwconfig

lo no wireless extensions

eth0 no wireless extensions

ath0 IEEE 802.11g ESSID: "nitd6"
mode:Managed Frequency: 2.447GHz Access Point: Not-Associated
BIt Rate:0kb/s Tx-Power:18dBm Sensitivity=0/3
Retry:off RTS thr:off Fragment thr:off
power management:off
link quality=0/94 signal level=-95Bbm noise level=-96dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag=0
Tx excessive retries:0 invalid misc:0  Missed beacon:0

sit0  no wireless extensions

---

### Post by Metaljaz on 2007-02-27
try this thread if you haven't already:

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

---

### Post by nonewmsgs on 2007-02-27
smile.  i just got it working thank you! 
i had just used the madwifi startup for newbies thing.  it is very similar.  thanks again.

what gets me is i checked in 2 ubuntu books (including the official one) and neither really wants to  go into detail about wireless.  they both pretty much assume it works.

---

