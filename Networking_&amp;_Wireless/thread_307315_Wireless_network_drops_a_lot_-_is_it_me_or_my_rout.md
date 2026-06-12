---
title: "Wireless network drops a lot - is it me or my router?"
date: 2006-11-26
forum: Networking &amp; Wireless
---

### Post by Kensey on 2006-11-26
I've been having an ongoing wireless issue that my wife suspects is due to a bug in the ipw2200 driver I'm using.  I think it's the router, but she insists it never happens when I'm not home.  Details:

I have a Dell Latitude D610 running Dapper, with an Intel Pro/Wireless 2200 card.  My wife has a Latitude D505 running Windows XP, with an Intel card (same model) as well.  Our wireless router is a Linksys WRT54G v4 running Linksys firmware 4.30.5.

Periodically our wireless network will disappear completely.  Both our laptops show the same behavior -- suddenly all networks disappear, then gradually they reappear, as though something had caused both our cards to reset.  It happens at the exact same time to both of us.  It happens to me by myself but she says it never happens to her if my laptop isn't on.

When I notice it, it seems to correlate with the appearance of a weak wireless network named SnyderNetwork, but the network in question is on channel 11 and I'm on channel 1 (the other 4 I typically see are all on channel 6) so it's not simple channel-stomping.  He (I say he, but I don't know who it actually is) and I are both running WPA; I use AES cipher and he uses TKIP.  Of the other four two are apparently unsecured and two use WPA/TKIP; one of the secured ones is configured using Linksys Secure Easy Setup.

The router doesn't seem to physically reset during this; I have things plugged into the wired ports in back that seem to be fine throughout.  I don't know if its transmitter stops transmitting or what since both our cards lose all networks at once.

Is this a behavior that others have seen?  Is there a bug in the ipw2200 driver that could cause other cards (particularly other Intel cards) to reset as well when it triggers?  Is there a bug in the Linksys WRT54G that could cause the network to disappear and reappear in the vicinity of a SES-configured Linksys network even though mine is configured manually?

---

### Post by taj on 2007-01-24
Sorry for the late reaction.
I also have dapper, intel ipw2200 and WRT54g.

The solution against drops is: install the latest firmware and driver. You will have to go through the [HOWTO]("http://www.ubuntuforums.org/showthread.php?t=26623"). Replace the version numbers with the latest ieee80211, firmware and driver versions, but do not proceed through to the WPA-supplicant part (install Network Manager instead).
Since I did this I never had any drops anymore.

I first upgraded the WRT54G firmware to Hyperwrt-Thibor, but that did not help, the problem was in ipw2200.

However, I do have frequent drops with a Siemens Gigaset SX553 Router I occasionally use. So, now I know again how frustrating this is.

The output of
~$ dmesg | grep ipw
should be something like this:
[17179586.312000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.1dmq
[17179586.312000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[17179587.068000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[17179587.368000] ipw2200: Detected geography ZZR (14 802.11bg channels, 0 802.11a channels)
I saw a few firmware messages that made me decide to upgrade

Good luck

---

### Post by Tethtibis on 2007-06-27
i've had two linksys routers in my life, they have to be reset CONSTANTLY. i wouldn't doubt it's the router.

---

