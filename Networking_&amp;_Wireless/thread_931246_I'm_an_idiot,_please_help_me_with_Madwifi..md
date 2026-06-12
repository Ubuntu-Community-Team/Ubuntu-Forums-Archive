---
title: "I'm an idiot, please help me with Madwifi."
date: 2008-09-27
forum: Networking &amp; Wireless
---

### Post by orre64 on 2008-09-27
First off, I know essentially nothing about Linux. :(

Yesterday I tried to get Ubuntu installed on a laptop, HP G7030EO. Everything fine except for wifi, which cannot be detected despite proprietary HAL drivers something being enabled. XP SP3 claims that my ethernet card is Atheros AR5006x. Ubuntu claims that my card is AR242x.

I started going through guides and the forum, and found some quick solutions that claimed to be able to solve my problem. Apparently, installing a driver called Madwifi would solve the problem. Most of the guides, however, were old and the tar archives linked had been removed in favor of the newest version of Madwifi.

I try to install it according to this guide: [http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo), everything seems to work fine, despite my newbishness, up until the "Creating an interface" step, where the command "wlanconfig ath0 create wlandev wifi0 wlanmode sta" yields some sort of no such device-error.

I have no clue if i managed to install the driver correctly, is there a way to check this?

Now I'm basically wondering if I could have some help to solve this. I am almost entirely sure that my card should be supported, but I honestly have no clue how to handle drivers etc in Linux.

I also head that Ibex will have some sort of native drivers for Atheros cards, is it in your opinion worth trying the alpha to see if that solves things?

---

