---
title: "WiFi unstable on 18.10 with Killer Wireless (Dell XPS 9370)"
date: 2018-11-27
forum: Networking &amp; Wireless
---

### Post by chrisklosowski on 2018-11-27
[FONT=arial]Hey all,

I'm starting with this form of support in order to see if anyone has some advice in how I can maybe pass this upstream to get fixed, but my setup is:

Ubuntu 18.10 (upgraded from a clean install of 18.04)
Dell XPS 9370
[COLOR=#333333]Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter [168c:003e] (rev 32)
[/COLOR][COLOR=#333333]Kernel driver in use: ath10k_pci

When I was running 18.04 I had no issues with the WiFi but now (on 18.10) at specific locations I'm getting issues where I'll be connected just fine, but then 'randomly' I'll lose my WiFi connection and have the Question Mark in the icon for Gnome Network Manager. I can sometimes get it to come back by going to Airplane mode and then disabling it. But that doesn't always do the trick.

As it was only happening mainly in one location (home) I decided to look at my router. I went in and changed my Channel to a specific channel instead of Auto and I've had the longest run at stable WiFi at home in a month. My questions for this group are:

1) Is it possible that this is a bug in Ubuntu 18.10 when an Access Point changes channels due to congestion (I live in a populated area with many access points within range)
2) If #1 is possible, where would I report that on launchpad, and what information would be helpful so that I can make sure the developers who would look at it have enough information to go on?

Appreciate the feedback.[/COLOR][/FONT]

---

### Post by thicolares on 2018-12-07
Hi

Same problem here.
Qualcomm Atheros: QCA6174 802.11ac Wireless Network Adapter
broadcast=yes driver=ath10k_pci driverversion=4.15.0-42-generic firmware=WLAN.RM.4.4.1-00079-QCARMSWPZ-1 ip=192.168.0.106 latency=0 link=yes multicast=yes wireless=IEEE 802.11
Same machine: Dell XPS 9370
Same clean install of Ubuntu 18.04

I'll try to change my Channel to a specific one too. I'm keen to know how to fix this for good.

Regards!

---

