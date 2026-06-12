---
title: "Safecom Wifi Card Woes"
date: 2006-08-15
forum: Networking &amp; Wireless
---

### Post by GunterPete on 2006-08-15
Hi folks,

I've had Ubuntu successfully installed on my laptop for months now, and I love it; so when I decided to setup a PC for my lounge naturally I wanted it to run Ubuntu also.

Things seemed to be going well until I came to configuring the wifi card, which is a Safecom, model SWLPT-54125.

I followed the guide on [the documentation]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#head-94f1ae7b5a3909097558fc0eb240d8a6eede5b6d"), and ndiswrapper succefully built a driver from the XP configuration files:
> media@sirpooter:~$ ndiswrapper -l
Installed ndis drivers:
usr11g          driver present, hardware present

Here is the output after the "loading the module section":
> media@sirpooter:~$ tail /var/log/messages
Aug 14 21:28:25 localhost kernel: [17181415.448000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Aug 14 21:28:44 localhost gconfd (root-5834): GConf server is not in use, shutting down.
Aug 14 21:28:44 localhost gconfd (root-5834): Exiting
Aug 14 21:33:38 localhost gconfd (root-6099): starting (version 2.14.0), pid 6099 user 'root'
Aug 14 21:33:38 localhost gconfd (root-6099): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Aug 14 21:33:38 localhost gconfd (root-6099): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Aug 14 21:33:38 localhost gconfd (root-6099): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Aug 14 21:33:38 localhost gconfd (root-6099): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Aug 14 21:33:38 localhost gconfd (root-6099): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Aug 14 21:33:54 localhost kernel: [17181744.076000] ndiswrapper version 1.8 loaded (preempt=yes,smp=no)

However the card doesn't seem to recognise any of the access points in range. The GUI Network config tool sees the card as wlan0, but nothing appears in the combo box, and I get the following when I try and scan:
> media@sirpooter:~$ iwlist wlan0 scan
wlan0     No scan results

There are three other computers in the house that can access the access point no worries. If anyones able to help I'd be so incredibly gratefull, as I'm at my wits end, and my housemate thinks I'm turning into an obsessive :-?

---

